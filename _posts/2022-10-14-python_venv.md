---
title:  Python Virtual Environments
categories: [Python]
tags: [python]
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

---

Create virtual environment:
```terminal
python3 -m venv .venv
```

Activate virtual environment:
```terminal
source .venv/bin/activate
```

---

## Using pyenv with VSCode

Open workspace settings:
`.vscode/settings.json`

Add:
```json
"python.terminal.activateEnvironment": true
```

{% include signature.md %}