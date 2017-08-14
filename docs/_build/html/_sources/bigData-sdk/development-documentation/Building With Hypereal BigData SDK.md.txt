### Building With Hypereal BigData SDK

Hypereal BigData SDK is only available on Windows OS currently.
It requires either Visual Studio 2013 or Visual Studio 2015.

#### Get Your Secret ID

Before starting integrate BigData SDK, you need to get your Secret ID in Hypereal Developer Center.

This Secret ID is used to initialize the Hypereal BigData SDK, and it is different from the App ID.


#### Redistribution

Developers must first install Hypereal runtime to run their Hypereal VR applications.
The runtime installs all necessary DLLs which will be loaded automatically when applications start.

#### Header File

You just need to include only one header file.

```
#include "Hypereal_BigDataAPI.h"	// Hypereal BigData SDK header file
```

#### Library

Hypereal BigData SDK is a static library.

```
#pragma comment(lib, "HvrBigDataAPI.lib")
```