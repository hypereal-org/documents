
### User

<br>

#### Overview

#### API Introduction

##### If An User is Already Logged In

```
bool HypUser()->IsUserLoggedIn()
```

User can login via Hypereal App Store Client, so there is no need to login again in the game or app.

Return true means user already logged in.

##### Get Logged In User

```
HypUser()->GetLoggedInUser();
```

A message with type ::EHypMessageType_User_GetLoggedInUser will be generated in response.

Call message->HasError() to check if an error occurred.

If no error occurred, the message will contain a payload of type hypDataLoggedInUser*.

You can extract the payload data from the message via HypUser()->ExtractMessageData();

##### Get User Access Token

```
HypUser()->GetAccessToken();
```

A message with type ::EHypMessageType_User_GetAccessToken will be generated in response.

Call message->HasError() to check if an error occurred.

If no error occurred, the message will contain a payload of type hypDataUserToken*.

You can extract the payload data from the message via HypUser()->ExtractMessageData();

##### Get Logged In User ID

```
HypUser()->GetLoggedInUserID();
```

return 0 if no user was logged in

##### Get Logged In User Image URL

```
HypUser()->GetLoggedInUserImageURL();
```

return null if no user was logged in