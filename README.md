APIx Manual & Documentation
===========================

The APIx Manual and Documentation use [reStructuredText](http://docutils.sourceforge.net/rst.html) format/parser and the [Sphinx](http://sphinx-doc.org) tool.

There are two distinct documentation trees contained within this directory:

Official Manual
---------------

* [Introduction](source/introduction.rst)
* [Quick Start](source/quickstart.rst>)
* [Configuration](source/config.rst>)
* [Example Project](source/example.rst>)
* [Plugins](source/plugins/index.rst>)

This manual is also rendered online on: Officila APIx Manual (http://apix.readthedocs.org)

API Documentation
-----------------

This is extracted from the APIx source code and comments using `Javadoc <http://en.wikipedia.org/wiki/Javadoc>`_ and `PHPDoc <http://en.wikipedia.org/wiki/PHPDoc>`_ formats.

Viewable at: [index](source/apix/index.rst>)

Installation
------------

To install Sphinx and dependencies run ``pip install sphinxcontrib-phpdomain`` then run ``make html``.

Contributing
------------

See [Contributing](CONTRIBUTING.md).

License
-------
APIx is licensed under the New BSD license -- see the [LICENSE](LICENSE) for the full license details.
