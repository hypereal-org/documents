### Release notes 0.5

<br>

The Developer Release Guide will present an overview of the features and API usages of the Platform SDK.

#### Introduction

Hypereal Platform SDK contains features that you can use to create social game experiences.

We're continuously updating our Platform SDK for new features, stability and compatibility.

#### Change List

- Add a new interface class IHypMessageManager for message pop and free.
- Use new API ExtractMessageData() in each module to fetch paylaod from message.
- Add two APIS in IHypUser for developers to get current logged in user's ID or image URL.
- Add a new interface class IHypRoom for multi-players experiences.
- Add a new interface class IHypMatchmaking for multi-players experiences, which only support quick match of two users.
- Add a new interface class IHypNetworking for data send and receive between multi-players.

#### Known Issues

- Two or more apps/games which are integrated with Hypereal Platform SDK are NOT allowed to run on one PC at the same time.
- After you calling HypStartup(), Hypereal Platform SDK will try to connect with multi-player server automatically, this will
take serveral seconds, so if you want to check the server connection before you calling other multi-player functions like HypRoom(),
HypMatchmaking() and HypNetworking(), please call HypClient()->IsServerConnected() first.