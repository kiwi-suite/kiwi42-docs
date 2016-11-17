Page Types
==========

PageTypes are an important part of kiwi. On one hand they are responsible how the content manager can build the sitemap
of the website, on the other hand PageTypes provides information like routing or which controller and action should be
dispatched. Moreover they act as a container around FormElements and provides a content manager a form with information
about a given page (like the actual page content or meta information like a publish date).

Per default PageType configurations are located under ``module/application/config/page_types``

An Example configuration:

.. code-block:: php

    [
        'name'          => '', // internal name of the pageType
        'label'         => '', // label of the pageType (will be displayed in the admin interface)
        'handle'        => '', // a pageType handle
        'class'         => '', // the pageType class
        'view'          => '', // the view which should be rendered
        'root'          => false, //true | false | null ... weather the pageType can be used as Root PageType
        'allowedChildren' => [], // array or null ... a list of pageTypes which are allowed as direct children of the pageType
        'allowedParents'=> [], // array or null ... a list of pageTypes which are allowed as direct parents of the pageType
        'properties'    => [], // some pageTypes might need some extra configurations
        'controller'    => '', // controller which will be dispatched
        'action'        => '', // action which will be dispatched
        'terminal'      => true, // weather it is allowed to append child pages
        'sorting'       => true, // weather it is allowed to sort this page
        'sections'      => [
            [
                'label' => 'general',
                'elements' => [
                    //See FormElements for more Information
                ],
            ],
        ],
        'defaults'      => [
            //See FormElements for more Information
        ],
    ]

