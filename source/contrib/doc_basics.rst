Contributing to the documentation
=================================

:Author: My Name


You can edit the docs online by clicking the "**edit this page**" button on any
given page which will open an online editor for that page.

Or you can fork the `Github's repo <https://github.com/frqnck/apix-docs>`_,
add your modifications, followed by a pull request.

Formatting guidelines
---------------------

The documentations are written and comply to the
`reStructuredText <http://en.wikipedia.org/wiki/ReStructuredText>`_ format
which is a plain text markup syntax similar to Markdown. See the official
`Quick Reference <http://docutils.sourceforge.net/docs/user/rst/quickref.html>`_. 

Basics
------

First, always use UTF-8 (with BOM) as encoding and 4-spaces (no tabs) for indentation.

Text should be wrapped at 80 columns. The only exception should be long URLs,
and code snippets.

Headings
^^^^^^^^

Heading are are created by underlining the title with the following characters:

- ``=`` Headline 1 for the page title.
- ``-`` Headline 2 for the page sections.
- ``^`` Headline 3 for sub-sections.
- ``~`` Headline 4 for sub-sub-sections.
- ``"`` Headline 5 for sub-sub-sub-subsections

The length of the underline must be as long as the headline.

The headings are preceded and followed by a blank line.

Paragraphs
^^^^^^^^^^

Paragraphs are simple blocks of text, with all the lines at the same level of
indentation. Paragraphs should be separated by more than one empty line.

Inline styles
^^^^^^^^^^^^^

* ``*italics*`` for *italics*.
* ``**bold**`` for **bold**.
* ````code```` for ``code or fixed-space literals``.

If you need to escape a character use a backslash e.g. \\*.

Lists
^^^^^

List markup is very similar to Markdown. 

Unordered lists
~~~~~~~~~~~~~~~

.. code-block:: rest

    * This is a bullet.
        * This is a sub bullet.

Numbered lists
~~~~~~~~~~~~~~

.. code-block:: rest

    1. First line
    2. Second line
    #. Use ``#`` for auto numbering.
    #. Would be listed as 4.

Description lists (aka <dl>)
~~~~~~~~~~~~~~~~

.. code-block:: rest

    term/name (aka <dt>)
        definition (aka <dd>)

Links
^^^^^

External links
~~~~~~~~~~~~~~

    ```Info.com <http://www.info.com>`_`` produces an external
    link to `Info.com <http://www.info.com>`_.

Internal pages
~~~~~~~~~~~~~~

.. rst:role:: doc

    ``:doc:`documentation``` produces :doc:`documentation`.

    Also, works with absolute path. Omit the ``.rst`` extension.

.. _some-ref-label:

Cross referencing
~~~~~~~~~~~~~~~~~

.. rst:role:: ref

    For instance, using ``:ref:`some-ref-label``` produces 
    :ref:`some-ref-label`.

    Fro this to work, it needs a *unique* reference label target such as::

        .. _some-ref-label:

        Cross referencing
        ~~~~~~~~~~~~~~~~~

    Note the reference label must be unique across the entire doc. Using ``dir-page-section`` and ``namespace-class-method`` is a good practice.

Adding image/figure files
^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: rest

    .. figure:: ../images/picture.gif
        :scale: 50 %
        :alt: Some alternative text.

Check the relevant `directive <http://docutils.sourceforge.net/docs/ref/rst/directives.html#figure>`_ for more info.

Stylesheet
---------------

Individual CSS styles will eventually be referenced here.

Highlighted block
^^^^^^^^^^^^^^^^^

Special notices/blocks of information can highlighted such as:

Tips
^^^^

Use ``.. tip::`` to document or re-iterate interesting points.

.. tip::

    This is a helpful tid-bit you probably forgot.

Notes
^^^^^

Use ``.. note::`` to document some important piece of information.

.. note::

    This is a special note.

Warnings
^^^^^^^^

Use ``.. warning::`` to document potential stumbling blocks.

.. warning::

    Ths is a warning -- potential hazard!



Describing language specific features
-------------------------------------

Use the following for language specific directives:

.. toctree::
    doc_lang_php

