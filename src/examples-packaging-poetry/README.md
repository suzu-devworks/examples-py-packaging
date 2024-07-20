# examples-packaging-poetry

[![Poetry](https://img.shields.io/endpoint?url=https://python-poetry.org/badge/v0.json)](https://python-poetry.org/)

This is a project to learn packaging using poetry.


## Table of Contents <!-- omit in toc -->

- [examples-packaging-poetry](#examples-packaging-poetry)
  - [Configure environment](#configure-environment)
  - [Install Poetry](#install-poetry)
  - [Getting started](#getting-started)
  - [More Information](#more-information)

## Configure environment

If you don't want to pollute the environment, have a separate venv:

```shell
python -m venv .venv.poetry
. .venv.poetry/bin/activate
```

After updating pip:

```shell
python -m pip install --upgrade pip
```


## Install Poetry

```shell
pip install poetry
```


## Getting started

Move to the root of your project...

```shell
cd src/examples-packaging-poetry
```

Install this project:

```shell
poetry install
```

When you run it:

```console
$ examples-poetry-cli

Hello poetry.
```


## More Information

- [poetry - docs](/docs/packaging/poetry.md)
