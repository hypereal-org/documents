### Unity Platfrom Plugin Guide
<br>

This plugin is for Unity to develop Hypereal Platform functions.

Note: You may want to install Hypereal Plugin first because the demo scene depends on some resource in Hypereal Plugin.

Once you import the platform plugin successfully. You can use interfaces in ``HyPlatform.cs``. And you can check ``hvr_platform_sample.cs``  for how to use them.

**Set AppID**

You can set AppID in Menu: ``Hypereal`` --> ``Platform Setting``. 

**Startup**
   
You should call ``Init()`` before you call any other functions
       
    bool ret = Hypereal.Platform.Init();

**Note:** Since there's a known issue if ``Init()`` calls multiple times without calling ``DeInit()``, you will get an error of ``EHypError_LoadInterface`` which will cause initialize failed. This is due to Unity Editor holds the platform dll which never release until restart it. We will fix this issue in next version. To solve this problem, you **MUST** call ``DeInit()`` when quit.
    
**Shutdown**

You can call ``DeInit()`` before your game shuts down.
    
    bool ret = Hypereal.Platform.DeInit(); 
    
    
**Entitlement**

You can call ``IsUserAuthorized()`` to check the entitlement of current user. Since the platform SDK works asynchronously, you may want to add a callback function for ``OnComplete()``

    ...
    public void IsUserAuthorized()
    {
        HyPlatform.IsUserAuthorized().OnComplete(IsUserAuthorizedCallback);
    }
    void IsUserAuthorizedCallback(Message msg)
    {
        // do stuffs with msg
    }
    
Other uses are same as the entitlement, for more information, you can check ``hvr_platform_sample.cs``.
 
 