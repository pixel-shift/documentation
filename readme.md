# Guides

## How To Compile Documentation

Documentation is compiled via sphinx.

1. Install sphinx-build and pip: `sudo apt-get install python3-sphinx python3-pip -y`
2. Install rtd themes: `pip3 install sphinx_rtd_theme`
3. Install Pygments code block lexer: `pip3 install Pygments`
4. From the folder you cloned the repo into, build the docs with `sphinx-build -b html -a -E ./source <output folder>`
