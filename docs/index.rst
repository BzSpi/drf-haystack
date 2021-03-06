==================================
Haystack for Django REST Framework
==================================

Contents:

.. toctree::
   :maxdepth: 2

   basic_usage
   advanced_usage

=====
About
=====
Small library aiming to simplify using Haystack with Django REST Framework

Features
========

Supported Python versions:

    - Python 2.6
        - Django 1.5 and 1.6
    - Python 2.7, 3.3, 3.4 and 3.5
        - Django 1.5, 1.6, 1.7 and 1.8


Installation
============
It's in the cheese shop!

.. code-block:: none

    $ pip install drf-haystack


Requirements
============
    - Django
    - Django REST Framework
    - Haystack (and a supported search engine such as Solr, Elasticsearch, Whoosh, etc.)
    - Python bindings for the chosen backend (see below).
    - (geopy and libgeos if you want to use geo spatial filtering)

Python bindings
---------------

You will also need to install python bindings for the search engine you'll use.

Elasticsearch
.............

See haystack `Elasticsearch <https://django-haystack.readthedocs.org/en/v2.4.1/installing_search_engines.html#elasticsearch>`_
docs for details

.. warning::

    ``django-haystack`` does not yet support Elasticsearch v2 yet, so we need to use the latest
    1.x branch.

.. code-block:: none

    $ pip install elasticsearch<2.0.0

Solr
....

See haystack `Solr <https://django-haystack.readthedocs.org/en/v2.4.1/installing_search_engines.html#solr>`_
docs for details.

.. code-block:: none

    $ pip install pysolr

Whoosh
......

See haystack `Whoosh <https://django-haystack.readthedocs.org/en/v2.4.1/installing_search_engines.html#whoosh>`_
docs for details.

.. code-block:: none

    $ pip install whoosh

Xapian
......

See haystack `Xapian <https://django-haystack.readthedocs.org/en/v2.4.1/installing_search_engines.html#xapian>`_
docs for details.


Contributors
============

This library has mainly been written by `me <https://github.com/rhblind>`_ while working
at `Inonit <https://github.com/inonit>`_. I have also had some help by these amazing people!
Thanks guys!

    - `Jacob Rief <https://github.com/jrief>`_
    - `Jannon Frank <https://github.com/jannon>`_
    - `Michael Fladischer <https://github.com/fladi>`_ (Debian package)

Changelog
=========

v1.5.6
------
*Release date: 2015-12-02*

    - Fixed a bug where ``ignore_fields`` on ``HaystackSerializer`` did not work unless ``exclude`` evaluates
      to ``True``.
    - Removed ``elasticsearch`` from ``install_requires``. Elasticsearch should not be a mandatory requirement,
      since it's useless if not using Elasticsearch as backend.

v1.5.5
------
*Release date: 2015-10-31*

    - Added support for Django REST Framework 3.3.0 (Only for Python 2.7/Django 1.7 and above)
    - Locked elasticsearch < 2.0.0 (See :drf-issue:`29`)

v1.5.4
------
*Release date: 2015-10-08*

    - Added support for serializing faceted results. Closing :drf-issue:`27`.

v1.5.3
------
*Release date: 2015-10-05*

    - Added support for :ref:`faceting-label` (Github :drf-issue:`11`).

v1.5.2
------
*Release date: 2015-08-23*

    - Proper support for :ref:`multiple-search-indexes-label` (Github :drf-issue:`22`).
    - Experimental support for :ref:`term-boost-label` (This seems to have some issues upstreams,
      so unfortunately it does not really work as expected).
    - Support for negate in filters.

v1.5.1
------
*Release date: 2015-07-28*

    - Support for More Like This results (Github :drf-issue:`10`).
    - Deprecated ``SQHighlighterMixin`` in favor of ``HaystackHighlightFilter``.
    - ``HaystackGenericAPIView`` now returns 404 for detail views if more than one entry is found (Github :drf-issue:`19`).

v1.5.0
------
*Release date: 2015-06-29*

    - Added support for field lookups in queries, such as ``field__contains=foobar``.
      Check out `Haystack docs <http://django-haystack.readthedocs.org/en/latest/searchqueryset_api.html?highlight=field%20lookup#field-lookups>`_
      for details.
    - Added default ``permission_classes`` on ``HaystackGenericAPIView`` in order to avoid crash when
      using global permission classes on REST Framework. See :ref:`permission-classes-label` for details.

v1.4
----
*Release date: 2015-06-15*

    - Fixed issues for Geo spatial filtering on django-haystack v2.4.x with Elasticsearch.
    - A serializer class now accepts a list or tuple of ``ignore_field`` to bypass serialization.
    - Added support for Highlighting.

v1.3
----
*Release date: 2015-05-19*

    - ``HaystackGenericAPIView().get_object()`` now returns Http404 instead of an empty ``SearchQueryset``
      if no object is found. This mimics the behaviour from ``GenericAPIView().get_object()``.
    - Removed hard dependencies for ``geopy`` and ``libgeos`` (See Github :drf-issue:`5`). This means
      that if you want to use the ``HaystackGEOSpatialFilter``, you have to install these libraries
      manually.

v1.2
----
*Release date: 2015-03-23*

    - Fixed ``MissingDependency`` error when using another search backend than Elasticsearch.
    - Fixed converting distance to D object before filtering in HaystackGEOSpatialFilter.
    - Added Python 3 classifier.

v1.1
----
*Release date: 2015-02-16*

    - Full coverage (almost) test suite
    - Documentation
    - Beta release Development classifier

v1.0
----
*Release date: 2015-02-14*

    - Initial release.


Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

