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
        'label' => '', //optional - but should be not empty
        'value' => '', //optional
        'required' => true, // optional, default: false
        'description' => '', //optional
    ]

Text
~~~~

Renders a <input type="text"> Element

.. code-block:: php

    [
        'minLength' => 0, //optional default 0
        'maxLength' => 0, //optional default 524288
        'type' => 'text', //required
        // ...
    ]

Textarea
~~~~~~~~

Email
~~~~~

Checkbox
~~~~~~~~

Switcher
~~~~~~~~

Csrf
~~~~

Hidden
~~~~~~

Date
~~~~

DateTime
~~~~~~~~

Fieldset
~~~~~~~~

Link
~~~~

MultiCheckbox
~~~~~~~~~~~~~

Password
~~~~~~~~

Radio
~~~~~

Select
~~~~~~

Stack
~~~~~

Wysiwyg
~~~~~~~

YouTube
~~~~~~~

Media
~~~~~


PreConfigured Elements
----------------------

PreConfigured Elements are based on Base Elements but have already values and/or options pre configured

Country
~~~~~~~
Based on a Select Element - a DropDown with all Countries
