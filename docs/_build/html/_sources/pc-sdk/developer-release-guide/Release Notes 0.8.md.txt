
### Release notes 0.8

#### Features
-	New room setting with better user experience, more stable, more accurate and more convenient
-	New distortion algorithm for better visual effect (only applied to nVidia graphic card)
-	Support for DVT device
-	Optimized tracking algorithm for lower CPU usage and dynamic tracking
-	New support for UE 4.15.1

#### Known Issues

- HMD USB compatibility issue. HMD may not work normal with some USB ports on some PCs. The root cause is that the current exceeds the capacity of the USB port on some motherboards. The solution is to plug-out then plug-in the USB port HMD 
- The digital line and HDMI lines inside the HMD may be plug out if the user wears the HMD and move too frequent and too fierce. The solution is to plug-in the USB and HDMI lines inside the HMD again
- Camera may not work well with the USB3.0 ports of some mother boards. The solution is to connect the camera to an independent USB 3.0 HUB with power adapter then to the PC USB port
- For Plugin version under 0.5, it is not backward compatible, for Plugin version above 0.5, it is backward compatible down to 0.5.
- Devices may not work well when Oculus runtime is running because of graphic device conflict. The solution is to turn off Oculus service and runtime.
- Window 7 users may experience a problem while updating firmware, please get more information from PC SDK - > Utilities -> Firmware Upgrade page.

### Release notes 0.8.113

#### Changes
-	Fix the issue that the image on one of the eye may flash in some games
- 	Fix the issue that the image may judder in some games
