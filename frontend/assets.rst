Assets
======

For (nearly) every website or web application you will need some kind of assets (like css, javascripts or images).
The kiwi asset system is helping you to copy/symlink the assets to the right place (inside a modular directory
structure) and provides a helper to generate urls to selected assets.

.. note:: The asset system doesn't provide any functionality on compressing/compiling of assets. In simple words it helps you to locate asset folders and copy/symlink them. What kind of frontend setup (grunt, gulp, sass, less etc) you are using is completely up to you (and also your responsibility to setup correctly.

The default config of the asset system should look similar to this:

.. code-block:: php

    [asset_url] => null
    [prepend_commit] => false
    [directories] =>
        [admin42] =>
            [target] => 'public/assets/admin/admin42'
            [source] => 'vendor/fruit42/admin42/assets/dist/'
            [base_url] => '/assets/admin/admin42'
        [media42] =>
            [target] => 'public/assets/admin/media42'
            [source] => 'vendor/fruit42/media42/assets/dist/'
            [base_url] => '/assets/admin/media42'
        [frontend42] =>
            [target] => 'public/assets/admin/frontend42'
            [source] => 'vendor/fruit42/frontend42/assets/dist/'
            [base_url] => '/assets/admin/frontend42'
        [application] =>
            [target] => 'public/assets/application'
            [source] => 'module/application/assets/dist/'
            [base_url] => '/assets/application'

.. tip:: With ``./bin/fruit config assets`` you can check your local asset config

Directories
~~~~~~~~~~~

Directories is a config list of target sources which will be symlinked/copied to the target folder through this command::

    ./bin/fruit config assets

Additional you can register a base_url per directory which can be used by the assetUrl :doc:`/frontend/view_helpers`.

Asset Url
~~~~~~~~~
Perhaps you want to deliver your assets from a different host like a static host or CDN. The ``asset_url`` provides the
possibility to append a string to assets url like

.. code-block:: php

    [
        'assets' => [
            'asset_url' => '//static.yourhost.com'
        ]
    ]

Per default ``asset_url`` is null. In this case the basePath of the project will be used.

Prepend Commit
~~~~~~~~~~~~~~
To avoid browser caching issues on your project you can enable ``prepend_commit`` which will prepend a ``v-<commit hash>`` to
the asset url. Per default the short version of your git commit hash will be used. If there is now git available, a random hash
will be used.

.. note:: The hash will be created on ``composer update`` or ``composer install``. Therfor you don't need a working git on your production server

For example an url which looks like this will transformed to::

    /assets/application/css/style.min.css => /v-6ef45ed/assets/application/css/style.min.css

.. note:: You may have to adopt your rewrite rules on your server
