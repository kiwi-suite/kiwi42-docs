Installation
============

Requirements
------------

To install kiwi42, you will need:

- PHP 5.6/7.0+ with intl extension
- MySQL or equivalent
- `Composer`_


Install
-------

Use `Composer`_'s ``create-project`` in your command line (CLI)::

    $ composer create-project raum42/kiwi42 kiwi42-project
    $ cd kiwi42-project


Now run the setup command provided by kiwi42's own :doc:`/start/fruit` which will be explained in detail later on::

    $ bin/fruit setup

This will among other things turn on development mode, run database migrations and symlink/copy the assets folders given by the credentials you provided. The resulting configuration can be found in the ``config/autoload`` directory.

**Permissions**

Set write permissions/ownership to the ``data`` folder recursively for the user that will run the application.

.. note:: **For Windows users:** the ``assets`` command tries to **symlink** folders from modules' ``assets`` folders to the ``public`` folder. This is possible on Windows 7 and newer and requires to be run with administrative permissions. Otherwise use the command's additional ``--copy`` option to copy files instead::

    $ bin/fruit assets --copy


Serve
-----

To run your kiwi42 project set up your local development server accordingly (virtual hosts) and point them to the ``public`` directory.

.. tip:: The `Zend Framework Skeleton Application`_ ships with both `Vagrantfile`_ and `Dockerfile`_. Feel free to use these if you want to virtualize your development environment. Refer to the respective documentations for installation and setup.


Now configure the application to your needs which will be explained in general in the following :doc:`/start/configure` section and in detail wherever relevant.

.. _Composer: https://getcomposer.org/
.. _Vagrantfile: https://github.com/raum42/kiwi42/blob/master/Vagrantfile
.. _Dockerfile: https://github.com/raum42/kiwi42/blob/master/Dockerfile
.. _Zend Framework Skeleton Application: https://github.com/zendframework/ZendSkeletonApplication
