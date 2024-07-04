Reference
=========

Plugins
-------

A plugin requires an ``entry.lua`` file with a given name and
`record <https://www.lua.org/pil/3.6.html>`_.

``declare_plugin(name, props)``
*******************************

.. function:: declare_plugin(name, props)
    :param name: The name of the plugin. (string)
    :param props: Plugin properties (`table <#properties>`_)
    :returns: No return

    Declares a plugin and laods it into the DCS EDGE engine.

``plugin_done()``
***************

.. function:: plugin_done()
    :returns: No return

    Sets a flag informing the engine of a finished plugin declaration.

Properties
**********

.. tip::
    Table element names are case-sensitive, changing the sensitivity may result in undefined behaviour.

    You may also insert or alter any additional elements you want inside the table, so long as they
    don't interfere with those currently documented.

.. list-table::
    :header-rows: 1

    * - Name
      - Type
      - Description
      - Required?
    * - installed
      - boolean
      - Can the player can interact with the plugin? (e.g. settings, mission editor)
      - ✓
    * - dirName
      - string
      - The name of the directory containing the plugin.
      - ✓
    * - displayName
      - string
      - The name of the plugin shown within UI elements. (exc. module viewer)
      - ✓
    * - fileMenuName
      - string
      - The name of the file containing the flyable declaration.
      - ✓
    * - update_id
      - string
      - The ID to check for in DCS updates.
      - ✗
    * - state
      - string
      - String representing plugin accessibility state. ("installed" or "uninstalled")
      - ✓
    * - info
      - string
      - The description of the plugin, shown in the main menu.
      - ✓
    * - encyclopedia_path
      - string
      - File path pointing towards an ``Encyclopedia`` folder containing ``Plane/plugin_name.txt``.
      - ✗
    * - binaries
      - table of strings
      - Strings representing names of binary executable files (``.dll``) to inject.
      - ✗
    * - Skins
      - `table <#skins>`_
      - Defines the path and representation of UI elements.
      - ✗
    * - Missions
      - `table <#missions>`_
      - Defines the path and UI representation for flyable missions.
      - ✗
    * - LogBook
      - `table <#logbook>`_
      - Defines the path and UI representation for the pilot logbook.
      - ✗
    * - InputProfiles
      - table
      - Defines the path and UI representation for input profile bindings.
      - ✗
    * - Options
      - `table <#options>`_
      - Option properties
      - ✗

Skins
*****

.. hint::
    This is a nested table of (1), you are viewing the inner table.

.. list-table::
    :header-rows: 1

    * - Field
      - Type
      - Description
      - Required?
    * - name
      - string
      - The name of the plugin to show within most UI. [#1]_
      - ✓
    * - dir
      - string
      - The folder path of elements used.
      - ✓

Missions
********

.. hint::
    This is a nested table of (1), you are viewing the inner table.

.. list-table::
    :header-rows: 1

    * - Field
      - Type
      - Description
      - Required?
    * - name
      - string
      - The name of the plugin to show within most UI. [#1]_
      - ✓
    * - dir
      - string
      - The folder path of mission files used.
      - ✓
    * - CLSID
      - string
      - Customisable string text showing a class ID, e.g. ``{CLSID...CLSID}``.
      - ✗

LogBook
*******

.. hint::
    This is a nested table of (1), you are viewing the inner table.

.. list-table::
    :header-rows: 1

    * - Field
      - Type
      - Description
      - Required?
    * - name
      - string
      - The name of the plugin to show within most UI. [#1]_
      - ✓
    * - type
      - string
      - The plugin type. [#2]_
      - ✓

Options
*******

.. list-table::
    :header-rows: 1

    * - Field
      - Type
      - Description
      - Required?
    * - name
      - string
      - The name of the plugin to show within most UI. [#1]_
      - ✓
    * - nameId
      - string
      - The ID of the plugin used for options.
      - ✓
    * - dir
      - string
      - The folder path of option settings used.
      - ✓
    * - CLSID
      - string
      - Customisable string text showing a class ID, e.g. ``"{" .. type_id .. " options}"``.
      - ✗

.. [#1] UI known includes: special settings, main menu and the mission editor.
.. [#2] Plugins are loaded and internally referenced by a "type" ID.