### Authorization

#### Overview

When a user can run an application with authorization, it means he have purchased the
application via the Hypereal store, or are otherwise authorized to run this application.
The Platform SDK authorization check system allows you to verify at run-time that the
currently user attempting to run your application is in fact authorized.

#### API Introduction

##### Check Authorization

```
HypClient()->IsUserAuthorized();
```

A message with type ::EHypMessageType_Client_IsUserAuthorized will be generated in response.

The message has no payload, user message->HasError() to check if success.
