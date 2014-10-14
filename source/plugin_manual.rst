Manual Plugin for APIx
======================

The Manual Plugin for APIx is just like `man page`_ for UNIX. Its goal is to generate human-friendly manual of your API and its resources on-the-fly. 

The manual comes in two parts:
    - The main section which provides:
        - a list of all your (public) resources.
        - a documentation of the API Inputs and Outputs, built from the main config options.
        - a human-friendly view at http://my_api.domain.tld/help.

    - The resource section which:
        - describes each resource in details.
        - uses `PHPDoc`_  (and `Javadoc`_) annotation format.
        - accessible at http://my.api.tld/help/path?method=GET

The following guidelines ensure that the content of your doc blocks comment will be parsed properly and will fit with the output. 

Basic Usage
===========
Here is an example of annotating a simple resource.

.. code-block:: php
    
    use Apix;

    $api = new Apix\Server();

    $api->onRead('/my_resource/:name/:optional',
        /**
         * Synopsis.
         * Long Description.
         * @param  type  $name      Description.
         * @param  type  $optional  Optional. Description.
         * @return type             Response description.
         */
         function ($name, $optional=null) {
            // whatever...
         }
    );



Synopsis
=====

A short and concise description of the resource.
It cannot be more than one line long. And generally ends with a period.

Markup of any kind are not permitted.

Long description
=====
A more detailled description of the resource which can pan over multi-lines.

Markup are permitted.

Tags
=====

Resource variables
------------------
The **@param** tag is used to document a single argument which is part of the resource path. 

It MUST contain a Type (e.g. a class name, array) and a name followed by a description.

It is good practice to note if the param has a Default value (or wether it is Optional) before the description such as:

.. code-block:: php
    
    * @param  string   $name    Default "Fork". The name of an item to act upon.
                                e.g. indicated as "../:name" in the resource path.
 
Request parameters
------------------
The **@global** tag is used to document a single parameters which is part of the request's `query string`_.

Its definition is similar to the @param tag.

.. code-block:: php
    
    * @global  integer   $limit    Defautl 100. The max number of sub-items to show.
                                   e.g. this could be "..?limit=10" in the query string.


Response
---------
The **@return** tag is used to document the resource response.

.. code-block:: php
    
    * @return \Response Return an \Response object [ ... ].


==========================
Additional optionals tags
==========================

Usage
-----
The **@usage** allow to overide the resource path name.

.. code-block:: php

    * @usage /profiles[?admin=0&...]

===========

.. code-block:: php

    $api->onCreate('/profile/:name',
        /**
         *
         *
         * @see Function/method/class relied on
         * @link Some Blah blah http://some.url/foo/bar
         *
         * @param type  $var    Description.
         * @param type  $var2   Optional. Description.
         *
         * @global type $varname1  Default <value>. Short description.
         * @global type $varname2  Default <value>. Short description.
         * @global type $varname3  Default <value>. Short description.
         *
         * @return type Description.
         *
         * @example http://example.com/my/bar Documentation of Foo balajdksfjlsdfj lsnjflksflksdjlfkjsdlkfjsdlkfjsldfj 
         * @example Documentation of Foo http://example.com/my/bar
         *
         * @see http://example.com/my/bar Documentation of Foo.
         * @see MyClass::$items For the property whose items are counted.
         * @see MyClass::setItems() To set the items for this collection.
         *
         * @license Some licencing infos, datat set part of XXX.
         *
         * @internal Typically used for adding notes for internal use only.
         * @todo Documents some left TODOs...
         *
         * @version 1.0.1
         * @copyright Some additional copyright
         * @apix_cors enable=1
         */
         function ($qkw=null, $filters=null) {
            // whatever...
         }
    );

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
