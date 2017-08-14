
### Pop And Free Message

<br>

#### hypRequest_t

All interfaces declared with return type hypRequest_t will generate response message which has a specified message type.

For example, once you have called:

```
HypClient()->IsUserAuthorized()
```

then a message with type EHypMessageType_Client_IsUserAuthorized will be generated in response.

#### Pop Message

You can pop message from the queue(FIFO order) by interface:

```
HypMessage *msg = HypMessageManager()->Pop();
```

#### Extract Message

First of all, get the message type via

```
msg->GetType()
```

Then check if the message has error by calling

```
msg->HasError()
```

If has error, get the error information by

```
msg->GetError()
```

If it has no error, and has payload data, use GetDataHandle() to get data handle, then use the corresponding ExtractMessageData() API to get detail data.

For example, if we received a message with type ::EHypMessageType_Room_GetCurrentRoom

```
if(msg->HasError())
{
	hypDataError *err = msg->GetError();
	if(err)
		//TODO: output error information
}
else
{
	hypDataRoomInfo *room = nullptr;
	if(HypRoom()->ExtractMessageData(msg->GetDataHandle, &room))
	{
		//TODO: output room information
	}
	else
	{
		printf("FATAL error: message didn't contain valid data!\n");
	}
}
```

#### Free Message

Each message should eventually be freed with

```
HypMessageManager()->Free(msg)
```

After this, all previous data(including data handle) derived from HypMessageManager()->Pop() is unusable.
