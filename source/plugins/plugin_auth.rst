Auth ``Apix\Plugin\Auth``
=========================

The Auth Plugin for APIx provides an authentification mechanism for your API. 

This is enable thru method/closure's annotation for each resource that require users or groups authentification.

.. note::

    This plugin is part of the core distribution. It is enable by default.
    For more information see :ref:`plugins-managing`.

Generic Usage
-------------

In order to inforce authentification of a resource, your need to use the ``@api_auth`` tag annotation.

.. code-block:: php
    
    use Apix;

    $api = new Apix\Server();

    $api->onRead('/resource/:name',
        /**
         * ...
         *
         * @api_auth   groups=clients,testers   users=franck
         */
         function ($name) {
            // whatever...
         }
    );

In the example above, only the specified `users` and/or `groups` will be given access on succesful autentification.

Authentification is skipped altogether, if:
    - `groups` and `users` are not provided in ``@api_auth``,
    - if one of the `group` is set to the same value as 'public_group' (set to "public" by default).

Configurable options
--------------------

The main configurable options are:

public_group
^^^^^^^^^^^^

This options is set to the string **public** by default. Use this option to change this value to fit your requirments.

adapter
^^^^^^^

Currently, two adapters are shipped with the main distribution. 

``Apix\Plugin\Auth\Basic``
""""""""""""""""""""""""""

This adapter provides HTTP `Basic`_ access authentication.

Use this over HTTPS as the credentials are not encrypted or hashed in any way.

An example of implementation:

.. code-block:: php
    
    use Apix;
    ...
    $adapter = new Plugin\Auth\Basic($c['api_realm']);
    $adapter->setToken(function (array $current) use ($c) {
        $users = Service::get('users_example');
        foreach ($users as $user) {
                if (
                    $current['username'] == $user['username']
                    && $current['password'] == $user['api_key']
                ) {
                    Service::get('session', $user);

                    return true;
                }
            }

            return false;
        });

``Apix\Plugin\Auth\Digest``
""""""""""""""""""""""""""

This adapter provides HTTP `Digest`_ access authentication.

It is use to encrypt and salt the user's credentials can be used with or without SSL. 

An example of implementation:

.. code-block:: php
    
    use Apix;
    ...
    $adapter = new Plugin\Auth\Digest($c['api_realm']);
    $adapter->setToken(function (array $current) use ($c) {
        $users = Service::get('users_example');
        foreach ($users as $user) {
            if (
                $user['username'] == $current['username']
                && $user['realm'] == $c['api_realm']
            ) {
                Service::get('session', $user);

                // Digest match againt your selected token.
                return $user['api_key'];
            }
        }

        return false;
    });


.. _Basic: http://en.wikipedia.org/wiki/Basic_access_authentication
.. _Digest: http://en.wikipedia.org/wiki/Digest_access_authentication
