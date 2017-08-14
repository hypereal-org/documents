
### Release notes 1.0

#### Features
- Optimized distortion algorithm for better visual effect
- Home Key Interception. Press Home Key during the game running, it will be back forward to the previous Background Program.
- Layer has been optimized so that different resolutions can be applied to different layer
- ASW and Queue Ahead can be enabled simultaneously
- Digital signature is applied to SDK executables and dll
- More settings are added in the Background Configuration: Volume, Brightness, Back to APP, Device Status and so on.
- Room Setting is optimized and video tutorial course is provided as well.
- Unreal Platform Plugin is provided with Room and Matchmaking feature
- Unity: Platform Plugin is provided with Room and Matchmaking feature

#### Bug fix
-	Fix the issue that velocity may be incorrect in Unity plugin and Native SDK

#### Known Issues

- Devices may not work well when Oculus runtime is running because of graphic device conflict. The solution is to turn off Oculus service and runtime.
- SDK 1.0 is not backward-compatible with earlier plugin versions.
- Unity Platform Plugin - Second time call to Hypereal.Platform.Init() without Hypereal.Platform.DeInit() gives a HypeError_LoadInterfaces error. Please refer following doc for more detais:
https://www.hypereal.com/#/developer/1.1.0/PC-SDK/Developer-Documentation/Unity-Platfrom-Plugin/Platfrom-Plugin.html#top

