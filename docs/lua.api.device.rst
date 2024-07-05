``avLuaDevice``
===============

.. seealso::
    If you're looking to implement a common system, such as
    :doc:`animation & movement of a landing gear <lua.api.landing_gear_system>`,
    please check :doc:`our guides <guide>`.

Represents a builtin device written in Lua, often used for cockpit avionics.

This file may contain any code you want, and will be executed with the appropriate
DCS Lua API functions exposed:

.. function:: get_draw_aircraft_argument_value(number)
    
    Gets the current value of an animation argument from the exterior :term:`EDM`.

    :param number: The number of the animation argument.
    :type number: integer
    :returns: The associated value.
    :rtype: integer

.. function:: set_draw_aircraft_argument_value(number)

    Sets a value to the specified animation argument for the exterior :term:`EDM`.

    :param number: The value to set.
    :returns: nil (implicit)

.. function:: show_param_handles_list(show_imgui)

    Toggles an :term:`ImGui` widget window on and off in-game.

    :param show_imgui: Should ImGui be shown in-game?
    :type show_imgui: boolean
    :returns: ?

.. function:: get_param_handle(name)

    Gets the name of a defined :doc:`parameter <lua.api.parameter>` with a handler.

    :param name: The name of the parameter.
    :type name: string
    :returns: A table with functions and data for handling.
    :rtype: `Handler table <#handler>`_

.. function:: GetSelf()

    Constructs an innermost table of data with special builtin functions.

    :returns: A table containing functions and data for the device.
    :rtype: `Device table <#device>`_

Handler
-------

Handlers are a special DCS construct made for controlling the state
of parameters when conditions [#1]_ are present.

.. class:: Handler

    .. method:: set(number)

        Sets the value of the parameter.

        :param number: The value to set.
        :type number: integer
        :returns: nil (implicit)

    .. method:: get()

        Gets the current parameter value.

        :rtype: integer

Device
------

A "device" in this context is the state of a process within a plugin.
This includes the ability to add additional Lua table elements, as well
as add event hooks with functions.

.. function:: listen_command(input_id)

    Checks and calls when a specified :doc:`input profile <lua.input>` binding
    has been detected.

    :param key_id: The ID of the input, e.g. ``Keys.PlaneGearDown``.
    :type key_id: integer
    :returns: nil (implicit)

.. [#1] Calling ``update()`` with ``if``, ``for`` and ``while`` expressions present.