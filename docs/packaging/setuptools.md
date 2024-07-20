# setuptools

> Setuptools is a collection of enhancements to the Python distutils that allow developers to more easily build and distribute Python packages, especially ones that have dependencies on other packages.

## Table of Contents <!-- omit in toc -->

- [setuptools](#setuptools)
  - [References](#references)
  - [Install](#install)
  - [Configurations](#configurations)
  - [Configuring setuptools using setup.cfg files](#configuring-setuptools-using-setupcfg-files)
    - [Controlling files in the distribution](#controlling-files-in-the-distribution)
    - [How the project was initialized](#how-the-project-was-initialized)
    - [Build package](#build-package)
    - [Using a src layout](#using-a-src-layout)
    - [Managing package version](#managing-package-version)
    - [Managing dependency packages](#managing-dependency-packages)
    - [Provide console scripts](#provide-console-scripts)
  - [`setup.py` commands](#setuppy-commands)
    - [Usage](#usage)
    - [\[clean\] Clean](#clean-clean)


## References

- https://setuptools.pypa.io/en/latest/userguide/index.html#
- https://packaging.python.org/ja/latest/guides/distributing-packages-using-setuptools/
- https://github.com/pypa/setuptools


## Install

Ensure pip, setuptools, and wheel are up to date.

```shell
python -m pip install --upgrade pip
pip install --upgrade setuptools wheel build
```

## Configurations

Currently, the mainstream way to manage projects is with pyproject.toml, as defined by PEP518.

When I looked previously, there were three examples with different patterns, but now most of them seem to have been changed to `pyproject.toml`.

1. legacy pattern of `setup.cfg` + `setup.py`
2. `pyproject.toml` + `setup.cfg`(main) compatibility pattern
3. Future-oriented patterns in `pyproject.toml`


<!-- ## Configuring setuptools using pyproject.toml files -->


## Configuring setuptools using setup.cfg files

This is a legacy pattern.

### Controlling files in the distribution

**`setup.py`**:

Serves two primary functions:

1. your project are configured
2. the command line interface for running various commands that relate to packaging tasks.

> When a PEP 517 build is invoked, setuptools will emulate a dummy setup.py file.  
> However, editable installs are not supported, so you'll eventually need a setup.py.

**`setup.cfg`**:

Ini file containing option defaults for the setup.py command.

**`README.md`**:

All projects should contain a readme file.

**`MANIFEST.in`**:

needed when you need to package additional files that are not automatically included in a source distribution.

**`LICENSE.txt`**:

Every package should include a license file detailing the terms of distribution.


### How the project was initialized

Create and move project folder:

```shell
mkdir -p src/examples-packaging-setup
cd src/examples-packaging-setup
```

Create package:

```shell
mkdir -p examples_packaging_setup/
touch examples_packaging_setup/__init__.py
```

Create two files for project settings.
There are no commands.

`setup.cfg`:

```ini
[metadata]
name = examples-packaging-setup
version = 0.1.0
description = "Python examples of packaging using setuptools."
license = MIT

[options]
install_requires =
    requests
    importlib-metadata; python_version<"3.10"
```
<!-- /* spell-checker:words importlib */ -->

If you use `setup.cfg`, `setup.py` is very simple like this:

```py
from setuptools import setup # type: ignore

setup()
```

The final directory will look like this:

```console
.
├── README.md
├── setup.cfg
├── setup.py
└── examples_packaging_setup
    └── __init__.py
```

### Build package

```shell
python -m build
```

If you get the error `No module named` build:

```shell
pip install build
```

### Using a src layout

- [Package Discovery and Namespace Packages](https://setuptools.pypa.io/en/latest/userguide/package_discovery.html#legacy-namespace-packages)

This type of layout, called the src layout, requires additional configuration.

```console
.
├── README.md
├── setup.cfg
├── setup.py
└── src
    └── examples_packaging_setup
        └── __init__.py
```

`setup.cfg`:

```diff
[options]
packages = find:
package_dir =
    =src

[options.packages.find]
where = src
exclude =
    tests*
```

### Managing package version

The version is managed globally in the top-level `__init__.py`.

```py
__version__ = "0.1.1"
```

`setup.cfg`(diff):

```diff
[metadata]
- version = 0.1.0
+ version = attr: examples_packaging_setup.__version__
```

### Managing dependency packages

There are no commands, they are handwritten.

Dependencies will be installed together when you list them in `install_requires`:

```ini
[options]
install_requires =
    requests
    importlib-metadata; python_version<"3.10"
```

Allows you to declare dependencies that are not installed by default:

```ini
[options.extras_require]
dev =
    black>=24.4.0
    build>=1.2.0
    flake8>=7.0.0
    mypy>=1.11.0
    isort>=5.13.0
    pyclean
doc =
    sphinx
```
<!-- /* spell-checker:words mypy */ -->
<!-- /* spell-checker:words isort */ -->
<!-- /* spell-checker:words pyclean */ -->

Specify the key when installing:

```shell
pip install -e .[dev,doc]
```

### Provide console scripts

How to provide console scripts in the setuptools package.

- [Entry Points](https://setuptools.pypa.io/en/latest/userguide/entry_point.html)

Create entry point

`console/command.py`:

```py
def main() -> None:
    print("Hello setuptools.")
```

`setup.cfg`:

```ini
[options.entry_points]
console_scripts =
    examples-setup-cli = examples_packaging_setup.console.command:main
```

Install the package locally:

```shell
pip install -e .
```

When you run it:

```console
$ examples-setup-cli

Hello setuptools.
```

## `setup.py` commands

- [Running setuptools commands](https://setuptools.pypa.io/en/latest/deprecated/commands.html#running-setuptools-commands)

### Usage

```shell
python setup.py --help-commands
python setup.py --help clean
```

### [clean] Clean

```shell
python setup.py clean --all
```
