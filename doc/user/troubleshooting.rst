=================
 Troubleshooting
=================

If syntax checking does not work as expected there are a number of steps that
you can follow to isolate and maybe fix the problem.

.. _flycheck-common-issues:

Common issues
=============

First check whether your issue is one of the common setup issues and problems.

Flycheck can’t find any programs on macOS
-----------------------------------------



Verify your setup
=================

If your issue is none of the aforementioned :ref:`common issues
<flycheck-common-issues>` the first step is to let Flycheck check your setup:

.. define-key:: C-c ! v
                M-x flycheck-verify-setup

   Show a :term:`verification buffer` with information about your
   :mode:`flycheck` setup for the current buffer.

   The buffer contains all syntax checkers available for the current buffer and
   tells you whether Flycheck would use each one and what reasons would prevent
   Flycheck from using a checker.  It also includes information about your
   Flycheck and Emacs version and your operating system.

The following image shows a :term:`verification buffer`:

.. image:: /images/flycheck-verify-buffer.png

The buffer shows all syntax checkers for the current buffer.  Note that you can
click on the syntax checker names to show the docstring for a syntax checker.

* *Green* items indicate *good* configuration.  In the screenshot both
  `python-flake8` and `python-pycompile` exist.

* *Orange* items indicate a *potential* misconfiguration.  The screenshot shows
  that no configuration file was found for `python-flake8` which is perfectly
  fine if there’s no flake8 configuration file in the project, but not so good
  if you’d like Flycheck to use a configuration file for flake8.  The section
  :ref:`flycheck-checker-config-files` has more information about configuration
  files.

  Likewise the buffer warns you that a ``demo`` (which is not part of Flycheck
  of course) syntax checker isn’t registered in `flycheck-checkers`.  If you’d
  like Flycheck to automatically use the syntax checker you should fix this
  issue but otherwise it’s safe to ignore this warning.

* *Red* items indicate *bad* configuration.  `python-plaint` wan’t found in the
  screenshot.  You’ll not be able to use pylint in the current buffer.

Debug syntax checkers
=====================

.. todo:: Document C-c ! C-c, how to interpret the output and what to do if
          things fail

If all else fails…
==================

.. todo:: Tell users to open an issue
