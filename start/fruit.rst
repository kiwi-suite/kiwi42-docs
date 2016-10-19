Fruit Console
=============

kiwi42 has its own console which is powered by an extended Zend Console within the core42 module.

To see all currently registered commands run the following on your command line from your project root::

    $ bin/fruit

Modules may register their own commands. kiwi42's default application module includes an example command to show how it works.

The command's CLI route is registered in ``module/application/config/cli.config.php`` and can be run like this::

    $ bin/fruit example --foo=bar

To show this or another command's help and parameter descriptions run::

    $ bin/fruit help example
