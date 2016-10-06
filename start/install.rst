Installation
============

Requirements
------------

To install kiwi42, you will need:

- PHP 5.5+/7.0+
- MySQL or equivalent
- `Composer`_

.. tip:: kiwi42 ships with ZF skeleton's `Vagrantfile`_ and `Dockerfile`_. Feel free to use these if you want to virtualize your development environment. Refer to the respective documentations for installation and setup.


Install
-------

1. To install the latest stable version run from your command line (CLI) within the project's root directory::

    composer install

2. Set write permissions/ownership to the ``data`` folder recursively for the user that will run the application.

3. Run the following commands provided by kiwi42's own :doc:`/start/fruit` which will be explained in detail later on::

    bin/fruit development on
    bin/fruit assets
    bin/fruit migration-migrate


.. note:: For Windows users: the ``assets`` command tries to **symlink** folders from modules' ``assets`` folders to the ``public`` folder. Use the command's additional ``--copy`` option to copy files instead.

Now configure the application to your needs which will be explained in detail in the following :doc:`/start/configure` section.

.. _Composer: https://getcomposer.org/
.. _Vagrantfile: https://github.com/raum42/kiwi42/blob/master/Vagrantfile
.. _Dockerfile: https://github.com/raum42/kiwi42/blob/master/Dockerfile
