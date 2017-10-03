<div class="ClassDoc YAMLDoc" id="joystick" markdown="1">

# class __joystick__

If you insert the JOYSTICK plugin at the start of your experiment, a
JOYSTICK object automatically becomes part of the experiment object
and can be used within an inline_script item as JOYSTICK.

%--
constant:
        arg_joybuttonlist: |
                A list of buttons that are accepted or `None` to accept all
                buttons.
        arg_timeout: |
                A timeout value in milliseconds or `None` for no timeout.
--%

[TOC]

<div class="FunctionDoc YAMLDoc" id="joystick-__init__" markdown="1">

## function __joystick\.\_\_init\_\___\(experiment, device=0, joybuttonlist=None, timeout=None\)

Intializes the joystick object.

__Arguments:__

- `experiment` -- An Opensesame experiment.
	- Type: experiment

__Keywords:__

- `device` -- The joystick device number.
	- Type: int
	- Default: 0
- `joybuttonlist` -- %arg_joybuttonlist
	- Type: list, NoneType
	- Default: None
- `timeout` -- %arg_timeout
	- Type: int, float, NoneType
	- Default: None

</div>

<div class="FunctionDoc YAMLDoc" id="joystick-flush" markdown="1">

## function __joystick\.flush__\(\)

Clears all pending input, not limited to the joystick.

__Returns:__

True if joyinput was pending (i.e., if there was something to flush) and False otherwise.

- Type: bool

</div>

<div class="FunctionDoc YAMLDoc" id="joystick-get_joyaxes" markdown="1">

## function __joystick\.get\_joyaxes__\(timeout=None\)

Waits for joystick axes movement.

__Keywords:__

- `timeout` -- A timeout value in milliseconds or `None` to use default timeout.
	- Type: int, float, NoneType
	- Default: None

__Returns:__

A (position, timestamp) tuple. The position is None if a timeout occurs.

- Type: tuple

</div>

<div class="FunctionDoc YAMLDoc" id="joystick-get_joyballs" markdown="1">

## function __joystick\.get\_joyballs__\(timeout=None\)

Waits for joystick trackball movement.

__Keywords:__

- `timeout` -- A timeout value in milliseconds or `None` to use default timeout.
	- Type: int, float, NoneType
	- Default: None

__Returns:__

A (position, timestamp) tuple. The position is `None` if a timeout occurs.

- Type: tuple

</div>

<div class="FunctionDoc YAMLDoc" id="joystick-get_joybutton" markdown="1">

## function __joystick\.get\_joybutton__\(joybuttonlist=None, timeout=None\)

Collects joystick button input.

__Keywords:__

- `joybuttonlist` -- A list of buttons that are accepted or `None` to default joybuttonlist.
	- Type: list, NoneType
	- Default: None
- `timeout` -- A timeout value in milliseconds or `None` to use default timeout.
	- Type: int, float, NoneType
	- Default: None

__Returns:__

A (joybutton, timestamp) tuple. The joybutton is `None` if a timeout occurs.

- Type: tuple

</div>

<div class="FunctionDoc YAMLDoc" id="joystick-get_joyhats" markdown="1">

## function __joystick\.get\_joyhats__\(timeout=None\)

Waits for joystick hat movement.

__Keywords:__

- `timeout` -- A timeout value in milliseconds or `None` to use default timeout.
	- Type: int, float, NoneType
	- Default: None

__Returns:__

A (position, timestamp) tuple. The position is `None` if a timeout occurs.

- Type: tuple

</div>

<div class="FunctionDoc YAMLDoc" id="joystick-get_joyinput" markdown="1">

## function __joystick\.get\_joyinput__\(joybuttonlist=None, timeout=None\)

Waits for any joystick input (buttons, axes, hats or balls).

__Keywords:__

- `joybuttonlist` -- A list of buttons that are accepted or `None` to default joybuttonlist.
	- Type: list, NoneType
	- Default: None
- `timeout` -- A timeout value in milliseconds or `None` to use default timeout.
	- Type: int, float, NoneType
	- Default: None

__Returns:__

A (event, value, timestamp) tuple. The value is `None` if a timeout occurs.

- Type: tuple

</div>

<div class="FunctionDoc YAMLDoc" id="joystick-input_options" markdown="1">

## function __joystick\.input\_options__\(\)

Generates a list with the number of available buttons, axes, balls and hats.

__Returns:__

A list with number of inputs as: [buttons, axes, balls,
hats].

- Type: list

</div>

<div class="FunctionDoc YAMLDoc" id="joystick-set_joybuttonlist" markdown="1">

## function __joystick\.set\_joybuttonlist__\(joybuttonlist=None\)

Sets a list of accepted buttons.

__Keywords:__

- `joybuttonlist` -- %arg_joybuttonlist
	- Type: list, NoneType
	- Default: None

</div>

<div class="FunctionDoc YAMLDoc" id="joystick-set_timeout" markdown="1">

## function __joystick\.set\_timeout__\(timeout=None\)

Sets a timeout.

__Keywords:__

- `timeout` -- %arg_timeout
	- Type: int, float, NoneType
	- Default: None

</div>

</div>

