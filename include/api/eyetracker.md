<div class="ClassDoc YAMLDoc" id="eyetracker" markdown="1">

# class __eyetracker__

A generic Python library for eye tracking.

<div class="FunctionDoc YAMLDoc" id="eyetracker-calibrate" markdown="1">

## function __eyetracker\.calibrate__\(\)

Calibrates the eye tracking system. The actual behavior of this
function depends on the type of eye tracker and is described below.

__EyeLink:__

This function will activate the camera-setup screen, which allows
you to adjust the camera, and peform a calibration/ validation
procedure. Pressing 'q' will exit the setup routine. Pressing
'escape' will first trigger a confirmation dialog and then, upon
confirmation, raises an Exception.

__EyeTribe:__

Activates a simple calibration routine.

__Returns:__

Returns True if calibration succeeded, or False if not; in
addition a calibration log is added to the log file and some
properties are updated (i.e. the thresholds for detection
algorithms).

- Type: bool

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-close" markdown="1">

## function __eyetracker\.close__\(\)

Neatly closes connection to tracker. Saves data and sets
`self.connected` to False.

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-connected" markdown="1">

## function __eyetracker\.connected__\(\)

Checks if the tracker is connected.

__Returns:__

True if connection is established, False if not; sets
`self.connected` to the same value.

- Type: bool

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-draw_calibration_target" markdown="1">

## function __eyetracker\.draw\_calibration\_target__\(x, y\)

Draws a calibration target.

__Arguments:__

- `x` -- The X coordinate
	- Type: int
- `y` -- The Y coordinate
	- Type: int

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-draw_drift_correction_target" markdown="1">

## function __eyetracker\.draw\_drift\_correction\_target__\(x, y\)

Draws a drift-correction target.

__Arguments:__

- `x` -- The X coordinate
	- Type: int
- `y` -- The Y coordinate
	- Type: int

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-drift_correction" markdown="1">

## function __eyetracker\.drift\_correction__\(pos=None, fix\_triggered=False\)

Performs a drift-correction procedure. The exact behavior of this
function on the type of eye tracker and is described below. Because
drift correction may fail, you will generally call this function in
a loop.

__EyeLink:__

Pressing 'q' during drift-correction will activate the camera-setup
screen. From there, pressing 'q' again will cause drift correction
to fail immediately. Pressing 'escape' will give the option to abort
the experiment, in which case an Exception is raised.

__Keywords:__

- `pos` -- (x, y) position of the fixation dot or None for a central fixation.
	- Type: tuple, NoneType
	- Default: None
- `fix_triggered` -- Boolean indicating if drift check should be performed based on gaze position (True) or on spacepress (False).
	- Type: bool
	- Default: False

__Returns:__

A boolean indicating if drift check is ok (True) or not (False).

- Type: bool

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-fix_triggered_drift_correction" markdown="1">

## function __eyetracker\.fix\_triggered\_drift\_correction__\(pos=None, min\_samples=30, max\_dev=60, reset\_threshold=10\)

Performs a fixation triggered drift correction by collecting
a number of samples and calculating the average distance from the
fixation position

__Keywords:__

- `pos` -- (x, y) position of the fixation dot or None for a central fixation.
	- Type: tuple, NoneType
	- Default: None
- `min_samples` -- The minimal amount of samples after which an average deviation is calculated.
	- Type: int
	- Default: 30
- `max_dev` -- The maximal deviation from fixation in pixels.
	- Type: int
	- Default: 60
- `reset_threshold` -- If the horizontal or vertical distance in pixels between two consecutive samples is larger than this threshold, the sample collection is reset.
	- Type: int
	- Default: 10

__Returns:__

A boolean indicating if drift check is ok (True) or not (False).

- Type: bool

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-get_eyetracker_clock_async" markdown="1">

## function __eyetracker\.get\_eyetracker\_clock\_async__\(\)

Returns the difference between tracker time and PyGaze time, which can be used to synchronize timing

__Returns:__

The difference between eyetracker time and PyGaze time.

- Type: int, float

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-log" markdown="1">

## function __eyetracker\.log__\(msg\)

Writes a message to the log file.

