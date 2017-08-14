### Matchmaking

<br>

Matchmaking is a mechanism to create a quick match between **two** players. You can check the class ``HyPlatformMatchmaking`` in ``HyPlatform.cs`` for all HyPlatformMatchmaking interface.

``QuickMatch_Enqueue`` and ``QuickMatch_Cancel`` will create a ``Request``. You may want set a callback when the request finished:

```
void SomeFunc()
{
	HyPlatformMatchmaking.QuickMatch_Enqueue.OnComplete(QuickMatchEnqueue);
}

void QuickMatchEnqueue(Message msg)
{
 	if (!msg.IsError)
	{
    	// Enqueue succeed
	}
}

```

You may want register a match found notification callback to listen the message of match found.

```
void SomeFunc()
{
	HyPlatformMatchmaking.SetMatchFoundNotificationCallback(matchmakingNotifactionCallback);
}

void matchmakingNotifactionCallback(Message<Matchmaking> msg)
{
    if (!msg.IsError)
    {
        Matchmaking mm = msg.Data;
        // Do something with matchmaking data.
    }
}
```