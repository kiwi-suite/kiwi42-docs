# kiwi42 Documentation

[Read The Docs](http://kiwi42.readthedocs.io/en/latest/)

## Generate docs

__Requirements__

    $ brew install python
    $ pip install sphinx sphinx-autobuild sphinx_rtd_theme
    
__Generate Docs__    
    
    $ make html

__Generate Docs with autoreloading__

    $ sphinx-autobuild . _build/html -i ".idea/*" -i ".git/*"
