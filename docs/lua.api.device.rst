``avLuaDevice``
===============

Represents a builtin device written in Lua, often used for cockpit avionics.

Functions
---------

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

Implementation
--------------

.. seealso::
    If you're looking to implement a common system, such as
    :doc:`animation & movement of a landing gear <lua.api.landing_gear>`,
    please check :doc:`guide`.

This file may contain any code you want, and will be executed with the appropriate
DCS Lua API functions exposed.