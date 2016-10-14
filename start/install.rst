Installation
============

Requirements
------------

To install kiwi42, you will need:

- PHP 5.6/7.0+
- MySQL or equivalent
- `Composer`_


Install
-------

1. Use `Composer`_'s ``create-project`` in your command line (CLI)::

    $ composer create-project --no-dev raum42/kiwi42 kiwi42-project
    $ cd kiwi42-project
    $ composer install

2. Set write permissions/ownership to the ``data`` folder recursively for the user that will run the application.

3. Run the following commands provided by kiwi42's own :doc:`/start/fruit` which will be explained in detail later on::

    $ bin/fruit development on
    $ bin/fruit assets
    $ bin/fruit migration-migrate


.. note:: **For Windows users:** the ``assets`` command tries to **symlink** folders from modules' ``assets`` folders to the ``public`` folder. Use the command's additional ``--copy`` option to copy files instead::

    $ bin/fruit assets --copy


Serve
-----

To run your kiwi42 project set up your local development server accordingly (virtual hosts) and point them to the ``public`` directory.

.. tip:: kiwi42 ships with ZF skeleton's `Vagrantfile`_ and `Dockerfile`_. Feel free to use these if you want to virtualize your development environment. Refer to the respective documentations for installation and setup.


Now configure the application to your needs which will be explained in detail in the following :doc:`/start/configure` section.

.. _Composer: https://getcomposer.org/
.. _Vagrantfile: https://github.com/raum42/kiwi42/blob/master/Vagrantfile
.. _Dockerfile: https://github.com/raum42/kiwi42/blob/master/Dockerfile
