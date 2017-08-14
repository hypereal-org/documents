### Controller 
<br>
#### Input

An application can fetch input state for a specified controller.

The HyInputState Struct includes the following fields:

| Field  					| Description										|
| :-------------------------| :-------------------------------------------------|
| m_buttons					| Button state described by HyButton. A corresponding bit is set if the button is pressed. <br> HY_BUTTON_HOME is reserved for internal usage by Hypereal SDK , so this bit always equals to 0.																													|
| m_touches  				| Touch state described by HyTouch. A corresponding bit is set if the button is touched.											|
| m_indexTrigger  			| Index Trigger value, in the range 0.0f to 1.0f. <br>A value of 1.0f means that the trigger is fully pressed.						|
| m_sideTrigger  			| Side Trigger value, in the range 0.0f to 1.0f. <br>A value of 1.0f means that the trigger is fully pressed.						|
| m_indexTriggerProximity  	| Proximity to index trigger , in the range 0.0f to 1.0f. <br>A value of 1.0f means that the index trigger is touched.				|
| m_touchpadProximity  		| Proximity to touchpad , in the range 0.0f to 1.0f. <br>A value of 1.0f means that the touchpad is touched.						|
| m_touchpad  				| Touchpad axis values as a 2-D vector. <br> The x value represents horizontal axis value , in the range -1.0 to 1.0 ,from left to right.<br>The y value represents Vertical axis value , in the range -1.0 to 1.0 ,from bottom to top.|

The following is a list of the enumeration of HyButton and Hytouch.

| HyButton  				| Description										|
| :-------------------------| :-------------------------------------------------|
| HY_BUTTON_TOUCHPAD_RIGHT	| Touchpad button on the right controller.			|
| HY_BUTTON_TOUCHPAD_LEFT  	| Touchpad button on the left controller.			|
| HY_BUTTON_MENU  			| Menu button.										|
| HY_BUTTON_HOME  			| Home button for private usage by Hypereal.		|

| HyTouch 							| Description												|
| :---------------------------------| :-------------------------------------------------		|
| HY_TOUCH_TOUCHPAD_RIGHT			| User in touching touchpad on the right controller.		|
| HY_TOUCH_INDEX_TRIGGER_RIGHT  	| User in touching index trigger on the right controller. 	|
| HY_TOUCH_TOUCHPAD_LEFT  			| User in touching touchpad on the left controller.			|
| HY_TOUCH_INDEX_TRIGGER_LEFT  		| User in touching index trigger on the left controller. 	|


The following example shows how to get input state and respond.

```
HyInputState inputState;
HyResult r = vrDevice->GetControllerInputState(HY_SUBDEV_CONTROLLER_LEFT, inputState);
if(hySucceeded(r))
{
	if (inputState.m_buttons & HY_BUTTON_TOUCHPAD_LEFT)
	{
		// handle 
	}
}
```

#### Haptic Feedback

An application can also set vibration for a specified controller.

```
HyResult r = vrDevice->SetControllerVibration(HY_SUBDEV_CONTROLLER_RIGHT, 100.0f, 0.5f);
```

The second parameter specifies the duration in millisecond, and the third parameter specifies the vibration amplitude ([0.0, 1.0]).
