==================================================================
 `Agoraplex Sphinx Theme <https://github.com/agoraplex/themes>`__
==================================================================

About
=====

This repository contains `Sphinx`_ themes for `Agoraplex`_ projects,
based on the `Pylons Sphinx Themes`_, and some helper roles. The
following themes exist:

- **agoraplex** - the generic `Agoraplex`_ documentation theme

.. _Sphinx: http://sphinx-doc.org/
.. _Agoraplex: http://agoraplex.github.com/
.. _Pylons Sphinx Themes: https://github.com/Pylons/pylons_sphinx_theme


Requirements
------------

- `Sphinx`_ 1.1 or newer

To rebuild the graphics from the SVG originals (which requires cloning
the `github repository <https://github.com/agoraplex/themes>`__):

- ``rsvg-convert`` from `librsvg`_

- ``pngtopam``, ``pnmremap``, ``pnmcolormap``, and ``pnmtopng`` from
  `Netpbm`_

- ``icotool`` from `icoutils`_

.. _librsvg: http://live.gnome.org/LibRsvg
.. _Netpbm: http://netpbm.sourceforge.net/
.. _icoutils: http://www.nongnu.org/icoutils/


Installation
------------

To use a theme in your Sphinx documentation, follow this guide:

1. Install the package::

    $ pip install agoraplex.themes.sphinx

2. Edit your ``conf.py`` doc configuration file to point to the
   `agoraplex` theme::

       import agoraplex.themes.sphinx

       # ...

       html_theme = 'agoraplex'
       html_theme_path = agoraplex.themes.sphinx.get_html_theme_path()


Helpers
-------

This package adds several Sphinx helper roles (in ``roles.py``). To
use these, add ``agoraplex.themes.sphinx.roles`` to the ``extensions``
list in your ``conf.py``.

The roles are:

- ``github``: link to a github_ project::

    :github:`agoraplex/themes`

  The ``github_url`` configuration directive defaults to
  ``https://github.com/``.

- ``pypi``: link to a project record at `PyPi, the Python Package
  Index <http://pypi.python.org/>`__::

    :pypi:`agoraplex.themes.sphinx`

  The ``pypi_url`` configuration directive defaults to
  ``http://pypi.python.org/pypi/``

- ``wikipedia``: link to a `Wikipedia`_ article::

    :wikipedia:`Ancient Agora of Athens`

  The ``wikipedia_url`` and ``wikipedia_lang`` configuration
  directives default to ``http://%s.wikipedia.org/wiki/`` and
  ``en``, respectively. Note that the ``wikipedia_url`` directive
  **must** contain a ``%s``, where the role will insert the
  ``wikipedia_lang`` value.

  The ``wikipedia`` role will (mostly) canonicalize an article
  name by replacing spaces with underscores (``_``), uppercasing
  the first letter of the name, and lowercasing the
  rest. Wikipedia's own URL rewriting is tolerant of case
  mismatch, so these simplistic rules work well enough.

.. _github: https://github.com/
.. _Wikipedia: http://wikipedia.org/


Configuration
-------------

In addition to the role-related configuration directives, this theme
adds the following directives to the set defined by the original
Pylons theme:

- ``fontsets``: a space-separated list of directory names, relative to
  the `font directory`_ (``_static/fonts``), from which to load a
  ``stylesheet.css`` file containing ``@font-face`` directives.

- ``font_body``, ``font_header``: the 'base' names of the fonts to use
  for body and header text, respectively.

.. note::

   The stylesheets assume that the font family is actually named
   ``<fontname>Regular``. So, to use `NeutonRegular` as the header
   font (which is the default), ``theme.conf`` would specify
   ``font_header=Neuton``.

.. _font directory: https://github.com/agoraplex/themes/blob/master/sphinx/agoraplex/static/fonts
