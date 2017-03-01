Configuration
=============

Configurations can be shipped inside a module and/or can be set/overwritten inside the ``config/autoload/``
directory by adding files with an ``config.php`` file ending. Static or default configurations should be shipped
inside the module directory, environment based configurations (for production server, staging, development etc.)
should be inside the ``config/autoload/`` directory.

Occasionally you need to set configurations only for the administration panel of kiwi42 (for example extending the
navigation inside the administration panel). Therefor you can add an admin directory in you module config or in your
``config/autoload/`` directory. All configuration files inside this admin directory will be only loaded, when the
administration panel is requested.

Environment based configurations should be located in ``config/autoload/`` and prefixed with ``local.``
(like ``local.mail.config.php``). They will be merged on top of all other available configurations. ``local*`` files
will be git ignored by default.


After a basic setup with fruit console there should be some separated configuration files (assets, database, ...)
but they may be combined into a single ``local.config.php`` as well.

Current configuration values can be inspected by using fruit console. For example to see which assets
folders are registered within modules and will be symlinked/copied run the following on your command line::

$ bin/fruit config assets

Configuration values and options will be explained in detail where they are relevant within this documentation.
Some basic configurations below.

Database Config
---------------

.. code-block:: php

    [
        'db' => [
            'adapters' => [
                'Db\Master' => [
                    'database' => 'your_database',
                    'username' => 'root',
                    'password' => '',
                    'hostname' => '127.0.0.1',
                ]
            ]
        ]
    ]


Mail Config
-----------

Null Mailer (default):

.. code-block:: php

    [
        'mail' => [
             'transport' => [
                'type' => 'null',
                'options' => [],
            ],
        ],
    ]

Over SMTP

.. code-block:: php

    [
        'mail' => [
            'transport' => [
                'type' => 'smtp',
                'options' => [
                    'host'              => '', //optional, default: localhost
                    'port'              => 25, //optional, default: 25
                    'encryption'        => '', //optional (ssl|tls), default: tls
                    'username'          => '', //optional
                    'password'          => '', //optional

                ],
            ],
        ],
    ]

Over Sendmail

.. code-block:: php

    [
        'mail' => [
            'transport' => [
                'type' => 'sendmail',
                'options' => [
                    'command'           => '', //optional, default: /usr/sbin/sendmail -bs
                ],
            ],
        ],
    ]

Over PHP Mail

.. code-block:: php

    [
        'mail' => [
            'transport' => [
                'type' => 'mail',
                'options' => [
                    'extra'             => '', //optional, default: -f%s
                ],
            ],
        ],
    ]


CSP Protection Config
---------------------

You can enable/disable the content security policy headers.

.. code-block:: php

    [
       'security' => [
            'csp' => [
                'enable'        => false,
                'nonce'         => false,
                'connect_src'   => false,
                'font_src'      => false,
                'img_src'       => false,
                'media_src'     => false,
                'object_src'    => false,
                'script_src'    => false,
                'style_src'     => false,
                'default_src'   => false,
                'form_action'   => false,
                'form_ancestors'=> false,
                'plugin_types'  => false,
                'child_src'     => false,
            ],
        ],
    ]

I18n Config
-----------

Definition which locales/languages are available in your frontend

.. code-block:: php

    [
       'i18n' => [
            'type' => 'language' // can be language or region
            'locales' => [
                'de-AT' => [
                    'default' => true
                ],
                'en-US' => [
                    'default' => false
                ],
            ]
        ]
    ]

Session Config
--------------

.. code-block:: php

    [
       'session_config' => [
            'name' => 'kiwi42',
            'use_trans_sid' => false,
            'use_cookies' => true,
            'use_only_cookies' => true,
            'cookie_httponly' => true,
        ]
    ]

Admin Config
------------

.. code-block:: php

    [
       'admin' => [
            'timezone' => 'Europe/Vienna',
            'locale' => 'en-US',
            'assets' => [],
            'login_captcha' => false,
            'login_captcha_options' => [ //your google reCaptcha credentials
                'sitekey' => '',
                'secret' => '',
            ]
        ]
    ]

Project Config
--------------

Some basic information about your application (mainly used for email sending

.. code-block:: php

    [
       'project' => [
            'name' => 'kiwi42',
            'email_subject_prefix' => '[kiwi42]: ',
            'email_from' => 'noreply@kiwi42.com',
            'project_base_url' => 'http://kiwi42.com',
        ]
    ]
