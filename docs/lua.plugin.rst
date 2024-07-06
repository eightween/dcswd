Plugins
=======

.. function:: mount_vfs_texture_path(fp)

  Loads a filepath to use for plugin textures with :term:`VFS`.

  :param fp: The file path.
  :type fp: string
  :returns: nil (implicit)

.. function:: mount_vfs_model_path(fp)

  Loads a filepath to use for plugin :term:`EDM` files with :term:`VFS`.

  :param fp: The file path.
  :type fp: string
  :returns: nil (implicit)

.. function:: mount_vfs_liveries_path(fp)

  Loads a filepath to use for flyable plugin liveries with :term:`VFS`.

  :param fp: The file path.
  :type fp: string
  :returns: nil (implicit)

.. function:: mount_vfs_sound_path(fp)

  Loads a filepath to use for plugin sounds with :term:`VFS`.

  :param fp: The file path.
  :type fp: string
  :returns: nil (implicit)

.. function:: plugin_done()

  Sets a flag informing the engine of a finished plugin declaration.

  :returns: nil (implicit)

.. function:: declare_plugin(name, props)

  Declares a plugin and loads it into :term:`EDGE`.
  
  :param name: The name of the plugin.
  :type name: string
  :param props: Plugin properties
  :type props: `Properties table <#properties>`_
  :returns: nil (implicit)

Tables
------

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
    - `Skins table <#skins>`_
    - Defines the path and representation of UI elements.
    - ✗
  * - Missions
    - `Missions table <#missions>`_
    - Defines the path and UI representation for flyable missions.
    - ✗
  * - LogBook
    - `LogBook table <#logbook>`_
    - Defines the path and UI representation for the pilot logbook.
    - ✗
  * - InputProfiles
    - `InputProfiles table <#inputprofiles>`_
    - Defines the path and UI representation for input profile bindings.
    - ✗
  * - Options
    - `Options table <#options>`_
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
    - The name of the plugin to show within most UI.
    - ✓
  * - dir
    - string
    - The folder path of elements used.
    - ✓

.. collapse:: Example

  .. code-block:: lua

    {
      {
        name = "plugin",
        dir = "Skins/",
      },
    }

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
    - The name of the plugin to show within most UI.
    - ✓
  * - dir
    - string
    - The folder path of mission files used.
    - ✓
  * - CLSID
    - string
    - Customisable string text showing a class ID, e.g. ``{CLSID...CLSID}``.
    - ✗

.. collapse:: Example

  .. code-block:: lua

    {
      {
        name = "plugin",
        dir = "Missions/",
        CLSID = "{CLSID01124567890CLSID}",
      },
    }

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
    - The name of the plugin to show within most UI.
    - ✓
  * - type
    - string
    - The plugin type.
    - ✓

.. collapse:: Example

  .. code-block:: lua

    {
      {
        name = "plugin",
        type = type_id,
      },
    }

InputProfiles
*************

.. code-block:: lua

  {
    [type_id] = "InputProfiles",
  }

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
    - The name of the plugin to show within most UI.
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

.. collapse:: Example

  .. code-block:: lua

    {
      {
        name = "plugin",
        nameId = type_id,
        dir = "Options/",
        CLSID = "{plugin options}",
      },
    }

Constants
---------

``LockOn_Options``
******************

Represents a table provides variables that describe different states in the game.

.. list-table::
  :header-rows: 1

  * - Field
    - Type
    - Description
    - Required?
  * - 
    - 
    - 
    -