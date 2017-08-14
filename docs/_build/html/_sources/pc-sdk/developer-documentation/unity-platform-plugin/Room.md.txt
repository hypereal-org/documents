### Room

<br>

Room is a place where player can play together, you can check the class ``HyPlatformRoom`` in ``HyPlatform.cs`` for all room interface.

Most of API in this class will create a ``Request<Room>``. You may want set a callback when the request finished:

```
void someFunc()
{
    HyPlatformRoom.CreateRoom(roomName, roomDesc, maxUser).OnComplete(updateRoomCallback);
}

void updateRoomCallback(Message<Room> msg)
{
    if (!msg.IsError)
    {
        Room room = msg.Data;
        // do something with room data.
        // ...
    }
}

```

Note that the API ``GetRoomList`` will create a ``Request<RoomList>``.

You also need to SetUpdateNotifactionCallback to listen the message form platform plugin. It's a ``Message<Room>`` too.

```
void someFunc()
{
    HyPlatformRoom.SetUpdateNotifactionCallback(updateRoomCallback);
}

void updateRoomCallback(Message<Room> msg)
{
    if (!msg.IsError)
    {
        Room room = msg.Data;
        // do something with room data.
        // ...
    }
}
```

**Know issue**

For the roomlist, we do not have a way to get next page of room, we will update this function soon.
