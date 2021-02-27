# Setting Up Python Locally

---

1. Use [pyenv](https://github.com/pyenv/pyenv) to manage python installations.
2. Use [Homebrew](https://brew.sh/) to install pyenv.

```shell
brew install pyenv
```

3. See the available remote versions of python.

```shell
pyenv install --list
```

4. Install python3.9 with pyenv

```shell
pyenv install 3.9.0
```

5. Make your environment use pyenv's active python for the system default.

```shell
# Add the following to .bash_profile or .zshenv
if command -v pyenv 1>/dev/null 2>&1; then
  eval "$(pyenv init -)"
fi
```

6. Switch to a different version of python.

```shell
pyenv global 3.9.0
```

**Resources**

- [pyenv tutorial](https://realpython.com/intro-to-pyenv/)
