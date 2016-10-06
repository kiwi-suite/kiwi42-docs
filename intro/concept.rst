Core Concepts
=============

kiwi42 is a `Zend Framework`_ (ZF) based Content Management System (CMS) targeted at developers. It's meant for small to large scaled projects while maintaining full flexibility for individual requirements at all times.

The core feature set includes but is not bound to:

- Users & Permissions by Roles
- Multilingual Contents
- Content Management
- Event Management
- Media Management
- Translation


Content Data Hierarchy
----------------------

The data structure for site contents within kiwi42 may be reduced to this simple hierarchy:

- Sitemap taking care of depth, language and versioning
    - Pages with a defined Page Type
        - Sections/Areas within Pages
            - Blocks dynamically added to Sections/Areas
                - Fields holding content data or referencing to Media, Links, etc.

Next to the structured content data above kiwi42 allows to easily maintain arbitrary resources that may be administrated through basic Create, Read, Update and Delete (CRUD) actions. kiwi42 provides the basic functionality and views for these but may be extended for more sophisticated and complex use cases.


Directory Structure
-------------------

kiwi42 lends its directory structure from the `ZF Skeleton application for zend-mvc projects`_.
Only a few structural requirements have to be fulfilled within custom modules to work with kiwi42 which will be mentioned and highlighted wherever applicable within this documentation. Apart from these kiwi42 does not dictate how developers should set up their application to maintain an optimal workflow - *especially* when it comes to the front end. Have it your way.


User Interface
--------------

The administration area's User Interface (UI) is enhanced by `AngularJS`_ (version 1 on principle as of this writing) for a fluid and dynamic user experience (UX) while keeping the interface itself to a bare minimum. It is based on Flatfull's `Angulr Theme`_ which maintains optimal usability on mobile devices.

The main AngularJS module is developed within the admin42 module and gets extended from within other modules as well.


Architecture
------------

kiwi42 itself may be considered being a slightly adapted and opinionated version of the `ZF Skeleton application for zend-mvc projects`_. raum42's additional custom modules and extensions follow ZF's architectural patterns to a very high degree whenever possible and useful.

However specific parts and tasks have been replaced by more specialized libraries such as:

- `Stash Cache`_ for caching
- `Swiftmailer`_ for sending mails
- `Monolog`_ for logging

Take a look at the latest `composer.json`_ file to get a sense of how the stack is composed.

raum42 provides its own set of modules as an application foundation and are declared as dependencies of kiwi42. Three main modules take care of abstracting and enhancing ZF to fit kiwi42's needs from "end to end":

**core42**

*TK*

**admin42**

*TK*

**frontend42**

*TK*


.. _Zend Framework: https://framework.zend.com/
.. _AngularJS: https://angularjs.org/
.. _Angulr Theme: http://flatfull.com/themes/angulr/angular/
.. _ZF Skeleton application for zend-mvc projects: https://github.com/zendframework/ZendSkeletonApplication
.. _Stash Cache: https://github.com/tedious/Stash
.. _Swiftmailer: https://github.com/swiftmailer/swiftmailer
.. _Monolog: https://github.com/Seldaek/monolog
.. _composer.json: https://github.com/raum42/kiwi42/blob/master/composer.json
