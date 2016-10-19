View Helpers
============

In view scripts there's usually need for functions aside from trivial control structures and displaying variables (like
e.g. formatting, generating links, ...)  which View Helpers can provide.

assetUrl
--------

Generates relative or absolute URLs to assets depending on the assets configuration.

.. code-block:: php

    <?= $this-assetUrl('/css/style.min.css', 'application') ?>

Both parameters are optional. The first parameter determines the path to the file (relative from the asset
url base or, when a second parameter is given, relative to the ``target`` parameter).
The second parameter declares the key of your asset directory config. See :doc:`/frontend/assets` for further information.
