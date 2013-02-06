===============
Divmod PyFlakes
===============

PyFlakes a Lint-like tool for Python, like `PyChecker`_ or `PyLint`_. It is
focused on identifying common errors quickly without executing Python code.

Its primary advantage over PyChecker is that it is *fast*. You don't have to
sit around for minutes waiting for the checker to run; it runs on most large
projects in only a few seconds.

The two primary categories of defects reported by PyFlakes are:

* Names which are used but not defined or used before they are defined
* Names which are redefined without having been used

These can each take many forms. For example, PyFlakes will tell you when you
have forgotten an import, mistyped a variable name, defined two functions with
the same name, shadowed a variable from another scope, imported a module
twice, or two different modules with the same name, and so on.

Download
========

* `0.6.1 Release <http://pypi.python.org/packages/source/p/pyflakes/pyflakes-0.6.1.tar.gz#md5=00debd2280b962e915dfee552a675915>`_
  (`Release Notes <http://bazaar.launchpad.net/~pyflakes-dev/pyflakes/master/view/67/NEWS.txt>`_)
  or ``pip install pyflakes``
* Trunk: ``bzr branch lp:pyflakes``
  (`Browse <http://bazaar.launchpad.net/~pyflakes-dev/pyflakes/master/files>`_)

Exits
=====

* `PyFlakes on PyPI <http://pypi.python.org/pypi/pyflakes>`_
* `PyFlakes on Launchpad <https://launchpad.net/pyflakes>`_
* `PyFlakes on SWiK <http://www.swik.net/pyflakes>`_

.. _PyChecker: http://pychecker.sourceforge.net
.. _PyLint: http://pypi.python.org/pypi/pylint
