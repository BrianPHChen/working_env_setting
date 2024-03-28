# Sphinx

Sphinx makes it easy to create intelligent and beautiful documentation.

I prefer use python, the following steps are based on `pip` tool

## Prerequisite
* `pyenv` and `perl`

can be installed through `oh-my-zsh` plugins
```bash
plugins=(
  ...
  pyenv
  perl
)
```

## Install Sphinx
I'd suggest use `pyenv` to generate a virtual env and do the following install steps.
```bash
pip install sphinx
pip install sphinx_rtd_theme
```

## Install Latex
```
apt install texlive-latex-extra
apt install latexmk
```

## Create the documentation project
```bash
// .venv is virtual env
sphinx-quickstart docs
```
After answering the questions. There should be new folder with the following content
```bash
docs
├── build
├── make.bat
├── Makefile
└── source
   ├── conf.py
   ├── index.rst
   ├── _static
   └── _templates
```

## Configure
In conf.py, first to add the path
```python
import os
import sys
from pathlib import Path
sys.path.insert(0, os.path.abspath(os.path.join('..', '..')))

# omit the middle

extensions = [
    'sphinx.ext.doctest',
    'sphinx.ext.autodoc',
    'sphinx.ext.viewcode',
    'sphinx.ext.napoleon'
]

# omit the middle

html_theme = 'sphinx_rtd_theme'
```

# Build the doc
```bash
// for html
sphinx-build -M html docs/source/ docs/build/

// for pdf
sphinx-build -M latexpdf docs/source/ docs/build/
```
