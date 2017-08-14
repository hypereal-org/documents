
### Networking

<br>

#### Overview



#### API Introduction

##### Send Packet To Single User

```
HypNetworking()->SendPacketToSingleUser(hypID_t userID, uint16_t length, const void *bytes)
```

Send a sequence of bytes to the target user. The length must be less than or equal to the allocated length of bytes.

This API will return true if packet was sent succeed, no matter the target user is online or offline.

If you send a packet but the target user is not online(or in game), the API may still return true, but the target user will not receive this packet, since we will not buffer the packet.

##### Send Packet To Current Room

```
HypNetworking()->SendPacketToCurrentRoom(uint16_t length, const void *bytes);
```

Send a sequence of bytes to all members of the room, excluding the currently logged in user.

Note that the room has to be created or joined by calling one of the existing room functions.

##### Read Packet

```
hypDataPacketRecv*  HypNetworking()->PacketRead();
```

Read the next incoming packet. Return nullptr if no more packets are available.

For example:

```
hypDataPacketRecv *packet;
while(packet = HypNetworking()->PacketRead())
{
	hypID_t sender = packet->GetSenderID();
	//TODO: handle packet data
	HypNetworking()->PacketFree();
}
```

##### Free Packet

```
HypNetworking()->PacketFree(hypDataPacketRecv *packet);
```

Each packet read should eventually be freed.
