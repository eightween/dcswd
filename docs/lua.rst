Lua
===

DCS World uses the embedded programming language, `Lua <https://www.lua.org/about.html>`_ 
for its `scripting engine <https://dcs.world/en/support/faq/1253/>`_.

Definitions
-----------

This section documents all currently known definitions and declarations related to
:term:`plugins <Plugin>`.

.. toctree::
   :maxdepth: 3

   lua.input
   lua.plugin

API Reference
-------------

This section covers all essential globals and functions from the DCS Lua API for coding
aircraft systems.

.. toctree::
   :maxdepth: 3

   lua.api.clickable
   lua.api.device
   lua.api.electric
   lua.api.weapon

There are additional examples included of common systems found in an aircraft:

.. toctree::
   :maxdepth: 2

   lua.api.landing_gear_system
   lua.api.parameter

.. _lua_logging:

Logging
-------

.. admonition:: Developer Notice

   There may be additional functions, but aren't confirmed.

Every Lua script within DCS has a global ``log`` variable.

.. function:: alert(string)

   Writes a tagged "ALERT" string to :term:`dcs.log`.