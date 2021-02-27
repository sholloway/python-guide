# Using Virtual Environments

---

Always use virtual environments.

## Creating a virtual environment

0. Switch to the version of python you the environment to use.

```shell
pyenv global 3.9.0
```

1. Create a virtual environment with the OOTB venv.

```shell
python -m venv dir-name
# This will create a directory named dir-name if it doesn't exist.
# create directories inside it containing a copy of the Python interpreter, the standard library, and various supporting files.
```

2. Activate the virtual environment.

```shell
# Unix/OS X
source dir-name/bin/activate
```

3. Upgrade pip in the virtual environment.

```shell
python -m pip install --upgrade
```

3. Install the packages you want

```shell
python -m pip install -r requirements.txt
```

**Resources**

- [Offical Docs](https://docs.python.org/3/tutorial/venv.html)
- [Brett Cannon's Take](https://snarky.ca/a-quick-and-dirty-guide-on-how-to-install-packages-for-python/)
