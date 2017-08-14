### Utilities
#### Loading Helper
Loading Helper helps applications display their loading progress. It is helpful when application itself is busy with loading data and not rendering for a long period of time.
To use loading helper, you need to have a device first. See Device about how to get one.
Then you can create a loading helper before application starts loading. The system will displace a screen with loading indicators, when the application stops submitting new frames.
```
HyLoadingHelper* helper = nullptr;
HyCreateInterface(HyLoadingHelper_InterfaceName, 0, &helper);
helper->Init(vrDevice);
```

When the application finishes loading, it should release the loading helper, start normal rendering and submitting new frames to graphics context.
```
helper->Release();
```

Before or while the application is loading, you can set an image for the loading screen too.
```
HyTextureDesc texture;
texture.m_texture = (ID3D11Texture2D*)rtTextureHandle;
texture.m_uvOffset = HyVec2{ 0.0f, 0.0f };
texture.m_uvSize = HyVec2{ 1.0f, 1.0f };
helper -> SetTexture(texture);
```

While you load, application can tell users how far they are, by setting loading progress (1-100). This will be displayed on the loading screen.
```
helper->SetProgress(percentage);
```

#### View Layer
View Layer represents a rectangle surface with a 2D image, and it is displayed over the 3D scene.
It can be created from Device.
```
HyViewLayer* layer = nullptr;
HyCreateInterface(HyViewLayer_InterfaceName, 0, &layer);
layer->Init(vrDevice);
```
When you are done with a view layer, you should release it like this.
```
layer->Release();
```
You need to set an image for the layer to become visible.
```
HyTextureDesc texture;
texture.m_texture = (ID3D11Texture2D*)rtTextureHandle;
texture.m_uvOffset = HyVec2{ 0.0f, 0.0f };
texture.m_uvSize = HyVec2{ 1.0f, 1.0f };
layer->SetTexture(texture);
```
You can give a new size to the layer, to make it larger or smaller.
```
layer->SetSize(HyVec2{ 1.0f, 1.0f });
```
You can also move the layer around, or rotate it to a new angle, by setting its pose.
```
HyPose pose;
pose.m_position = { 0, 0, 0 };
pose.m_rotation = { 0, 0, 0, 1 };
layer->SetPose(pose);
```
There can be priorities between layers. A layer with a larger priority number, will be displayed above layers with smaller numbers. The priority can be set like this.
```
layer->SetPriority(0);
```

#### Input Helper

Input Helper helps application get input from a virtual keyboard. It is helpful when the application wants a private input which will not display in mirror pass. 
To use input helper, you need to have a device first. See Device about how to get one.
Then you can create an input helper before the application starts input. The system will displace the screen with a virtual keyboard when the application stops submitting new frames.
```
if (hySucceeded(HyCreateInterface(HyInputHelper_InterfaceName, 0, (void**)&inputhelper)))
	inputhelper->Init(vrDevice);
```

You can set a default string after initializing successfully.
```
if (hySucceeded(res)) inputhelper->SetDefaultString(TEXT("default"));
```

After the helper Initialized successfully, you can get the input via:
```
const int size = 128;
wchar_t str[size]{};
int realSize = 0;
auto res = inputhelper->GetString(str, size, &realSize, false);
```
**Note**: You should check the result that `GetString` returned. It will return a `HySuccess` if user finished the input.


Once the input is finished, you should release the helper:

```
inputhelper->Release();
inputhelper = nullptr;
```

