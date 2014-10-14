APIx Manual & Documentation
===========================

The APIx Manual and Documentation use `reStructuredText <http://docutils.sourceforge.net/rst.html>`_ format/parser and the 
`Sphinx <http://sphinx-doc.org/>`_ tool.

There are two distinct documentation trees contained within this directory:

Official Manual
---------------

* `Introduction <source/introduction.rst>`_
* `Quick Start <source/quickstart.rst>`_
* `Configuration Start <source/config.rst>`_
* `Example Project <source/example.rst>`_
* `Plugins <source/plugins.rst>`_

This manual is also rendered online on: http://apix.readthedocs.org/

API Documentation
-----------------

This is extracted from the APIx source code and comments using `Javadoc <http://en.wikipedia.org/wiki/Javadoc>`_ and `PHPDoc <http://en.wikipedia.org/wiki/PHPDoc>`_ formats.

Viewable at: `index <source/apix/index.rst>`_

Installation
------------

To install Sphinx and dependencies run ``pip install sphinxcontrib-phpdomain`` then run ``make html``.

Contributing
------------

See `Contributing <CONTRIBUTING.md>`_.

License
-------
APIx is licensed under the New BSD license -- see the `LICENSE.txt <LICENSE.txt>`_ for the full license details.
