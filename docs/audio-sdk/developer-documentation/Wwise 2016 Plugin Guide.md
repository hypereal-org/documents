
### Wwise 2016 Plugin Guide 
<br>

#### HyperealVR Wwise 2016 Audio Spatializer Plugin Guide
1.  To install and enable the plugin in Wwise authoring tool, please copy/extract HyprealAudioPlugin.dll and HyperealAudioPlugin.xml to _WwiseDir_\Authoring\x64\Release\bin\plugins .  Please make sure that you've installed Hypereal runtime.

2.  Currently the plugin only supports 1024 "Samples per Output" which can be set in **`Project->User`** Prefrences as shown in  the following picture.
    ![](./res_wwise_guide/wwise_2016_authoring_1.png)

3.  Add a Child Audio Bus under **Master Audio Bus**.  Then select the added bus and click the **Mixer Plug-in** tab.  Add the plugin named "Hypereal Audio Spatializer".  For any sound/audio needs spatialization effect, select the added audio bus as its output bus.  Please note that currently the plugin only support **2-channel** sound sources.  Other kind of sound sources may provide unexpected result.

