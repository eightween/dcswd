Getting started
===============

.. note::
    Some of the contents are from :term:`BGSC`.

Setting up
----------

.. attention::
    This is a quickstart written for developers creating a new flyable
    :term:`plugin <Plugin>` from scratch. If you are modifying a flyable plugin,
    see :doc:`lua.plugin`.

A flyable plugin consists of multiple directories for various aspects, such as
the cockpit, settings, (options) liveries, textures & 3D models. DCSWD comes with
a template repository which can be cloned via. git:

.. warning::
    This repository does not exist yet.

.. code-block:: bash

    $ git clone --recursive https://github.com/filiastra/dcswd-template

Modifying files
---------------

.. warning::
    This section assumes using the repository.

``entry.lua``
*************

A plugin requires to be loaded directly into :term:`EDGE` in order be functionally
present in-game. We can achieve this by creating an entry:

.. code-block:: lua
    :linenos:
    :emphasize-lines: 2, 4, 6, 9, 22, 25
    
    --- Defines the name for in-game module viewer.
    local self_id = "Mod"
    --- Defines the type stored internally within DCS.
    local type_id = "MOD_TYPE"
    --- Defines the current version shown on DCS UI.
    local VERSION = "0.1.0-dev"

    --- Defines the plugin's properties.
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

Debugging
*********

You can debug DCS by using :ref:`lua_logging` to write to :term:`dcs.log`.

Cockpit scripting
-----------------

:term:`EDGE` is capable of detecting connectors in an :term:`EDM`. These connectors can also be
interacted with, such as :doc:`lua.api.device` (e.g. :doc:`lua.api.landing_gear_system`) and/or
:doc:`lua.api.clickable`.

.. _A-4E: https://github.com/heclak/community-a4e-c