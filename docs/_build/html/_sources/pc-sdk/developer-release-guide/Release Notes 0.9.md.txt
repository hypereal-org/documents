
### Release notes 0.9

#### Features
-	Optimized distortion algorithm to support both AMD and nVidia graphic card for better visual effect
- Expand the support of Queue Ahead function to Windows 7
-	Support for new DVT2 device
- Support proximity sensor on HMD
- Optimized flow for room setting
- Optimized flow for firmware upgrade: HMD first then controller
- Unity supports
--	Add the support to VRTK, align with commit af7ccb638fef06236c07233f367327473728795a on the VRTK master branch
--  New interfaces to get velocity, angle velocity, acceleration and angular acceleration
- Unreal supports
--  Add the support for new 2D plane display like unreal console
--  New BP functions to get velocity, angle velocity, acceleration and angular acceleration

#### Known Issues

- Camera may not work well with the USB3.0 ports of some mother boards. The solution is to connect the camera to an independent USB 3.0 HUB with power adapter then to the PC USB port
- Devices may not work well when Oculus runtime is running because of graphic device conflict. The solution is to turn off Oculus service and runtime.
- For Plugin version under 0.5, it is not backward compatible, for Plugin version above 0.5, it is backward compatible down to 0.5.

### Release notes 0.9.1

#### Features
- Add DRM protection to games which launches on Hypereal platform

#### Bug fix
-	Fix the issue that windows focus may be lost when user input text
- Fix the issue that game continues running even after user log out

