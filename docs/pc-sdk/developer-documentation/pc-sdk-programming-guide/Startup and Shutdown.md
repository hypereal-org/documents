### Startup and Shutdown
<br>

The first step of using Hypereal VR SDK is starting up.

```
HyResult r = HyStartup();
```

This function will initialize all components of SDK. If it returns error, all subsequent operations will get unexpected results.

The last step of using Hypereal VR SDK is shutting down.

```
HyResult r = HyShutdown();
```

This function will clean up all resources held by SDK.
