``avLuaDevice``
===============

.. seealso::
    If you're looking to implement a common system, such as
    :doc:`animation & movement of a landing gear <lua.api.landing_gear_system>`,
    please check :doc:`our guides <guide>`.

Represents a builtin device written in Lua, often used for cockpit avionics.

This file may contain any code you want, and will be executed with the appropriate
DCS Lua API functions exposed:

Hooks
-----

.. function:: SetCommand(input_id, number)

    Called whenever an input binding has been detected.

    :param input_id: The ID of the input, e.g. ``Joystick.CmsDown``.
    :type input_id: integer
    :param number: The current value of the input.
    :type number: integer

.. function:: CockpitEvent(name, value)

    Called whenever an in-game event has been detected:

    - GroundPowerOn
    - GroundPowerOff
    - GroundAirOff
    - GroundAirOn
    - WeaponRearmFirstStep
    - WeaponRearmComplete
    - WeaponRearmSingleStepComplete
    - UnlimitedWeaponStationRestore
    - WheelChocksOn
    - WheelChocksOff

    :param name: The name of the event.
    :type name: string
    :param value: The value associated with the event.
    :type value: any (implicit)

.. function:: GetSelf()

    Constructs an innermost table of the device specified in ``device_init.lua``.

    :returns: A table containing functions and data for the device.
    :rtype: `Device table <#device>`_

.. function:: post_initialize()

    Called upon starting a DCS mission.

.. function:: update()

    Called on an interval set by :func:`make_default_activity`.

----

.. function:: make_default_activity(seconds)

    Sets the callsite execution interval for the script. The recommended value is ``0.01``,
    or 1/10th a millisecond.

    :param seconds: The amount of time in-between intervals.
    :type seconds: integer
    :returns: nil (implicit)

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

.. function:: get_cockpit_draw_argument_value(number)

    Gets the current value of an animation argument for the interior :term:`EDM`.

    :param number: The number of the animation argument.
    :type number: integer
    :returns: The associated value.
    :rtype: integer

----

.. function:: show_param_handles_list(show_imgui)

    Toggles an :term:`ImGui` widget window on and off in-game.

    :param show_imgui: Should ImGui be shown in-game?
    :type show_imgui: boolean
    :returns: ?

.. function:: dispatch_action(device_id, input_id, value)

    Triggers an involuntary input with a desired value. Similar to
    :func:`performClickableAction`, this will only result in a
    :func:`SetCommand` call.

    :param device_id: The ID of the device to use.
    :type device_id: string
    :param input_id: The ID of the input to use.
    :type input_id: integer
    :param value: The value to trigger the device input with.
    :type value: integer
    :returns: nil (implicit)

----

.. function:: get_base_data()

    Gets sensor data all over the aircraft from in-game.

    :returns: A table with functions for different sensor values.
    :rtype: `BaseData table <#base-data>`_

BaseData
********

.. function:: getAngleOfAttack()

    Gets the current angle of attack.

    :rtype: integer

.. function:: getAngleOfSlide()

    Gets the current angle of slide.

    :rtype: integer

.. function:: getBarometricAltitude()

    Gets the current altitude in barometric unit.

    :rtype: integer

.. function:: getCanopyPos()

    Gets the current position of the canopy.

    :rtype: integer

.. function:: getCanopyState()

    Gets the current state of the canopy, e.g. damaged, open, closed.

    :rtype: integer (???)

.. function:: getEngineLeftFuelConsumption()

    Gets the current fuel consumption rate of the left engine.

    :rtype: integer

.. function:: getEngineLeftRPM()

    Gets the current RPM percentage of the left engine.

    :rtype: integer

.. function:: getEngineLeftTemperatureBeforeTurbine()

    Gets the current temperature of the left engine (in Celsius) before
    statrtup.

    :rtype: integer

.. function:: getEngineRightFuelConsumption()

    Gets the current fuel consumption rate of the right engine.

    :rtype: integer

.. function:: getEngineRightRPM()

    Gets the current RPM percentage of the right engine.

    :rtype: integer

.. function:: getEngineRightTemperatureBeforeTurbine()

    Gets the current temperature of the right engine (in Celsius) before
    statrtup.

    :rtype: integer

----

.. function:: get_param_handle(name)

    Gets the name of a defined :doc:`parameter <lua.api.parameter>` with a handler.

    :param name: The name of the parameter.
    :type name: string
    :returns: A table with functions and data for handling.
    :rtype: `Handler table <#handler>`_

Handler
*******

Handlers are a special DCS construct made for controlling the state
of parameters when conditions [#1]_ are present.

.. function:: set(number)

    Sets the value of the parameter.

    :param number: The value to set.
    :type number: integer
    :returns: nil (implicit)

.. function:: get()

    Gets the current parameter value.

    :rtype: integer

Device
------

A "device" in this context is the state of a process within a plugin.
This includes the ability to add additional Lua table elements, as well
as add event hooks with functions.

.. function:: listen_command(input_id)

    Checks and calls :func:`SetCommand` when a specified
    :doc:`input profile <lua.input>` binding has been detected.

    :param input_id: The ID of the input, e.g. ``Keys.PlaneGearDown``.
    :type input_id: integer
    :returns: nil (implicit)

.. function:: listen_event(name)

    Checks and calls :func:`CockpitEvent` when an event has been detected.

    :param name: The name of the event.
    :type name: string
    :returns: nil (implicit)

----

.. function:: performClickableAction(input_id, value, ???)

    Triggers an involuntary input with a desire value. This will lead to
    :func:`SetCommand` and/or :func:`CockpitEvent` called.

    (Not to be confused with :func:`dispatch_action`)

    :param input_id: The ID of the input to use.
    :type input_id: integer
    :param value: The value associated with the input.
    :type value: integer
    :param ???:
    :type ???: boolean

.. [#1] Calling ``update()`` with ``if``, ``for`` and ``while`` expressions present.