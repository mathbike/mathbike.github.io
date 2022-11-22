---
title:  Python Virtual Environments
categories: [Python]
tags: [python]
---

## Set up a Python environment in vscode

```sh
echo "enter the name of the directory:" && read NAME
git clone https://github.com/mathbike/newpy ~/$NAME
cd $NAME
rm -rf .git newpy.sh
python3 -m venv .venv
deactivate
COMMANDS_TXT="z.1_commands.txt"
echo -e "########## COMMANDS ##########\n" > $COMMANDS_TXT
echo "pip freeze > requirements.txt" >> $COMMANDS_TXT
code .
```

```terminal
pip freeze > requirements.txt
```

## Some other things

Pip install requirements.txt
```terminal
pip install -r requirements.txt
```

Activate virtual environment:
```terminal
source .venv/bin/activate
```

---

## pyenv

GitHub repo:
<a href="https://github.com/pyenv/pyenv" target="_blank">https://github.com/pyenv/pyenv</a>

Commands Reference:
<a href="https://github.com/pyenv/pyenv/blob/master/COMMANDS.md" target="_blank">https://github.com/pyenv/pyenv/blob/master/COMMANDS.md</a>

---

Required packages:
```terminal
sudo apt install -y make build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev \
libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev python-openssl \
git
```

Install:
```terminal
git clone https://github.com/pyenv/pyenv.git ~/.pyenv
```

Add the following to your `.bashrc`:
```sh
# pyenv
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init --path)"
```

---

## Using pyenv

List all available versions:
```terminal
pyenv install -l
```

Install python version:
```terminal
pyenv install [PYTHON_VERSION]
```

Show installed versions:
```terminal
pyenv versions
```

Show active version:
```terminal
pyenv version
```

Set global version:
```terminal
pyenv global [PYTHON_VERSION]
```

Set local version:
```terminal
pyenv local [PYTHON_VERSION]
```
