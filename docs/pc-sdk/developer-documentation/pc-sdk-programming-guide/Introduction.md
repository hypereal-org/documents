### Introduction

<br>

#### API Overview

Hypereal VR SDK has a small API footprint that includes structs, abstract classes, enumerations and functions. All of them have the prefix "Hy". The interfaces defined by abstract classes provide the major features of the SDK. We intend to keep the API clean, stable and backwards-compatible.

**HyResult** defines the success and error codes.

**HyGraphicsAPI** defines the supported graphics API.

**HyTextureFormat** defines the supported texture formats.

**HyEye** is a convenient enumeration for indexing eyes.

**HyVec2**, **HyVec3**, **HyQuat**, **HyMat4**, **HyPose** are the common math structs. We don't provide any functions, math operators to them. An application should leverage these values in its own math classes if it needs to operate them

- **HyMat4** is a column majored matrix which is layout compatible with popular graphics API such as Direct3D and OpenGL
- **HyPose** represents a rigid euclidean transform (affine transform without scale)

**HyFov** describes FOV (field of view) of a viewport. It's a flexible format which can represent asymmetrical FOV.

**HyViewport** is used to define a viewport or region of textures.

The API is well documented, developers can find more detail explanation there.

#### Coordinate System

Hypereal VR SDK uses a right hand coordinate system. The x axis points to the right, the y axis points upward and the z axis points outwards the screen. Distance unit is meters. If an application uses a different coordinate system, it should do a mapping between them.
