Getting started
===============

.. note::
    Some of the contents are from :term:`BGSC`. This page is incomplete.

Setting up
----------

.. attention::
    This is a quickstart written for developers creating a new flyable
    :term:`plugin <Plugin>` from scratch. If you are modifying a flyable plugin,
    see :doc:`lua.plugin`.

A flyable plugin consists of multiple directories for various aspects, such as
the cockpit, settings, (options) liveries, textures & 3D models. DCSWD comes with
a template repository which can be cloned via. git:

.. code-block:: bash

    $ git clone --recursive https://github.com/filiastra/dcswd-template

Modifying files
---------------

``entry.lua``
*************

A plugin requires to be loaded directly into :term:`EDGE` in order be functionally
present in-game. We can achieve this by creating an entry:

.. code-block:: lua
    :linenos:
    :emphasize-lines: 2, 5, 15, 27, 30
    
    -- This isn't necessary, but it may be useful for future states.
    local State = { enabled = 'installed', disabled = 'uninstalled' }

    --- Represents the base plugin information we want.
    local plugin = {
        name = 'Plugin name',
        type = 'PluginName',
        version = '0.1.0',
        description = 'This plugin is currently under development.',
    }

    --- Defines the properties for defining a plugin.
    -- The bulk of declaring a plugin comes down to metadata and
    -- file path information.
    local DeclarePluginProperties = {
        dirName = current_mod_path,
        displayName = _(plugin.name),
        fileMenuName = _(plugin.name),
        installed = true,
        state = State.enabled,
        update_id = plugin.name,
        version = plugin.version,
        info = plugin.description,
    }

    --- Directly loads the plugin information established into EDGE.
    declare_plugin(plugin.type, DeclarePluginProperties)

    -- Signalling we're done with plugin entry.
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