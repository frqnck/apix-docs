Cache ``Apix\Plugin\Cache``
=========================

The Cache Plugin for APIx provides a caching layer for your APi's resources. 

Cachign is set either:
    - globaly using the configurable options,
    - and/or per individual resource using the ``@api_cache`` tag annotation.

Global usage
------------

Caching can be set or not globally. A set of main configurable options are avilabale.

These options also act as the default and inherited option for the annotated subtags.

Configurable options
^^^^^^^^^^^^^^^^^^^^

enable
^^^^^^

This options is set to the **True** by default. (TODO: review this part of the code)

adapter
^^^^^^^

By default, this option is set to **``Apix\Cache\Apc``** which handles `APC`_ and `APCu`_. 

There are adapters for Redis, Memcached and many other data/cache stores.

Checkout `Apix Cache`_ for a list of available adapters and their specific options.

default_ttl
^^^^^^^^^^^

This options is set to **10mins** by default. This is the cache lifetime, ``null`` stands forever.

runtime_flush
^^^^^^^^^^^^^

This options is set to **True** by default.

If set to True the given tags are flushed at runtime. It is recommened to disable this and do this offline  instead for instance using Cronjob.

append_tags
^^^^^^^^^^^

This holds an array of tags that will be appended to items being cached.

For instance, you may want to use this option to automatically tag all new entries with the major version of your API 'v1', or with 'dev' while developing.


Usage thru annotation
---------------------

Tag: ``@api_cache`` 
^^^^^^^^^^^^^^^^^^^

Generally, to caches the output of a resource transparently you will use a method/closure's annotation using the ``@api_cache`` tag and configure it using some subtags. The `Request-URI` acts as the unique cache id.

For instance, to cache a resource for 45 minutes you would annotate it as follow:

.. code-block:: php
    
    use Apix;

    $api = new Apix\Server();

    $api->onRead('/resource/:name',
        /**
         * ...
         *
         * @api_cache   ttl=45mins   tags=tag1,tag2
         */
         function ($name) {
            // whatever...
         }
    );



In this example, the resource will be cached under the cache id `/resource/whatever` (the Request-URI) for the amount of time provided in the subtag ``ttl``. Susequent requests to `/resource/whatever` will hit the cache or regenerate it if it is empty (or expired).

Additionally, this resource will be cached with the given tags which can be useful for grouping cached data together. For instance, this allow to run periodic purging of some specific tags. It is also useful when grouping data to unique user-group, client-group, use-cases, etc...

Subtags
^^^^^^^

ttl
"""

This sets the time-to-live in seconds. It takes either an integer representating a value in seconds or a textual datetime string such as "10days". ``ttl=null`` means `forever`. If not set, it will use the value from 'default_ttl'.

tags
""""

If provided, the cached entry will be tagged with the given tag(s).

flush
"""""

If 'runtime_flush' is enable in th configurable options then the given 

Additionally, if a'runtime_flush' is st, some tags maybe flushed/purged from the cache.

.. _APC: http://php.net/book.apc.php
.. _APCu: http://pecl.php.net/package/APCu
.. _Apix Cache: https://github.com/frqnck/apix-cache
