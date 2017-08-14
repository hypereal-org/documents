### Building With Hypereal Platform SDK

Hypereal Platform SDK is only available on Windows OS currently.
It requires either Visual Studio 2013 or Visual Studio 2015.

#### Get Your App ID

Before starting integrate Platform SDK, you need to get your App ID in Hypereal Developer Center.

This App ID is used to initialize the Hypereal Platform SDK.

#### Redistribution

Developers must first install Hypereal runtime to run their Hypereal VR applications.
The runtime installs all necessary DLLs which will be loaded automatically when applications start.

#### Header File

Header files are sperated, but you just need to include only one file.

```
#include "Hypereal_Platform.h"	// Hypereal Platform SDK header file
```

#### Library

Hypereal Platform SDK is a static library.

```
#pragma comment(lib, "HvrPlatformAPI.lib")
```