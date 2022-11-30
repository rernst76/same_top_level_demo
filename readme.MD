# Same Level Demo

## QUESTION:
How do I construct a pytest project using the  standard directory structure:

```text
/src
/tests
```

## Review Starting Structure

To start with this structure is a bit odd, technically you are creating two separate packages
with the current structure. Typically you would have a containing folder, also with an `__init__.py`
which would indicate the top level package, and then your `src` and `tests` folders would be
sub-packages as they also have an `__init__.py` file.

This page in the python docs covers the topic: [6.4 Packages](https://docs.python.org/3/tutorial/modules.html)

### Working with the starting structure

We can still make this work -- we just can't use relative imports. You are not allowed
to use relative imports outside the top level package, which for `test_func1_in_tests.py`
is the `tests` package.

To move forward we need to use absolute imports.

So instead of:

```python
from ..src.func1 import function1
```

we would use:

```python
from src.func1 import function1
```

Because in the current structure `src` and `tests` are being treated as two entirely
separate packages.

### Modifying structure to allow relative imports

In order to use relative imports, we need to put the `src` and `tests`
packages in a containing packages. Let's make an `app` package.

We do this by creating a containing folder and adding an `__init__.py` file.

Then we have two options to run pytest:

- cd into the app folder: `cd app && pytest`
- tell pytest to run in app: `pytest app`

Pytest needs to know what package it is running from within, which is why if you just
run `pytest` from the `same_top_level` it will fail.

#### Using absolute imports in app

In general absolute imports are preferred, they tend to cause less problems.
We can use absolute imports even with the app structure.

We just change the import to: `from app.src.func1 import function1`


