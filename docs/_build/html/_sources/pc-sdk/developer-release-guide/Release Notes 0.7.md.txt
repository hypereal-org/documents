
### Release notes 0.7

#### Features
- Optimized system performance for time warping
- DFU function to upgrade the FW of HW devices
- Support of installing unreal plugin to the directory of project
- Record user pose and position
- Support more than one camera in Unity plugin

#### Known Issues

- HMD USB compatibility issue. HMD may not work normal with some USB ports on some PCs. The root cause is that the current exceeds the capacity of the USB port on some motherboards. The solution is to plug-out then plug-in the USB port HMD 
- The digital line and HDMI lines inside the HMD may be plug out if the user wears the HMD and move too frequent and too fierce. The solution is to plug-in the USB and HDMI lines inside the HMD again
- Camera may not work well with the USB3.0 ports of some mother boards. The solution is to connect the camera to an independent USB 3.0 HUB with power adapter then to the PC USB port
- Game engine(UE and Unity) plugin is not back compatible. An game build with 0.4 plug-in cannot run on the SDK 0.5. The game need to be built again with 0.5 plug-in from SDK 0.5 release package. 
- Devices may not work well when Oculus runtime is running because of graphic device conflict. The solution is to turn off Oculus service and runtime.
- Window 7 users may experience a problem while updating firmware, please get more information from PC SDK - > Utilities -> Firmware Upgrade page.
