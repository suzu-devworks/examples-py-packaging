# examples-packaging-setup

This is a project to learn packaging using setuptools.

<!-- /* spell-checker:words setuptools */ -->

## Table of Contents <!-- omit in toc -->

- [examples-packaging-setup](#examples-packaging-setup)
  - [Configure environment](#configure-environment)
  - [Getting started](#getting-started)
  - [More Information](#more-information)


## Configure environment

If you don't want to pollute the environment, have a separate venv:

```shell
python -m venv .venv.setup
. .venv.setup/bin/activate
```

Update pip and setuptools wheels:

```shell
python -m pip install --upgrade pip
pip install --upgrade setuptools wheel build
```

## Getting started

Move to the root of your project...

```shell
cd apps/examples-packaging-setup
```

Install this project:

```shell
pip install -e .
```

When you run it:

```console
$ examples-setup-cli

Hello setuptools.
```


## More Information

- [Setuptools - docs](/docs/packaging/setuptools.md)
