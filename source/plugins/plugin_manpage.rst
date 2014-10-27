ManPage ``Apix\Plugin\ManPage``
===============================

    The ManPage Plugin for APIx is just like `man page`_ for UNIX.

An intro
--------

Its main goal is to generate **up-to-date** and **human-friendly** manual of your
API and document all of its resources.

The manual comes in two parts:
    - The main section which provides:
        - a list of all your (public) resources.
        - documents all the Inputs and Outputs.

    - The resource section which:
        - describes each resource in details, 
        - uses `PHPDoc`_  (and `Javadoc`_) annotation format.

.. note::

    This plugin is part of the core distribution and enable by default.
    For more information see :ref:`plugins-managing`.

.. tip::

    You can learn much more about the routing system in the :doc:`Routing chapter </book/routing>`.

Plugin options
--------------

==========================================  ===========
Option                                      Description
==========================================  ===========
**enable** *boolean*                        Default True. Wether to enable or not this plugin.

**example** *string*                        String to append to extracted @example.
**see** *string*                            String to append to extracted @see.
**link** *string*                           String to append to extracted @link.
**copyright** *string*                      String to append to extracted @copyright.
**license** *string*                        String to append to extracted @license.

==========================================  ===========



Basic usage
-----------
Here is an example of annotating a simple resource.

.. code-block:: php
    
    $api = new Apix\Server();

    $api->onRead('/beers/from/:where/:type',
        /**
         * Title - short description.
         * Long description.
         * @param   string      $where      Default "London". The location name.
         * @param   type        $type       Optional. A beer type e.g. Larger, Pale Ale, Stout.
         * @global  integer     $limit      Default 100. The number of brand to list.
         * @return type                     The response description.
         */
         function ($where, $type=null) {
            // ...
         }
    );

Generic annotation
------------------

Title - Short description
^^^^^^^^^^^^^^^^^^^^^^^^^

A short and concise description or title for the resource. It represents its **Synopsis**.
It cannot be more than one line long. And generally ends with a period.
Markup of any kind are not permitted.

Long description
^^^^^^^^^^^^^^^^

A more detailled description of the resource which can pan over multi-lines.
Markup are permitted.

Essential annotation tags
-------------------------

==========================================  ===========
Annontation                                 Description
==========================================  ===========
**@param** *type* *$name* *description*     Documents a resource path parameter.
**@global** *type* *$name* *description*    Documents a request's `query string`_ parameter.
**@return** *type* *description*            Provides the **Response** of a resource.
==========================================  ===========

.. note::
    
    If the @param or @global are optional with a default value. It is good practice to indicate
    it before the description as per the example further above.

Additional tags
---------------

==============================  ===========
Annontation                     Description
==============================  ===========
**@usage** */resource/:var*     Overrides the Synopsy's Usage field.
**@example** *description*      This tag is use to 
**@see** *reference*            Provides a "See also" to some element of documentation.
**@link** *<url>*               Displays a link to some pages.
**@copyright** *description*    Documents some copyrights details.
**@license** *<url>* *name*     Provides the name and URL of a relevant license.
==============================  ===========


.. TODO multiline arguments!
.. * @param array $args {
.. *     An array of arguments. Optional.
.. *
.. *     @type type $key1 Description. Default <value>. Accepts <value>, <value>.
.. *                      (aligned with Description, if wraps to a new line)
.. *     @type type $key2 Description.
.. * }

.. _man page: http://en.wikipedia.org/wiki/Man_page
.. _PHPDoc: http://en.wikipedia.org/wiki/PHPDoc
.. _Javadoc: http://en.wikipedia.org/wiki/Javadoc
.. _query string: http://en.wikipedia.org/wiki/Query_string
