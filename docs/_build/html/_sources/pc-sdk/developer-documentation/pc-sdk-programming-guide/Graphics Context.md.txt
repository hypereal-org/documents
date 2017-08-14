### Graphics Context
<br>

Graphics context is the abstract of Hypereal VR rendering solution. It provides important information for stereo rendering, such as render target size, eye poses. It submits render target textures, and copies mirror/distorted texture back.

#### Creation, Release and Update

Graphics context is created by a device.
```
HyGraphicsContext *vrGraphicsCxt = nullptr;
HyGraphicsContextDesc cxtDesc;
cxtDesc.m_graphicsDevice = (ID3D11Device*)d3d11Device;
cxtDesc.m_graphicsAPI = HY_GRAPHICS_D3D11;
cxtDesc.m_pixelFormat = HY_TEXTURE_R8G8B8A8_UNORM_SRGB;
cxtDesc.m_pixelDensity = 1.0f;
cxtDesc.m_mirrorWidth = 1920;
cxtDesc.m_mirrorHeight = 1080;
cxtDesc.m_generateMips = false;
cxtDesc.m_flags = 0;
HyResult r = vrDevice->CreateGraphicsContext(cxtDesc, &vrGraphicsCxt);
```

The first parameter is a descriptor composed by native graphics device, graphics API type, pixel format, pixel density and mirror/distorted texture size.

To dispose a graphics context, just call its Release() method.

```
vrGraphicsCxt->Release();
```

A device can create only one graphics context. An application must first release the created one and then create a new one if graphics context needs to be updated.

```
vrGraphicsCxt->Release();
vrGraphicsCxt = nullptr;
HyResult r = vrDevice->CreateGraphicsContext(cxtDesc, &vrGraphicsCxt);
```

#### Configure Rendering

The first step to configure stereo rendering is to calculate render target size.

```
uint32_t leftWidth = 0, leftHeight = 0;
uint32_t rightWidth = 0, rightHeight = 0;
vrGraphicsCxt->GetRenderTargetSize(HY_EYE_LEFT, leftWidth, leftHeight);
vrGraphicsCxt->GetRenderTargetSize(HY_EYE_RIGHT, rightWidth, rightHeight);
```

These returned values are the final render target sizes if an application uses two render targets (one for each eye). However, if the application uses only one render target for two eyes, the final size is:

```
uint32_t finalWidth = leftWidth + rightWidth;
uint32_t finalHeight = leftHeight > rightHeight ? leftHeight : rightHeight;
```

Note: the returned render target size is affected by pixel density (it's set when creating graphics context).

#### Rendering Loop

The main loop of stereo rendering using Hypereal VR SDK includes following steps.
  	1. Get HMD pose
  	2. Get eye pose
  	3. Get or use updated FOV
  	4. Calculate projection matrix
  	5. Render scene
  	6. Calculate projection matrix

1. Get HMD pose

```
    HyTrackingState hmdTrackingState;
    HyResult r = vrDevice->GetTrackingState(HY_SUBDEV_HMD, 0, hmdTrackingState);
```
The second parameter is current frame number (0 is acceptable)

2. Get eye poses

```
    HyPose eyePoses[HY_EYE_MAX];
    vrGraphicsCxt->GetEyePoses(hmdTrackingState.m_pose, nullptr, eyePoses);
```

An application can pass interpupillary distance as the second parameter, it's optional (default value will be used if passing nullptr)

3. Get or use updated FOVs

```
HyFov fov[2];
r = vrDevice->GetFloatArray(HY_PROPERTY_HMD_LEFT_EYE_FOV_FLOAT4_ARRAY, fov[0].val, 4);
r = vrDevice->GetFloatArray(HY_PROPERTY_HMD_RIGHT_EYE_FOV_FLOAT4_ARRAY, fov[1].val, 4);
```

An application can get the standard FOV values of current HMD.  And of course the application could change these values as needed, for some specifal gameplay / effects etc.

4. Calculate projection matrix

```
HyMat4 projMatrix;
vrGraphicsCxt->GetProjectionMatrix(fov[eyeIndex], 0.1f, 1000.0f, true, projMatrix);
```

Calculate projection matrix for each eye, the first parameter is the FOV for this eye.  The next two are z values of the near and far clipping planes. The fourth parameter specifies the coordinate system to use.

5. Render scene

Render the game scene to a render target texture with view matrix from eye pose and projection matrix above.

6. Submit render target texture

```
HyTextureDesc texture;
texture.m_texture = (ID3D11Texture2D*)rtTextureHandle;
texture.m_uvOffset = HyVec2{ 0.0f, 0.0f };
texture.m_uvSize = HyVec2{ 1.0f, 1.0f };
texture.m_flipU = false;
texture.m_flipV = false;
HyResult r = vrGraphicsCxt->Submit(0, &texture, 1, nullptr, nullptr);
```

The first parameter is current frame number (0 is acceptable, but if you want the tracking system to work more precisely for your application please specific detailed frame number of current frame). The second parameter is a pointer to HyTextureDesc which is the descriptor for render target texture. The descriptor is composed by texture handle, UV offset and size, flags to flip UV or no. The third parameter specifies the number of render target textures. The fourth parameter is optional, it specifies the region of render target textures. The last parameter is optional too, it specifies eye FOVs (default FOVs in HyDeviceDesc will be used if it is nullptr, but if you updated these FOVs please pass them here).

#### Mirror/Distorted Texture

An application can get the mirror/distorted result if it needs.

```
CD3D11_TEXTURE2D_DESC texDesc(DXGI_FORMAT_R8G8B8A8_UNORM, 1920, 1080);
texDesc.BindFlags = D3D11_BIND_SHADER_RESOURCE | D3D11_BIND_RENDER_TARGET;
ID3D11Texture2D *mirrorTexture = nullptr;
d3d11Device->CreateTexture2D(&texDesc, NULL, &mirrorTexture);
vrGraphicsCxt->CopyMirrorTexture(mirrorTexture, 1920, 1080, nullptr);
```

The first three parameters are destination texture information including texture handle, texture size. The last parameter specifies the region of mirror/distorted texture to copy. It's optional, passing nullptr means the entire region.
