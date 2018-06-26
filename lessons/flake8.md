# Flake8

## Objectives
* Discuss why flake tools are necessary and beneficial to a project
* Setup pytest-flake8
* Suppress selected warnings
* Run flake checks as part of a Travis build
* Learn about additional plugins that can enhance your flake setup

**Duration: 20 minutes**

Code style checkers are a great way to ensure that your project has a clean
and consistent style with minimal code smell. Consistent style makes it easier
for new contributors to follow the code, makes the code easier to maintain, and
helps keep all of us honest when following best-practices. Automatically
checking the code style can reduce the burden of the maintainer in reviewing
pull requests and ensures that the checks are always run.

### pytest-flake8
* Install pytest-flake8 with `conda install pytest-flake8`
* Run the tests locally with `pytest --flake8` This will find all `.py` files
  and run the checks against them.
* We have failures! That's okay, we'll leave them for now so we can make sure
  our tests fail the automated build later (always a good idea) and we'll
  ignore others in the configuration.

### Supressing warnings
* While rules are great, some of them are more restrictive that we'd like. We
  need to add some rules in `setup.cfg` to modify our flake setup.
* First, let's add a rule to extend the maximum line length - the default of
  79 characters. It's a bit restrictive and in our opinion excessively
  limiting. Add these lines to `setup.cfg` and rerun

```
[flake8]
max-line-length = 95
```

* Sometimes there are flake rules that we don't necessarily agree with either.
  They can be ignored in all files by adding them to the ignore list.

```  
[flake8]
ignore = F405 D999
max-line-length = 95
```

### Add to Travis config

### Discuss additional flake8 plugins
* pytest-flake8 will run any additional flake plugins it finds. Here are some
  of our favorites:

  - flake8-builtins!=1.4.0
  - flake8-comprehensions
  - flake8-copyright
  - flake8-docstrings
  - flake8-import-order
  - flake8-mutable
  - flake8-pep3101
  - flake8-print
  - flake8-quotes