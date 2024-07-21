# examples-packaging-pdm

[![pdm-managed](https://img.shields.io/endpoint?url=https%3A%2F%2Fcdn.jsdelivr.net%2Fgh%2Fpdm-project%2F.github%2Fbadge.json)](https://pdm-project.org)

This is a project to learn packaging using PDM.

## Table of Contents <!-- omit in toc -->

- [examples-packaging-pdm](#examples-packaging-pdm)
  - [Install the package manager](#install-the-package-manager)
  - [Getting started](#getting-started)
  - [More Information](#more-information)


## Install the package manager 

```shell
curl -sSL https://pdm-project.org/install-pdm.py | python3 -
```

## Getting started

Move to the root of your project...

```shell
cd src/examples-packaging-pdm
```

If you don't want to pollute the environment, have a separate venv:

```shell
pdm venv create 
```

Select your environment and update the `.pdm-python`:

```shell
 pdm use -i -f .venv/
```

Install all dependencies and this project as editable:

```shell
pdm install
```

When you run it:

```console
$ examples-pdm-cli

Hello pdm.
```


## More Information

- [pdm - docs](/docs/packaging/pdm.md)
