### Generate And Release Instance

<br>

#### Generate Instance
The first step must always be Generate Instance.

```
IHybRecorder *instance = HybGenerateInstance(AppID, SecretID, 0);
``` 

If you don't know your Secret ID, please read the section "Get Your Secret ID" in "Building With Hypereal BigData SDK".
The App ID is just a symbol to distinguish between different users.
In order to prevent the conflict, it is recommended to use your App ID geted from Hypereal.

#### Release Instance

The last step will be Hypereal BigData SDK Release Instance.

```
HybReleaseInstance(instance);
```

This function will clean up all resources held by Instance.

#### ATTENTION

In fact, the period of data transmission is one second, the instance will cache all the data to be uploaded. If you immediately release the instance after recording the event or setting the property, the buffer data will fail to upload. So it is not recommended to frequently generate and release the instance, just using only an instance is fine.