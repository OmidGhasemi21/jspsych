# jspsych-slider-response plugin

This plugin displays an image or HTML-formatted content and allows the subject to respond by pressing a key on the keyboard. The stimulus can be displayed until a response is given, or for a pre-determined amount of time. The trial can be ended automatically if the subject has failed to respond within a fixed length of time.

Because this plugin can display any HTML content, it is quite versatile. It can be used for any situation in which the response generated by the subject is a single keystroke.

## Parameters

This table lists the parameters associated with this plugin. Parameters with a default value of *undefined* must be specified. Other parameters can be left unspecified if the default value is acceptable.

Parameter | Type | Default Value | Description
----------|------|---------------|------------
stimulus | string | *undefined* | The stimulus to display. Either HTML-formatted, or the path to an image.
is_html | boolean | false | If `stimulus` is an HTML-formatted string, this parameter needs to be set to `true`.
min | integer | 0 | The minimum value of the slider scale.
max | integer | 100 | The maximum value of the slider scale.
step | integer | 1 | The step size of the slider scale.
labels | array of strings | *undefined* | A set of labels for the slider scale. They will be automatically distributed so that the first and last labels are centered below the endpoints of the scale. The other labels will be spaced at equal intervals.

## Data Generated

In addition to the [default data collected by all plugins](overview#datacollectedbyplugins), this plugin collects the following data for each trial.

Name | Type | Value
-----|------|------
response | numeric | The numeric value of the slider.
rt | numeric | The time in milliseconds for the subject to make a response. The time is measured from when the stimulus first appears on the screen until the subject's response.

## Examples

#### Approximating a smooth continuous scale with the default settings

```javascript
var trial = {
	type: 'slider-response',
	stimulus: '<p>How similar are these pictures?</p><img src="img/happy_face_1.jpg"></img><img src="img/sad_face_1.jpg"></img>',
	labels: ["Not at all similar",  "Identical"],
}
```

#### Using min, max, and step to create a discrete scale with labeled options

```javascript
var trial = {
	type: 'slider-response',
	stimulus: '<p>How similar are these pictures?</p><img src="img/happy_face_1.jpg"></img><img src="img/sad_face_1.jpg"></img>',
	labels: ["Not similar", "Sort of similar", "Very similar"],
	min: 0,
	max: 2,
	step: 1
}
```