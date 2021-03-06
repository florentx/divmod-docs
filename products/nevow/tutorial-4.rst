======================
Nevow Tutorial: part 4
======================


Using the ``children`` class attribute
========================================


.. code-block:: python

    ######################################################################
    # Run using 'twistd -noy file.tac', then point your browser to
    # http://localhost:8080
    # A very simple Nevow site.
    ######################################################################

    from twisted.application import service, internet

    from nevow               import appserver
    from nevow               import rend
    from nevow               import loaders
    from nevow               import tags as T

    class SubPage ( rend.Page ):
        docFactory = loaders.stan (
            T.html [ T.head ( title = 'Sub Page' ),
                     T.body [ T.h1 [ 'This is a Sub Page' ],
                              T.p [ 'I lack much of interest.' ],
                              T.p [ 'You might find ',
                                    T.a ( href = '/' ) [ 'this' ],
                                    ' more interesting' ],
                              ]
                     ]
            )

    class MainPage ( rend.Page ):
        docFactory = loaders.stan (
            T.html [ T.head ( title = 'Main Page' ),
                     T.body [ T.h1 [ 'This is the Main Page' ],
                              T.p [ 'Try going to the pages ',
                                    T.a ( href = 'foo' ) [ 'foo' ],
                                    ' or ',
                                    T.a ( href = 'bar' ) [ 'bar' ],
                                    ],
                              T.p [ 'Don't try going ',
                                    T.a ( href = 'baz' ) [ 'here' ],
                                    ' as it doesn't exist.'
                                    ]
                              ]
                     ]
            )

        children = {
            'foo' : SubPage(),
            'bar' : SubPage()
            }

    ######################################################################
    # Nevow Boilerplate
    ######################################################################

    application = service.Application ( 'nevowdemo' )
    port        = 8080
    res         = MainPage()
    site        = appserver.NevowSite ( res )
    webService  = internet.TCPServer ( port, site )
    webService.setServiceParent ( application )


Note the following:

  * Instead of a ``childFactory()`` method we have an explicit mapping of child
    path elements to page objects;
  * Two independent child pages, ``foo`` and ``bar`` have been created. These
    are persisted in the dictionary; they are not created on demand;
  * An attempt to visit a child page that doesn't have an entry in the
    ``children`` dictionary will fail.

Of course, **any** page can have children, not just the main page. Try modifying
the example above to add another page below the ``SubPage`` objects.

Continue on to :doc:`tutorial-five`.

.. todo:: I suppose this is 'tutorial-four', we miss all the others!
