.. dcs-api-docs documentation master file, created by
   sphinx-quickstart on Thu Jul  4 16:04:03 2024.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

.. admonition:: Developer Notice
   
   This documentation is currently work-in-progress. If you find any issues or problems,
   please help out by `supporting the project`_.

DCSWD
=====

Welcome to the unofficial :term:`DCS` World Lua API documentation, (DCSWD) primarily designed
to document unknown globals, constants and functions written for :term:`plugins <Plugin>`.

**This is not a replacement** for :term:`BGDAM`, instead a continuation of :term:`BGSC` on a
broader level. Information is tailored around learning how to write and implement custom Lua
scripts of your own to simulate systems of an aircraft, with all plugin definitions available
to you, including flyables.

Building from source
--------------------

1. Clone the latest documentation, found on GitHub:

.. code-block:: bash

   $ git clone --recursive https://github.com/filiastra/dcs-api-docs.git

2. Install the required dependencies:

.. code-block:: bash

   $ pip install -r requirements.txt 
   
3. Test build the documentation:

.. code-block:: bash
   
   $ cd docs/ && make html

Documentation
-------------

.. toctree::
   :maxdepth: 2

   quickstart
   lua
   guide
   glossary

Search
------

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

.. _supporting the project: https://github.com/filiastra/dcs-api-docs