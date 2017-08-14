### Release Notes

This section describes changes for each version release.

#### Release Note 1.1.0:

**Features:**

-  Implemented the feature of  'show model flag' for 'TrackObjRig' and 'RenderModel'.

- Add support for right Sens menu button. Now the menu button on both controller will lag about 0.5s to get a menu event. Double click for both Sens is for SteamVR plugin and Home, which you should not use.


**Changes:**

- Remove Tracker nodes from the prefab ``HyTrackObjRig``.

- An unmatched version between dll and c# code was changed from **Warning** to **Error** in the log.

**Bug fixes:**

- Fix the bug that a crash or nonresponding may be caused when close game too quickly.

- Fix the bug that closing **Unity Editor** may cause a crash when preview.

<br>

--------------------

<br>

#### Release Note 1.0.166

**Features:**

- Check runtime version with plugin version: if plugin version is greater than runtime version, popup a message.(To avoid upward compatibility issue).

<br>

------------------------------

<br>

#### Realease Note 1.0.151

**Features:**

- Check Dll version in c# code in case sometime plugin doesn't update properly.

- Implement 'Loading Helper' which can handle app doesn't submit frame while loading a new scene.

**Bug fixes**

- Fix the bug that app occupies too much GPU resources while pausing.

- Fix the bug that 'preview' can only work on the first time.

<br>

---------------------------------

#### Realease Note 1.0.126

**Bug fixes**

- Fix crash using a released mirror texture pointer.

<br>

-------------------------
#### Realease Note 1.0.0

**Features**

- Add a recommended setting to turn off v-sync in the project.