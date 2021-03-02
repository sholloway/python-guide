# Creating a Python CLI Application

---

## Create an App with Poetry

[Poetry](https://python-poetry.org/) is a dependency manager and build tool that also provides scaffolding. These are the steps to create a new CLI app.

1. Create the project skeleton.

```shell
poetry new my-project
```

2. Add dependencies to the pyproject.toml file.
   Put runtime dependencies under _tool.poetry.dependencies_ section and
   developer dependencies under the _tool.poetry.dev-dependencies_ section.

For example, to use [click](https://click.palletsprojects.com/en/7.x/) for parameter parsing and [rich](https://github.com/willmcgugan/rich) for CLI UI add the following.

```shell
poetry add click rich
```

And to do add development dependencies:

```shell
poetry add -D pytest mypy coverage pyflakes
```

3. Working with the virtual environment.
   Poetry creates a virtual environment when you use the _new_ or _init_ command.
   To see the details on the virtual environment use the below.

```shell
poetry env info
```

4. Run your app or tools in the context of the virtual environment.
   Note: When a script is added or updated, run poetry install to make them available in the project's virtualenv.

```shell
poetry run your_script or tool
```

5. To build your app use the _build_ command.

**Resources**

- [zipapp](https://docs.python.org/3/library/zipapp.html#module-zipapp)
- [poetry](https://python-poetry.org/)
