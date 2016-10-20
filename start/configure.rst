Configuration
=============

The configuration files for a kiwi42 project can be found in ``config/autoload/``. They're prefixed with ``local.`` and therefore auto loaded and git ignored by default.

After a basic setup with fruit console there should be some separated configuration files (assets, database, ...) but they may be combined into a single ``local.config.php`` as well.

Configuration values and options will be explained in detail where they are relevant within this documentation.

Current configuration values can be inspected by using fruit console. For example to see which assets folders are registered within modules and will be symlinked/copied run the following on your command line::

$ bin/fruit config assets

As for the host independent **global project configuration** it's advised to have a look at the ``config/*.config.php`` files to see how kiwi42 is set up as a Zend Framework application.
