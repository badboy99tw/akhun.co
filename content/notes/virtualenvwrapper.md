---
title: virtualenvwrapper
lastmod: 2015-04-02
---

## Install

```shell
pip install virtualenvwrapper
```

## Environment (.bashrc)

```shell
# virtualenvwrapper

export WORKON_HOME=$HOME/.virtualenvs
export PROJECT_HOME=$HOME/works
source /usr/local/bin/virtualenvwrapper.sh
```

## Basic commands

- workon: 列出有哪些 virtualenv，或是切換到指定的 virtualenv
- mkvirtualenv
- rmvirtualenv
- mktmpenv
- lsvirtualenv
- cpvirtualenv

## References

- http://doughellmann.com/2008/05/01/virtualenvwrapper.html
- http://virtualenvwrapper.readthedocs.org/en/latest/command_ref.html
