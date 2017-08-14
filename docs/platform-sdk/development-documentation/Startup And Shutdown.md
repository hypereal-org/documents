
### Startup and Shutdown

<br>

#### Startup
The first step must always be starting up Hypereal Platform SDK.

```
EHypResult ret = HypStartup(AppID);
``` 

If you don't know your App ID, please read the section "Get Your App ID" in "Building With Hypereal Platform SDK".

#### Shutdown

The last step will be Hypereal Platform SDK shutdown.

```
EHypResult ret = HypShutdown();
```

Those functions will clean up all resources held by SDK.