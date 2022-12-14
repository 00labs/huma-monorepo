# Getting Started

Hi, welcome to Huma. This guide will quickly take you through setting up the development environment for Huma Evaluation Agent System, including individual evaluation agents and signal adapters that power the Decentralized Signal Portfolio(DSP).

See our [whitepaper](https://docs.huma.finance/) to learn more about the Huma Protocol and the underwriting system's overall design.

## System Architect

To support the Huma Protocol and the lending pools to make good lending decisions. There're 3 major off-chain components we built:

- Decentralized Signal Portfolio (DSP)
  - DSP consists of a group of Signal Adapters that gather data from a variety of on-chain and off-chain sources.
- Evaluation Agent
  - Each evaluation agent is a microservice employed by a lending pool to make underwriting decisions.
  - EA relies on the DSPs to gather data about the loan request.
  - You can think DSP is the features and EA is the model in a Machine Learning system.
- Evaluation Agent Host (EAverse)
  - EAverse is the node quarterbacking Huma Protocol, DSP and EAs.
  - It's currently a centralized platform due to the complexity of computation. As decentralized execution engines become more powerful, we will transition to a decentralized execution platform as well.

## Requirements

The Huma Evaluation Agent services are developed in Python. We use [Poetry](https://python-poetry.org/) to manage dependency for these [FastAPI](https://fastapi.tiangolo.com/) services.

We suggest you use python version >= 3.10. The development environment is tested using [venv](https://docs.python.org/3/library/venv.html) for python env management.

### Running local server

```bash
make run-local
```

Go to `http://localhost:8000/docs` and you can make requests through the UI.

## Development Environment

### Poetry

Poetry is a tool for dependency management and packaging for Python. It creates a lockfile to guarantee reproducible installs and distribution. Highly recommended to browse through [poetry usage](https://python-poetry.org/docs/basic-usage/) if not familiar with it already.

Please install it following the official installer. For macOS users, note brew install may not install poetry correctly.

```bash
curl -sSL https://install.python-poetry.org | python3 -`
```

### Install dependencies

Poetry automatically creates new venv for packages with `pyproject.toml`.
(optional) VS Code users might find setting `poetry config virtualenvs.in-project true` makes it easier to manage the python interpreter.

```bash
poetry install
```

### Code style

To ensure code consistency we have CI to check code style. We use `black`, `flake8` and `isort` with some customization. You can run the CI check with

```bash
make lint-check
```

To automatically fix issues, run

```bash
make lint
```

### Type hints and validation

In this project, we require all code to use type hints in order to ensure the reliability and maintainability of our codebase.

Using [Type Hints](https://peps.python.org/pep-0484/) and [Pydantic](https://pydantic-docs.helpmanual.io/) in our project allows us to improve the quality and reliability of our code. Type hints provide a way to specify the expected data types for function arguments and return values, which can help catch errors at runtime and improve code readability. Pydantic adds additional features on top of type hints, such as automatic data validation and data conversion, which can help prevent errors and ensure that our code is working with consistent, correct data.

### Running tests

To run the whole test suite.

```bash
make test
```

To run individual tests:

```bash
ENV=test poetry run python3 -m pytest {Path to the test file}
```

### Pull Requests

- Please create pull requests early to start the conversation about the changes.
- The pull request title should summarize the contribution. Prefix with [WIP] if the PR is still a work in progress.
- All new codes should have an extensive suite of tests with necessary fixtures included. All CI tests need to pass before merging.

### Deployment

We use GitHub workflows to manage CI and CD pipelines. Once the new PR is merged, a new docker image will be built and pushed to [container repository](https://aws.amazon.com/ecr/). Currently, the final step in applying Terraform change is managed by Huma DAO.
