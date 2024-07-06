Getting started
===============

.. note::
    The contents of this page are from :term:`BGSC`.

Setting up the project
----------------------

.. note::
    This structure assumes you are developing a flyable plugin. For non-flyable, consider
    using the ``Mods/tech`` directory instead.

Plugins typically define a ``Scripts`` directory. The architecture of popular mods, such as the
`A-4E`_ contain a similar layout:

::

    ../DCS/Mods/aircraft/Name/
        Cockpit/Scripts/
        Options/
        Scripts/
        aircraft_name.lua
        entry.lua

Initialisation
--------------

A plugin is required to be loaded by the engine in order to execute properly or appear in-game.
This is done by adding an ``entry.lua`` file, which DCS will automatically check for all
subdirectories within ``Mods/aircraft``. A basic example includes:

.. code-block:: lua
    
    --- Defines the name for in-game module viewer.
    local self_id = "Mod"
    --- Defines the type stored internally within DCS.
    local type_id = "MOD_TYPE"
    --- Defines the current version shown on DCS UI.
    local VERSION = "0.1.0-dev"

    local DeclarePluginProperties =
    {
        installed       = true,
        dirName         = current_mod_path,
        displayName     = _(self_id),
        fileMenuName    = _(self_id),
        update_id       = self_id,
        version         = VERSION,
        state           = "installed",
        info            = _(self_id .. " description"),
    }

    -- global lua function directly loads as known module
    declare_plugin(type_id, DeclarePluginProperties)

    -- alerts engine that we're done loading
    plugin_done()

For more information on plugin definition, please check :doc:`lua.ref`.

Debugging
*********

DCS has two methods of debugging: using the ``dcs.log`` file found within your ``Saved Games`` path,
or using ``Export.lua`` from your ``DCS/Scripts`` path. For basic debugging of the entry process,
please consider using the log file.

Cockpit scripting
-----------------

:term:`EDGE` is capable of detecting connectors in an :term:`EDM`. These connectors can also be
interacted with, such as :doc:`lua.api.device` (e.g. :doc:`lua.api.landing_gear_system`) and/or
:doc:`lua.api.clickable`.

.. _Beginners Guide to Systems Coding: https://bgsc.rtfd.io/
.. _A-4E: https://github.com/heclak/community-a4e-c