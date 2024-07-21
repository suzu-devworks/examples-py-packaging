# examples-packaging-pipenv

This is a project to learn packaging using pipenv.

<!-- /* spell-checker:words pipenv */ -->

## Table of Contents <!-- omit in toc -->

- [examples-packaging-pipenv](#examples-packaging-pipenv)
  - [Configure environment](#configure-environment)
  - [Getting started](#getting-started)
  - [More Information](#more-information)


## Configure environment

If you don't want to pollute the environment, have a separate venv:

```shell
python -m venv .venv.pipenv
. .venv.pipenv/bin/activate
```

After updating pip, install the package manager:

```shell
python -m pip install --upgrade pip
pip install pipenv
```


## Getting started

Move to the root of your project...

```shell
cd src/examples-packaging-pipenv
```

When you run it:

```console
$ pipenv run start

Courtesy Notice: Pipenv found itself running within a virtual environment, so it will automatically use that environment, instead of creating its own for any project. You can set PIPENV_IGNORE_VIRTUALENVS=1 to force pipenv to ignore that environment and create its own instead. You can set PIPENV_VERBOSITY=-1 to suppress this warning.
Hello pipenv.
```

It's a warning but I don't care.


## More Information

- [pipenv - docs](/docs/packaging/pipenv.md)

