# [Python CI Template][git]
### :bust_in_silhouette: By [Chris Wordsworth][author]

[![Build Status][build.svg]][travis]

---

Derived from the pypa sample project [located here][pypa/sample].

Incorporates Travis-CI automated testing methodologies and borrows structure and configuration files previously adopted in my node.js development workflow.

---

#### TODO:
- [ ] Add pre-commit hooks to run autopep8 (`autopep8 -iraa .`)
- [x] Add testing hooks to travis
- [x] Incorporate tox build system
- [x] Implement [PEP 517][517]
---

## PEP 517
PEP 517 specifies the use of "*a build-system independant format for source trees*".

Basically, the ideas introduced in PEP 517 and the implementation provided by setuptools are implemented through the use of [`setup.cfg`][setup.cfg] and [`pyproject.toml`][pyproject.toml] files.

This template provides examples of these files to act as both the starting-point for new projects, and a reference-point for more complex project structures.

## Building the Sample Package
The package can be built by opening a shell in the root project directory and calling **`pip wheel .`**.
You may optionally specify a directory for the compiled package to be placed in by providing the argument **`-w <dir>`**, or **`--wheel-dir <dir>`**. For example, the complete invocation might look like this:

```
pip wheel --wheel-dir ./dist/ .
```

## Installing the Built Package
After the package has been built, you can install it locally by calling **`pip install <path-to-package.whl>`**

Upon installation you should be able to call upon the entry-point configured in `setup.cfg` by calling **`example-add`**. It should provide something similar to the following output:
```
> example-add
Call your main application code here
Hello Preview!
15
```
This behaviour originates from `src/example/__init__.py`, which contains the following code:
```python
from example.calculator import Calculator


def main():
    "Entry point for the application script"
    print("Call your main application code here")

    print("Hello Preview!")
    print(Calculator.add(1, 2, 3, 4, 5))

```

## Continuous Integration using Travis-CI
This project template leverages Travis-CI's functionality to run integration tests each time a commit is pushed to GitHub. For this functionality to work from your own repos, you will need a Travis-CI account that is authorised with your GitHub. Once this is set up, Travis-CI will automatically build any commits that include a `.travis.yaml` file. This file is used to define the behaviour of the Travis-CI automated build system.

More resources and documentation can be found on the [Travis-CI documentation website][travis-ci].

## tox
I won't go over tox in any detail, other than to say that it is used to manage build automation and testing within the Travis-CI environment. It can also be called locally during development by calling `tox` from the project directory.

Further information is freely available [on the internet][tox].

---

[git]: https://github.com/cmw278/python-template
[author]: https://github.com/cmw278/
[build.svg]: https://travis-ci.com/cmw278/python-template.svg?branch=master "Travis-CI build status"
[travis]: https://travis-ci.com/cmw278/python-template

[pypa/sample]: https://github.com/pypa/sampleproject "PyPA sample project"
[517]: https://www.python.org/dev/peps/pep-0517 "Uses `setup.cfg` and `pyproject.toml`"

[setup.cfg]: https://setuptools.readthedocs.io/en/latest/setuptools.html#id52 "The setuptools specification for a setup.cfg file"
[pyproject.toml]: https://setuptools.readthedocs.io/en/latest/setuptools.html#id53 "The setuptools specification for a pyproject.toml file"
[travis-ci]: https://docs.travis-ci.com/ "Travis-CI Documentation"
[tox]: https://tox.readthedocs.io/en/latest/ "tox documentation"
