Assets
======

For (nearly) every website or web application you will need some kind of assets (like css, javascripts or images).
The kiwi asset system is helping you to copy/symlink the assets to the right place (inside a modular directory
structure) and provides a helper to generate urls to selected assets.

.. note:: The asset system doesn't provide any functionality on compressing/compiling of assets. In simple words it helps you to locate asset folders and copy/symlink them. What kind of frontend setup (grunt, gulp, sass, less etc) you are using is completely up to you (and also your responsibility to setup correctly.

The default config of the asset system should look similar to this:

.. code-block:: php

    [asset_url] => null
    [asset_path] => null
    [prepend_commit] => false
    [prepend_base_path] => true
    [directories] =>
        [admin42] =>
            [target] => 'admin/admin42'
            [source] => 'vendor/fruit42/admin42/assets/dist/'
        [media42] =>
            [target] => 'admin/media42'
            [source] => 'vendor/fruit42/media42/assets/dist/'
        [frontend42] =>
            [target] => 'admin/frontend42'
            [source] => 'vendor/fruit42/frontend42/assets/dist/'
        [application] =>
            [target] => 'application'
            [source] => 'module/application/assets/dist/'

.. tip:: With ``./bin/fruit config assets`` you can check your local asset config

Directories
~~~~~~~~~~~

Directories is a config list of target sources which will be symlinked/copied to the target folder through this command::

    ./bin/fruit config assets


Prepend Commit
~~~~~~~~~~~~~~
To avoid browser caching issues on your project you can enable ``prepend_commit`` which will prepend a ``v-<commit hash>`` to
the asset url. Per default the short version of your git commit hash will be used. If there is now git available, a random hash
will be used.

.. note:: The hash will be created on ``composer update`` or ``composer install``. Therfor you don't need a working git on your production server

.. note:: You may have to adopt your rewrite rules on your server

Examples
~~~~~~~~
Assume your project is running under ``www.your-project.local/app/``.

With this config:

.. code-block:: php

    [asset_url] => null
    [asset_path] => '/assets'
    [prepend_commit] => false
    [prepend_base_path] => true
    [directories] =>
        [admin42] =>
            [target] => 'admin/admin42'
            [source] => 'vendor/fruit42/admin42/assets/dist/'

When ``/css/styles.min.css`` from namespace ``admin42`` is request::

    /app/assets/admin/admin42/css/styles.min.css

With this config:

.. code-block:: php

    [asset_url] => null
    [asset_path] => '/assets'
    [prepend_commit] => true
    [prepend_base_path] => true
    [directories] =>
        [admin42] =>
            [target] => 'admin/admin42'
            [source] => 'vendor/fruit42/admin42/assets/dist/'

When ``/css/styles.min.css`` from namespace ``admin42`` is request::

    /app/assets/v-54fah56/admin/admin42/css/styles.min.css

With this config:

.. code-block:: php

    [asset_url] => 'https://static.your-project.com/'
    [asset_path] => '/assets'
    [prepend_commit] => true
    [prepend_base_path] => true
    [directories] =>
        [admin42] =>
            [target] => 'admin/admin42'
            [source] => 'vendor/fruit42/admin42/assets/dist/'

When ``/css/styles.min.css`` from namespace ``admin42`` is request::

    https://static.your-project.com/app/assets/v-54fah56/admin/admin42/css/styles.min.css

