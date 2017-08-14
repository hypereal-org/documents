### Networking

<br>

Networking provide ways to send packets to other player. You can check the class ``HyPlatformNet`` in ``HyPlatform.cs`` for more infomation.

There're two ways to send packets: ``SendPacketToSingleUser``, ``SendPacketToSingleUser``. You can get packet via ``PacketRead``.

Note that you may want add PacketRead in an update function if you don't miss recive packets.

```
void Update()
{
	var packet = HyPlatformNet.PacketRead();
	if(packet != null)
	{
		// Process packet
	}
}

```