View Helpers
============

In your view scripts, you'll need some functions aside from trivial control structures and displaying variables:
e.g. formatting, generating links, ...
View Helpers help you to perform these tasks. kiwi is shipped with the following helper:

assetUrl
--------

Usage in your view script

.. code-block:: php

    <?= $this-assetUrl('/css/style.min.css', 'application') ?>

Both parameters are optional. The first parameter determines the url path to the file (weather relative from the asset
url base or when a second parameter is given, relative from the base_url of the given config).
The second parameter declares the key of your asset directory config. See :doc:`/frontend/assets` for further information.

