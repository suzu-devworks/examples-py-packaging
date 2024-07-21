# examples-packaging-rye

[![Rye](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/rye/main/artwork/badge.json)](https://rye.astral.sh)
[![Ruff](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/ruff/main/assets/badge/v2.json)](https://github.com/astral-sh/ruff)

This project is an attempt to create package using rye.

## Table of Contents <!-- omit in toc -->

- [examples-packaging-rye](#examples-packaging-rye)
  - [Install the package manager](#install-the-package-manager)
  - [Getting started](#getting-started)
  - [More Information](#more-information)


## Install the package manager 

```shell
curl -sSf https://rye.astral.sh/get | RYE_TOOLCHAIN=`which python` RYE_INSTALL_OPTION="--yes" bash
```

After installation, load the environment and enable rye.

```shell
source "$HOME/.rye/env"
```


## Getting started

Move to the root of your project...

```shell
cd src/examples-packaging-rye
```

Install this project:

```shell
rye sync
```

The virtualenv is created automatically.


## More Information

- [Rye - docs](/docs/packaging/rye.md)
