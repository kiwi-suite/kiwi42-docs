Form Elements
=============

Building forms are a very basic part of kiwi. Outside of the "admin" Environment is the standard Zend Framework Form
available. Inside the "admin" Environment is a modified version of the Zend Form in use. It still strongly depends on
the Zend Form, but it has a slightly different way of defining forms and has it own view helpers (do work better
together with angular).

This documentation only covers form building inside the administration interface of kiwi. If you need a form outside
of the interface you can choose the technology you want (eg. Zend Form, Zend Inputfilter without Form, any other
techique).

Base Elements
-------------

FormElements are definied in an simple Array-Syntax. Here a basic syntax of the definition (some FormElements
might have extra configuration parameters which is covered later):

.. code-block:: php

    [
        'name' => '', //required
        'type' => '', //required
        'label' => '', //optional - but should be not empty - will run through the internal translator
        'value' => '', //optional
        'required' => true, // optional, default: false
        'description' => '', //optional
    ]

Text
~~~~

Renders a ``<input type="text">`` element with an attached strlen validator

.. code-block:: php

    [
        'type' => 'text', //required
        'minLength' => 0, //optional, default 0
        'maxLength' => 0, //optional, default 524288
        // ...
    ]

Textarea
~~~~~~~~

Renders a ``<textarea>`` element with an attached strlen validator

.. code-block:: php

    [
        'type' => 'textarea', //required
        'minLength' => 0, //optional, default 0
        'maxLength' => 0, //optional, default PHP_MAX_INT
        'rows' => 0, //optional, default 5
        // ...
    ]

Email
~~~~~
Renders a ``<input type="text">`` element with an attached email validator

.. code-block:: php

    [
        'type' => 'email', //required
        // ...
    ]

Checkbox
~~~~~~~~

Renders a single ``<input type="checkbox">`` element

.. code-block:: php

    [
        'type' => 'checkbox', //required
        'checkedValue' => '', //optional, default string 'true'
        'uncheckedValue' => '', //optional, default string 'false'
        // ...
    ]

Switcher
~~~~~~~~
Switcher is a visual component (an On/Off-Switch). Internally in works like the checkbox element.

.. code-block:: php

    [
        'type' => 'switcher', //required
        'checkedValue' => '', //optional, default string 'true'
        'uncheckedValue' => '', //optional, default string 'false'
        // ...
    ]

Csrf
~~~~
The Csrf element helps to provide protection from CSRF attacks on forms, ensuring the data is submitted by the
session that generated the form. This is achieved by adding a hash value to the form data. For security reason
this element should be used in every form.

.. code-block:: php

    [
        'type' => 'csrf', //required
        'csrfOptions' => [
            'salt' => '', //optional
            'timeout' => 0, //optional, default 300 seconds
        ],
        // ...
    ]

Hidden
~~~~~~
Renders a ``<input type="hidden">`` element

.. code-block:: php

    [
        'type' => 'hidden', //required
        // ...
    ]

Date
~~~~
This generates a date picker element with an attached date validator

.. code-block:: php

    [
        'type' => 'date', //required
        // ...
    ]

DateTime
~~~~~~~~
This generates a date and time picker element with an attached date time validator

.. code-block:: php

    [
        'type' => 'dateTime', //required
        // ...
    ]

Fieldset
~~~~~~~~

Link
~~~~

MultiCheckbox
~~~~~~~~~~~~~

Renders a one or more ``<input type="checkbox">`` elements  with an attached inArray validator

.. code-block:: php

    [
        'type' => 'multiCheckbox', //required
        'values' => [
            // key => label - label will run through the internal translator
        ], //required
        // ...
    ]

Password
~~~~~~~~
Renders a ``<input type="password">`` element

.. code-block:: php

    [
        'type' => 'password', //required
        // ...
    ]

Radio
~~~~~
Renders a one or more ``<input type="radio">`` elements with an attached inArray validator

.. code-block:: php

    [
        'type' => 'radio', //required
        'values' => [
            // key => label - label will run through the internal translator
        ], //required
        // ...
    ]

Select
~~~~~~
Renders a ``<select>`` element  with an attached inArray validator

.. code-block:: php

    [
        'type' => 'select', //required
        'values' => [
            // key => label - label will run through the internal translator
        ], //required
        'emptyValue' => [
            // key => label - label will run through the internal translator
        ], //required
        // ...
    ]

Stack
~~~~~

Wysiwyg
~~~~~~~
Renders a ``tinymce`` wysiwyg editor

.. code-block:: php

    [
        'type' => 'wysiwyg', //required
        'editorOptions' => [] //optional => you can pass tinymce editor options as array
        // ...
    ]

YouTube
~~~~~~~
The YouTube Element provides the functionality to parse youtube links and storing the youtube id

.. code-block:: php

    [
        'type' => 'youtube', //required
        // ...
    ]

Media
~~~~~
Through the media element media files can be selected/uploaded.

.. code-block:: php

    [
        'type' => 'media', //required
        'categorySelection' => '', //optional - select only from given category, default: *
        'typeSelection' => '' //optional - select only given type. possible values are *, images or pdf. default: *
        // ...
    ]

PreConfigured Elements
----------------------

PreConfigured Elements are based on Base Elements but have already values and/or options pre configured

Country
~~~~~~~
Based on a Select Element - a DropDown with all Countries

.. code-block:: php

    [
        'type' => 'country', //required
        // ...
    ]

This element is an shortcut of:

.. code-block:: php

    [
        'type' => 'select',
        'values' => [
            'AF' => 'Afghanistan',
            //...
            'AT' => 'Austria',
            //...
            'ZW' => 'Zimbabwe',

        ],
    ]

Online
~~~~~~
Short version of an online/offline switcher

.. code-block:: php

    [
        'type' => 'online', //required
        // ...
    ]

This element is an shortcut of:

.. code-block:: php

    [
        'type' => 'switcher',
        'checkedValue' => 'online',
        'uncheckedValue' => 'offline',
    ]


Image
~~~~~
Through the image element images can be selected/uploaded.

.. code-block:: php

    [
        'type' => 'image', //required
        'categorySelection' => '', //optional - select only from given category, default: *
        // ...
    ]

This element is an shortcut of:

.. code-block:: php

    [
        'type' => 'media',
        'typeSelection' => 'images',
    ]

