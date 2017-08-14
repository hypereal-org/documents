
### Room

<br>

#### Overview



#### API Introduction

##### Get Current Room

```
HypRoom()->GetCurrentRoom()
```

A message with type ::EHypMessageType_Room_GetCurrentRoom will be generated in response.

Call message->HasError() to check if an error occurred.

If no error occurred, the message will contain a payload of type hypDataRoomInfo.

You can extract the payload data from the message via HypRoom()->ExtractMessageData();

##### Create A Room

```
HypRoom()->CreateRoom(const char* roomName, const char* roomDescription, int maxUserNumber)
```

A message with type ::EHypMessageType_Room_CreateRoom will be generated in response, and
you can get this message via HypMessageManager()->Pop().

Call message->HasError() to check if an error occurred.

If no error occurred, the message will contain a payload of type hypDataRoomInfo*.

You can extract the payload data from the message via HypRoom()->ExtractMessageData();

Note that you can't create a room if you are already in a room.

##### Get Room Info

```
HypRoom()->GetRoomInfo(hypID_t roomID)
```

A message with type ::EHypMessageType_Room_GetRoomInfo will be generated in response, and you can get this message via HypMessageManager()->Pop().

Call message->HasError() to check if an error occurred.

If no error occurred, the message will contain a payload of type hypDataRoomInfo*.

You can extract the payload data from the message via HypRoom()->ExtractMessageData();


##### Get Room List

```
HypRoom()->GetRoomList(int roomPageIndex)
```

A message with type ::EHypMessageType_Room_GetRoomList will be generated in response, and you can get this message via HypMessageManager()->Pop().

Call message->HasError() to check if an error occurred.

If no error occurred, the message will contain a payload of type hypDataRoomList*.

You can extract the payload data from the message via HypRoom()->ExtractMessageData();

##### Kick Room User

```
HypRoom()->KickRoomUser(hypID_t userID)
```

A message with type ::EHypMessageType_Room_KickRoomUser will be generated in response, and you can get this message via HypMessageManager()->Pop().

Call message->HasError() to check if an error occurred.

If no error occurred, the message will contain a payload of type hypDataRoomInfo*.

You can extract the payload data from the message via HypRoom()->ExtractMessageData();

Other room members will received a notification message with type ::EHypMessageType_Notification_Room_RoomUpdate

##### Join Room

```
HypRoom()->JoinRoom(hypID_t roomID)
```

A message with type ::EHypMessageType_Room_JoinRoom will be generated in response, and you can get this message via HypMessageManager()->Pop().

Call message->HasError() to check if an error occurred.

If no error occurred, the message will contain a payload of type hypDataRoomInfo*.

You can extract the payload data from the message via HypRoom()->ExtractMessageData();

Other room members will received a notification message with type ::EHypMessageType_Notification_Room_RoomUpdate


##### Leave Room

```
HypRoom()->LeaveRoom()
```

A message with type ::EHypMessageType_Room_LeaveRoom will be generated in response, and you can get this message via HypMessageManager()->Pop().

Call message->HasError() to check if an error occurred.

The message has no payload, if no error occured, it means success.

Other room members will received a notification message with type ::EHypMessageType_Notification_Room_RoomUpdate

If room owner leave his room, the room will be destroyed.
