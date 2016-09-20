<div class="ClassDoc YAMLDoc" id="image_button" markdown="1">

# class __image_button__

The image_button widget is a clickable image.

__Example (OpenSesame script):__

~~~
widget 0 0 1 1 image_button path='5.png' var='response'
~~~

__Example (Python):__

~~~ .python
from libopensesame import widgets
form = widgets.form(exp)
# The full path to the image needs to be provided.
# self.experiment.pool can be used to retrieve the full path
# to an image in the file pool.
image_button = widgets.image_button(form, path=pool['5.png'],
        var='response')
form.set_widget(image_button, (0,0))
form._exec()
~~~

[TOC]

<div class="FunctionDoc YAMLDoc" id="image_button-__init__" markdown="1">

## function __image\_button\.\_\_init\_\___\(form, path=None, adjust=True, frame=False, image\_id=None, var=None\)

Constructor.

__Arguments:__

- `form` -- The parent form.
	- Type: form

__Keywords:__

- `path` -- The full path to the image. To show an image from the file pool, you need to first use `experiment.get_file` to determine the full path to the image.
	- Type: str, unicode, NoneType
	- Default: None
- `adjust` -- Indicates whether the image should be scaled according to the size of the widget.
	- Type: bool
	- Default: True
- `frame` -- Indicates whether a frame should be drawn around the widget.
	- Type: bool
	- Default: False
- `image_id` -- An id to identify the image when it is clicked. If `None`, the path to the image is used as id.
	- Type: str, unicode, NoneType
	- Default: None
- `var` -- The name of the experimental variable that should be used to log the widget status.
	- Type: str, unicode, NoneType
	- Default: None

</div>

[image_button.__init__]: #image_button-__init__
[__init__]: #image_button-__init__

<div class="FunctionDoc YAMLDoc" id="image_button-draw_frame" markdown="1">

## function __image\_button\.draw\_frame__\(rect=None, style=u'normal'\)

Draws a simple frame around the widget.

__Keywords:__

- `rect` -- A (left, top, width, height) tuple for the frame geometry or `None` to use the widget geometry.
	- Type: tuple, NoneType
	- Default: None
- `style` -- A visual style. Should be 'normal', 'active', or 'light'.
	- Type: str, unicode
	- Default: 'normal'

</div>

[image_button.draw_frame]: #image_button-draw_frame
[draw_frame]: #image_button-draw_frame

<div class="FunctionDoc YAMLDoc" id="image_button-on_mouse_click" markdown="1">

## function __image\_button\.on\_mouse\_click__\(pos\)

Is called whenever the user clicks on the widget. Returns the image_id or the path to the image if no image_id has been specified.

__Arguments:__

- `pos` -- An (x, y) coordinate tuple.
	- Type: tuple

</div>

[image_button.on_mouse_click]: #image_button-on_mouse_click
[on_mouse_click]: #image_button-on_mouse_click

<div class="FunctionDoc YAMLDoc" id="image_button-render" markdown="1">

## function __image\_button\.render__\(\)

Draws the widget.

</div>

[image_button.render]: #image_button-render
[render]: #image_button-render

<div class="FunctionDoc YAMLDoc" id="image_button-set_rect" markdown="1">

## function __image\_button\.set\_rect__\(rect\)

Sets the widget geometry.

__Arguments:__

- `rect` -- A (left, top, width, height) tuple.
	- Type: tuple

</div>

[image_button.set_rect]: #image_button-set_rect
[set_rect]: #image_button-set_rect

<div class="FunctionDoc YAMLDoc" id="image_button-set_var" markdown="1">

## function __image\_button\.set\_var__\(val, var=None\)

Sets an experimental variable.

__Arguments:__

- `val` -- A value.

__Keywords:__

- `var` -- A variable name, or None to use widget default.
	- Type: str, unicode, NoneType
	- Default: None

</div>

[image_button.set_var]: #image_button-set_var
[set_var]: #image_button-set_var

</div>

[image_button]: #image_button
