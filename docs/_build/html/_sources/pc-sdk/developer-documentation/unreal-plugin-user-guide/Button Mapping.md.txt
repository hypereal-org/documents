### Button Mapping
<br>

You can use Hypereal Controller with Unreal.

The following is a list of button mapping between Hypereal SDK and Unreal.


| SDK Value  					| Unreal Key									|
| :-------------------------	| :-------------------------------------------------|
| HY_BUTTON_MENU 				| HyTouch_Menu (DisplayName:"Hypereal Touch Menu")
| HY_BUTTON_TOUCHPAD_RIGHT		| MotionController_Right_Thumbstick																			|
| HY_BUTTON_TOUCHPAD_LEFT  		| MotionController_Left_Thumbstick																			|		
| m_indexTrigger  				| MotionController_Left_TriggerAxis/MotionController_Right_TriggerAxis										|
| m_sideTrigger  				| MotionController_Left_Grip1Axis/MotionController_Right_Grip1Axis											|
| m_indexTrigger > threshold	| MotionController_Left_Trigger/MotionController_Right_Trigger												|
| m_sideTrigger  > threshold	| MotionController_Left_Grip1/MotionController_Right_Grip1													|
| m_touchpadProximity  			| HyTouch_Left_TouchPad_CapTouch/HyTouch_Right_TouchPad_CapTouch <br> (DisplayName:"Hypereal Touch (L) TouchPad Touch/Hypereal Touch (R) TouchPad Touch")|
| m_indexTriggerProximity  		| HyTouch_Left_IndexTrigger_CapTouch/HyTouch_Right_IndexTrigger_CapTouch <br> (DisplayName:"Hypereal Touch (L) Index Trigger Touch/Hypereal Touch (R) Index Trigger Touch")	|
| m_touchpad.x    				| MotionController_Left_Thumbstick_X/MotionController_Right_Thumbstick_X 					|
| m_touchpad.y  				| MotionController_Left_Thumbstick_Y/MotionController_Right_Thumbstick_Y					|


The Up/Down/Left/Right buttons of touchpad are emulated in Unreal and do not exist in HyInputState of sdk 


| Emulated Value  				| Unreal Key Name									|
| :-------------------------	| :-------------------------------------------------|
| TouchPad Up 					| MotionController_Left_FaceButton1/MotionController_Right_FaceButton1		|
| TouchPad Down   				| MotionController_Left_FaceButton3/MotionController_Right_FaceButton3		|		
| TouchPad Left  				| MotionController_Left_FaceButton4/MotionController_Right_FaceButton4		|
| TouchPad Right 				| MotionController_Left_FaceButton2/MotionController_Right_FaceButton2		|




