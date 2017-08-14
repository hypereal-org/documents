### Unity Plugin FQA

Here's the FQA by developers when using Hypereal VR plugin. We will update this document from time to time. You may want often comeback to see if this page updated.

**Q**:  Which configuration should I choose for Hypereal VR in "Virtual Realty supproted"?

**A**: Those configurations are for SDKs that already implement in Unity native code. Hypereal doesn't implement that way. There're two way to set this setting:
 - Uncheck the "Virtual Realty supproted".
 - Set the "None" section as the first one.
<br>

**Q**: How can I recenter in Hypereal VR plugin?

**A**: Call ``RecenterBase(HyRecenterType)`` in HyperealVR.cs.

<br>

**Q** : How to disable VR setting popup in Unity?

**A**: Make sure ``EnableSettingUI(true) `` in HyperealVR.cs not called any where. If your plugin version is lower than 1.0.99, you should call ``EnableSettingUI(false) `` manually.

<br>

**Q**: How to change the mirror type which showed on desktop?

**A**: Set the ``MirrorType`` in class HyperealVR.

<br>

**Q**: How to disable render controller and tracker model?

**A**: We just implement this function in V1.1. You can easily set ``HyRenderModel.ShowModel`` to ``false`` to hide the model. You can also set ``HyTrackObjRig.ShowModel`` to ``false`` to hide controllers.

