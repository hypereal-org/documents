### Device
<br>
Hypereal VR hardwares include HMD (Head Mounted Display), touch controllers and tracking ability. They will return different information at runtime. We call them sub devices. Each sub device has a corresponding enumeration.

#### Sub Devices

Hypereal VR hardwares include HMD (Head Mounted Display), two controllers and some trackers. They will return different information at runtime. We call them sub devices. Each sub device has a corresponding enumeration.

```
enum HySubDevice
{
	HY_SUBDEV_Unknown = -1,									/**< Invalid device type. */
	HY_SUBDEV_HMD = 0,										/**< Head Mounted Display type. */
	HY_SUBDEV_CONTROLLER = 0x100,							/**< Controller type. */
	HY_SUBDEV_CONTROLLER_LEFT = HY_SUBDEV_CONTROLLER,		/**< Prediefined left controller. */
	HY_SUBDEV_CONTROLLER_RIGHT = HY_SUBDEV_CONTROLLER + 1,	/**< Prediefined right controller. */
	HY_SUBDEV_TRACKER = 0x200								/**< Tracker type, 0x200 - 0x299. */
};
```
You could use macro "HyGetSubDeviceType" to get the type from a sub device ID. And you can use "HySubDeviceType" to define new IDs. For example, the conditions in the following assertions are always satisfied:
```
assert(HY_SUBDEV_CONTROLLER_LEFT  == HySubDeviceID(HY_SUBDEV_CONTROLLER, 0));
assert(HY_SUBDEV_CONTROLLER_RIGHT == HySubDeviceID(HY_SUBDEV_CONTROLLER, 1));
assert(HyGetSubDeviceType(HY_SUBDEV_CONTROLLER_LEFT) == HY_SUBDEV_CONTROLLER);
assert(HyGetSubDeviceType(HY_SUBDEV_CONTROLLER_RIGHT) == HY_SUBDEV_CONTROLLER);
```

#### Creation and Release

If Hypereal VR SDK is started up successfully, then a device can be created.

```
HyDevice *vrDevice = nullptr;
HyResult r = HyCreateInterface(HyDevice_InterfaceName, 0, &vrDevice);
```

The first parameter is the version of a specific interface "HyDevice". If the device is created successfully, its pointer will be returned.

To dispose a device, just call its Release method.

```
vrDevice->Release();
```

An application should never call any device methods if the device is released.

#### Runtime Status

Device runtime status may changes each frame. An application should adjust its behavior based on the status.

```
const HyMsgHeader* msg;
HyResult r = vrDevice->RetrieveMsg(&msg);
```

The messages will inform about whether sub devices are connected and tracked, whether the application is on focus (visible), whether the application is pending quit, and whether the inter-papillary distance is changing.

You can switch on `msg->m_type` to know what the current message is about. You can cast msg to the concrete message type HyXXX to get more information about it.

Repeatedly call this function until `msg->m_type` become HY_MSG_NONE, to get all available messages. And pass those you don't know how/want to process, to DefaultMsgFunction to let the system aware and use the default behavior.

#### Properties

Device properties system provides some predefined properties by enumeration of HyDeviceProperty, like FOV, IPD etc.

Application would use the functions such as "GetBoolValue()", "SetBoolValue()", "GetFloatValue", "SetFloatValue" and so on to use this system to retrieve or set properties, please not all set/get methods of properties are implemented, if any of them was not implement, these functions will return hyError_NotImplemented.

#### Tracking

Tracking is an important feature of Hypereal VR SDK. It introduces new human-computer interaction mode. An application can fetch tracking state for HMD and controllers.

```
HyTrackingState trackingState;
HyResult r = vrDevice->GetTrackingState(HY_SUBDEV_HMD, 0, trackingState);
```

An application should pass a frame number (0 is acceptable) as the second parameter. The main components of tracking state includes pose, linear velocity and acceleration, angular velocity and acceleration. Also the tracking state has a flag to specify whether rotation and position are tracked.

**HY_TRACKING_ROTATION_TRACKED** means rotation part is tracked

**HY_TRACKING_POSITION_TRACKED** means position part is tracked

Trackers are key components of the tracking system, however we only provide pose information for them.

```
HyPose pose;
HyResult r = vrDevice->GetTrackerPose(HY_SUBDEV_TRACKER_MASTER, pose);
```

All returned tracking pose is relative to a tracking origin.

**HY_TRACKING_ORIGIN_EYE**

**HY_TRACKING_ORIGIN_FLOOR**

An application can set tracking origin type:

```
HyTrackingOrigin preTrackingOrigin = vrDevice->ConfigureTrackingOrigin(HY_TRACKING_ORIGIN_FLOOR);
```

This method will return current tracking origin type if passing **HY_TRACKING_ORIGIN_UNKNOWN** as the parameter.

#### Without Tracking

Hypereal VR SDK also supports "no tracking" mode for some special product models of Hypereal VR. Developer could checking if current device is tracked or not by property of "HY_PROPERTY_POSITION_TRACKING_ENABLED_BOOL". 

In this mode, we applied a head model in position of returned pose of a HMD from vrDevice->GetTrackerPose(). So if you want to do a head model by yourself, please directly ignore position in that "pose".

**HY_TRACKING_POSITION_TRACKED**, when in tracking mode but this flag was set in flag of pose, we also applied the same head model in it.