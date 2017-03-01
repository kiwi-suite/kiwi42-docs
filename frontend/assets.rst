Assets
======

For (nearly) every website or web application you will need some kind of assets (like css, javascripts or images).
The kiwi asset system is helping to symlink/copy assets to the right place (inside a modular directory
structure) and provides a helper to generate urls to selected assets.

Do symlink/copy your assets just run::

    ./bin/fruit assets


.. note:: **For Windows users:** the ``assets`` command tries to **symlink** folders from modules' ``assets`` folders. This is possible on Windows 7 and newer and requires to be run with administrative permissions. Otherwise use the command's additional ``--copy`` option to copy files instead::

    $ bin/fruit assets --copy

.. note:: The asset system doesn't provide any functionality for compressing/compiling of assets but helps to locate asset folders and copy/symlink them. What kind of frontend setup (grunt, gulp, sass, less etc) you are using is completely up to you (and also your responsibility to setup correctly.

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

.. tip:: With ``./bin/fruit config assets`` you can check your local asset config.

Directories
~~~~~~~~~~~

Directories is a config list of target sources which will be symlinked/copied to the target folder through this command::

    ./bin/fruit config assets


Prepend Commit
~~~~~~~~~~~~~~
To avoid browser caching issues you can enable ``prepend_commit`` which will prepend a ``v-<commit hash>`` to
the asset url. Per default the short version of your git commit hash will be used. If git is unavailable a random hash
will be used instead.

.. note:: The hash will be created when running ``composer update`` or ``composer install``. Therefore it is not needed to have git installed on the production servers.

.. note:: You may have to adopt your rewrite rules on your server.

Examples
~~~~~~~~

See :doc:`/frontend/view_helpers` to see how to add URLs to assets in views.

The following asset URLs will be generated depending on the assets configuration.

Without ``prepend_commit``::

    /app/assets/admin/admin42/css/styles.min.css


With ``prepend_commit`` enabled::

    /app/assets/v-54fah56/admin/admin42/css/styles.min.css

With ``asset_url`` set to e.g. ``https://static.my-project.com/`` and ``prepend_commit`` enabled::

    https://static.your-project.com/app/assets/v-54fah56/admin/admin42/css/styles.min.css

