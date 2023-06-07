# Evaluation Agent

The Evaluation Agent (EA) is the risk management layer in the Huma Protocol. They are responsible for the underwriting decisions for the lending pools they are associated with. The goal for the EA platform is to build a secured, community-driven system to support accurate underwriting decisions at scale.

Each EA implements a standard interface to interact with Huma SDK and Huma contracts. They also have borrower authenticated read access to relevant signals in the DSP for their models.

## EA Hosting

Each lending pool selects an EA from the HUMA EA registry to delegate its underwriting. EAs can further specialize to serve the use cases of a specific pool, or stay more generic to support more pools.

The EAs are fully decentralized. Each EA is a microservice with a shared interface. For anti-fraud considerations, Huma does not require the EAs to open-source their models. Both Huma and the Pool Owner will inspect and validate the EA before selecting it to underwrite for a pool.

The EA hosting platform is open-sourced (as in this repo). It is centralized at this moment due to the need for the complexity of computations and to support faster iteration in the early stage. As decentralized execution engines become more powerful, we will transition the EA hosting platform to a decentralized execution platform as well.

## Creating a new EA

To create a new EA. Developers submit their models, EAs, to Huma DAO for review. Once approved, the EAs are deployed in a secure container provided by Huma.

See a [sample Evaluation Agent](https://github.com/00labs/huma-example-underwriter) that underwrites loans using simple rules based on wallet transaction history.

An NFT is minted to represent each EA. Although any developer can mint an EA NFT, only Huma DAO can update the relevant metadata (e.g. status, performance) for each EA NFT and creates an entry in the EA Registry so that it is discoverable by pool owners.

```python
import pydantic
class UnderwritingRequest(pydantic.BaseModel):
    pool_address: str
    borrower_wallet_address: str
    context: dict[str, Any] | None = None
```

In the schema above:
- `pool_address` (required) is the blockchain address of the lending pool.
- `borrower_wallet_address` (required) is the wallet address of the borrower.
- `context` (optional) is the additional pool-specific data needed to underwrite the request. For example, for the Request Network Invoice Factoring pool, invoice-related data are passed through this field. Instead of leaving the type to be a generic `dict[str, Any]`, you can leverage Pydantic to define the exact shape like the following:

```python
import pydantic
class UnderwritingRequestReceivable(pydantic.BaseModel):
    param: str
class UnderwritingRequestContext(pydantic.BaseModel):
    receivable: UnderwritingRequestReceivable
class UnderwritingRequest(pydantic.BaseModel):
    pool_address: str
    borrower_wallet_address: str
    context: UnderwritingRequestContext
```

Note that this field is optional. If your EA does not require additional data then you don't have to specify this field.

#### Response object

The response object to the EA should have the format below. See inline comments for what they represent.

```python
import pydantic
class Token(pydantic.BaseModel):
    """
    Represents the information of the token that the loan proceeds will be distributed in.
    """
    symbol: str
    name: str
    decimal: int
class Terms(pydantic.BaseModel):
    """
    Represents the lending terms.
    """
    credit_limit: int
    interval_in_days: int
    apr_in_bps: int
    remaining_periods: int = 1
class Receivable(pydantic.BaseModel):
    """
    Represents the receivable information.
    """
    amount: int
class Approval(pydantic.BaseModel):
    """
    Represents an approval decision. Provide the token information and the lending terms at the minimum. If applicable, also specify the receivable information.
    """
    token: Token
    terms: Terms
    receivable: Receivable | None = None
class Rejection(pydantic.BaseModel):
    """
    Represents a rejection decision. Provide the rejection reasons in the `reasons` field.
    """
    reasons: list[str]
class UnderwritingApproval(pydantic.BaseModel):
    """
    The underwriting decision. If the underwriting request is approved, return an `Approval` as the result. Otherwise, return a `Rejection`.
    """
    result: Approval | Rejection
```

#### Route
The API route for making underwriting decisions should be called `/approve`: this is where the EAVerse will send underwriting requests for approval. With the above request and response objects in mind, you can implement the `/approve` route like the following:

```python
import fastapi
from huma_signals.adapters.lending_pools import adapter as lending_pool_adapter
from huma_signals.adapters.request_network import request_invoice_adapter
from underwriter import models
router = fastapi.APIRouter()
@router.post("/approve")
async def approve(
    request: models.UnderwritingRequest,
) -> models.UnderwritingApproval:
    # Fetch signals using Signal Adapters. Here we are fetching two kinds of signals here, but you can fetch
    # as many or as few as necessary.
    invoice_adapter = request_invoice_adapter.RequestInvoiceAdapter()
    invoice_signals = await invoice_adapter.fetch(
        borrower_wallet_address=request.borrower_wallet_address,
        receivable_param=request.context.receivable.param,
    )
    pool_adapter = lending_pool_adapter.LendingPoolAdapter()
    lending_pool_signals = await pool_adapter.fetch(pool_address=request.pool_address)
    # Use signals above to make the underwriting decision and return the result.
    result = models.Approval(...)  # or models.Rejection(...) if the request should be rejected.
    return models.UnderwritingApproval(result=result)
```

Note that in order to fetch signals using Huma Signal Adapters, you need to install the [huma-signals](https://pypi.org/project/huma-signals/) package as a dependency.

### Submit code for approval

To create a new EA, developers submit the code to Huma DAO for review. Once approved, the EA will be deployed in a secure container provided by Huma.

An NFT is minted to represent each EA. Although any developer can mint an EA NFT, only Huma DAO can update the relevant metadata (e.g. status, performance) for each EA NFT and create an entry in the EA Registry so that it is discoverable by pool owners.

We invite developers to contribute to the initial development and ongoing maintenance of EAs. As a way to kickstart development, Huma offers bounty programs where a portion of the protocol revenue will be allocated to reward EA and Signal Adapter developers and maintainers. The Huma DAO will review all contributions and determine how to distribute the reward among different contributors. Join us and be a part of building the future of decentralized finance!
