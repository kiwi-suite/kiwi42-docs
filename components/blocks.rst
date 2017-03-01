Blocks
======

A block is an instance of a certain type of content that can be displayed in the page. Every block is specified by an
configuration and a html snippet.
Inside the specification you describe what a content editor of the website can/must enter for a certain block. Inside the
html snippet, you can access this information.

.. code-block:: php

    [
        'name'          => '', // internal name of the block
        'label'         => '', // label of the block (will be displayed in the admin interface)
        'elements' => [
            //See FormElements for more Information
        ],
]