__Arguments:__

- `msg` -- A message.
	- Type: str, unicode

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-log_var" markdown="1">

## function __eyetracker\.log\_var__\(var, val\)

Writes a variable's name and value to the log file

__Arguments:__

- `var` -- A variable name.
	- Type: str, unicode
- `val` -- A variable value

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-pupil_size" markdown="1">

## function __eyetracker\.pupil\_size__\(\)

Returns the newest pupil size sample; size may be measured as the diameter or the area of the pupil, depending on your setup (note that pupil size mostly is given in an arbitrary units).

__Returns:__

Returns pupil size for the eye that is currently being tracked (as specified by self.eye_used) or -1 when no data is obtainable.

- Type: int, float

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-sample" markdown="1">

## function __eyetracker\.sample__\(\)

Returns newest available gaze position.

__Returns:__

An (x,y) tuple or a (-1,-1) on an error.

- Type: tuple

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-send_command" markdown="1">

## function __eyetracker\.send\_command__\(cmd\)

Directly sends a command to the eye tracker (not supported for all brands; might produce a warning message if your setup does not support direct commands).

__Arguments:__

- `cmd` -- The command to be sent to the eye tracker.
	- Type: str, unicode

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-set_detection_type" markdown="1">

## function __eyetracker\.set\_detection\_type__\(eventdetection\)

Set the event detection type to either PyGaze algorithms, or
native algorithms as provided by the manufacturer (only if
available: detection type will default to PyGaze if no native
functions are available)

__Arguments:__

- `eventdetection` -- A string indicating which detection type
should be employed: either 'pygaze' for
PyGaze event detection algorithms or
'native' for manufacturers algorithms (only
if available; will default to 'pygaze' if no
native event detection is available)
	- Type: str, unicode

__Returns:__

Detection type for saccades, fixations and blinks in a tuple, e.g. ('pygaze','native','native') when 'native' was passed, but native detection was not available for saccade detection.

- Type: tuple

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-set_draw_calibration_target_func" markdown="1">

## function __eyetracker\.set\_draw\_calibration\_target\_func__\(func\)

Specifies a custom function to draw the calibration target. This will function will override the default [draw_calibration_target].

__Arguments:__

- `func` -- The function to draw a calibration target. This function should accept two parameters, for the x and y coordinate of the target.
	- Type: function

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-set_draw_drift_correction_target_func" markdown="1">

## function __eyetracker\.set\_draw\_drift\_correction\_target\_func__\(func\)

Specifies a custom function to draw the drift-correction target. This function will override the default [draw_drift_correction_target].

__Arguments:__

- `func` -- The function to draw a drift-correction target. This function should accept two parameters, for the x and y coordinate of the target.
	- Type: function

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-set_eye_used" markdown="1">

## function __eyetracker\.set\_eye\_used__\(\)

Logs the `eye_used` variable, based on which eye was specified (if both eyes are being tracked, the left eye is used). Does not return anything.

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-start_recording" markdown="1">

## function __eyetracker\.start\_recording__\(\)

Starts recording. Sets `self.recording` to `True` when recording is successfully started.

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-status_msg" markdown="1">

## function __eyetracker\.status\_msg__\(msg\)

Sends a status message to the eye tracker, which is displayed in the tracker's GUI (only available for EyeLink setups).

__Arguments:__

- `msg` -- A string that is to be displayed on the experimenter PC,
e.g.: "current trial: %d" % trialnr.
	- Type: str, unicode

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-stop_recording" markdown="1">

## function __eyetracker\.stop\_recording__\(\)

Stops recording. Sets `self.recording` to `False` when recording is successfully stopped.

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-wait_for_blink_end" markdown="1">

## function __eyetracker\.wait\_for\_blink\_end__\(\)

