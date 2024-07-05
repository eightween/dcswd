.. dcs-api-docs documentation master file, created by
   sphinx-quickstart on Thu Jul  4 16:04:03 2024.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

DCSWD
=====

.. warning::
   This documentation is currently work-in-progress. If you find any issues or problems,
   please help out by `supporting the project`_.

Welcome to the unofficial :term:`DCS` World API Docs, (DCSWD) designed with a main focus to
document unknown globals, constants and functions written for :term:`plugins <Plugin>`.

**This is not a replacement** for :term:`BGDAM`, and is instead a continuation of
:term:`BGSC`. The DCS Lua API is categorically split into three: all Lua code, including
API-styled references for aircraft systems scripting, and a reference for plugin scripting.

Building from source
--------------------

1. Clone the latest documentation, found on GitHub:

.. code-block:: bash

   $ git clone --recursive https://github.com/filiastra/dcs-api-docs.git

2. Install the required dependencies:

.. code-block:: bash

   $ pip install -r requirements.txt 
   
3. Enter from root and test build the documentation:

.. code-block:: bash
   
   $ cd docs/ && make html

Table of Contents
-----------------

.. toctree::
   :maxdepth: 2

   lua
   guide
   glossary

Search
------

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

.. _supporting the project: https://github.com/filiastra/dcs-api-docs