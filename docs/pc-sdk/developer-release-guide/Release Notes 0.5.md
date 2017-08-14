
### Release notes 0.5

#### Features
- Asynchronous Space Warping (w/ both nVidia and AMD graphic cards)
- Layer support. Different layer can have different resolution. More texture formats are supported
- Hypereal touch support and camera tracking support
- Optimized system performance with queue ahead rendering
- Optimized flow for room setting to support new camera
- New runtime UI for configuration setting

#### Known Issues

- HMD USB compatibility issue. HMD may not work normal with some USB ports on some PCs. The root cause is that the current exceeds the capacity of the USB port on some motherboards. The solution is to plug-out then plug-in the USB port HMD 
- The digital line and HDMI lines inside the HMD may be plug out if the user wears the HMD and move too frequent and too fierce. The solution is to plug-in the USB and HDMI lines inside the HMD again
- Camera may not work well with the USB3.0 ports of some mother boards. The solution is to connect the camera to an independent USB 3.0 HUB with power adapter then to the PC USB port
- Game engine(UE and Unity) plugin is not back compatible. An game build with 0.4 plug-in cannot run on the SDK 0.5. The game need to be built again with 0.5 plug-in from SDK 0.5 release package. 