Waits for a blink end and returns the blink ending time.
Detection based on Dalmaijer et al. (2013) if EVENTDETECTION is set
to 'pygaze', or using native detection functions if EVENTDETECTION
is set to 'native' (NOTE: not every system has native functionality;
will fall back to ;pygaze' if 'native' is not available!)

__Returns:__

Blink ending time in milliseconds, as measured from experiment begin time.

- Type: int, float

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-wait_for_blink_start" markdown="1">

## function __eyetracker\.wait\_for\_blink\_start__\(\)

Waits for a blink start and returns the blink starting time.
Detection based on Dalmaijer et al. (2013) if EVENTDETECTION is set
to 'pygaze', or using native detection functions if EVENTDETECTION
is set to 'native' (NOTE: not every system has native functionality;
will fall back to ;pygaze' if 'native' is not available!)

__Returns:__

Blink starting time in milliseconds, as measured from experiment begin time

- Type: int, float

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-wait_for_event" markdown="1">

## function __eyetracker\.wait\_for\_event__\(event\)

Waits for an event.

__Arguments:__

- `event` -- An integer event code, one of the following:

- 3 = STARTBLINK
- 4 = ENDBLINK
- 5 = STARTSACC
- 6 = ENDSACC
- 7 = STARTFIX
- 8 = ENDFIX
	- Type: int

__Returns:__

A `self.wait_for_*` method is called, depending on the specified event; the return value of corresponding method is returned.

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-wait_for_fixation_end" markdown="1">

## function __eyetracker\.wait\_for\_fixation\_end__\(\)

Returns time and gaze position when a fixation has ended;
function assumes that a 'fixation' has ended when a deviation of
more than self.pxfixtresh from the initial fixation position has
been detected (self.pxfixtresh is created in self.calibration,
based on self.fixtresh, a property defined in self.__init__).
Detection based on Dalmaijer et al. (2013) if EVENTDETECTION is set
to 'pygaze', or using native detection functions if EVENTDETECTION
is set to 'native' (NOTE: not every system has native functionality;
will fall back to ;pygaze' if 'native' is not available!)

__Returns:__

A `time, gazepos` tuple. Time is the end time in milliseconds (from expstart), gazepos is a (x,y) gaze position tuple of the position from which the fixation was initiated.

- Type: tuple

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-wait_for_fixation_start" markdown="1">

## function __eyetracker\.wait\_for\_fixation\_start__\(\)

Returns starting time and position when a fixation is started;
function assumes a 'fixation' has started when gaze position
remains reasonably stable (i.e. when most deviant samples are
within self.pxfixtresh) for five samples in a row (self.pxfixtresh
is created in self.calibration, based on self.fixtresh, a property
defined in self.__init__).
Detection based on Dalmaijer et al. (2013) if EVENTDETECTION is set
to 'pygaze', or using native detection functions if EVENTDETECTION
is set to 'native' (NOTE: not every system has native functionality;
will fall back to ;pygaze' if 'native' is not available!)

__Returns:__

A `time, gazepos` tuple. Time is the starting time in milliseconds (from expstart), gazepos is a (x,y) gaze position tuple of the position from which the fixation was initiated.

- Type: tuple

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-wait_for_saccade_end" markdown="1">

## function __eyetracker\.wait\_for\_saccade\_end__\(\)

Returns ending time, starting and end position when a saccade is
ended; based on Dalmaijer et al. (2013) online saccade detection
algorithm if EVENTDETECTION is set to 'pygaze', or using native
detection functions if EVENTDETECTION is set to 'native' (NOTE: not
every system has native functionality; will fall back to ;pygaze'
if 'native' is not available!)

__Returns:__

An `endtime, startpos, endpos` tuple. Endtime in milliseconds (from expbegintime); startpos and endpos are (x,y) gaze position tuples.

- Type: tuple

</div>

<div class="FunctionDoc YAMLDoc" id="eyetracker-wait_for_saccade_start" markdown="1">

## function __eyetracker\.wait\_for\_saccade\_start__\(\)

Returns starting time and starting position when a saccade is
started; based on Dalmaijer et al. (2013) online saccade detection
algorithm if EVENTDETECTION is set to 'pygaze', or using native
detection functions if EVENTDETECTION is set to 'native' (NOTE: not
every system has native functionality; will fall back to ;pygaze'
if 'native' is not available!)

__Returns:__

An `endtime, startpos` tuple. Endtime in milliseconds (from expbegintime); startpos is an (x,y) gaze position tuple.

- Type: tuple

</div>

</div>

