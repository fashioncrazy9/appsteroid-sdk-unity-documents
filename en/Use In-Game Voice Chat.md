# About In-Game Voice Chat

## Introduction
In-game text chat is a solution to have realtime communication with other players during game play. Up to 4 players can communicate during a session.

## Steps and Sample

### Preparation
* To use functions provided by AppSteroid, follow the document [GetStarted](GetStarted.md) and complete the initial setup.
* In coming calls for voice chat will function through push message, so please complete the settings referring to these documents [iOS]([Unity-iOS]Setting Up PushNotification.md)/[Android]([Unity-Android]Setting Up PushNotification.md) as well.

### Settings for Incoming Call
Setup the behavior for incoming calls during the game with the following method.

    public static void SetIncomingVoiceChatBehavior(IncomingVoiceChatBehavior incomingVoiceChatBehavior)

IncomingVoiceChatBehavior defines the behavior of incoming calls and the default behavior is Ask.

|Value|description|
|-----|-----|
|Ask|Ask players whether to join the conference or not with a confirmation dialog box |
|AutoAccept|Automatically join to the conference |
|DoNothing|Ignore|

### Transmitting Voice Chat

Use the following method to transmit voice chat. The transmitter will start a group voice chat as a host. Any voice session will end when the host disconnect from that session.

  public static void StartConference(string groupId, Action<Error> startConferenceCallback, Action<Error> createConferenceCallback)


##### Sample Code

  {
    FASConference.StartConference(Group.Id, OnGroupConferenceStartError, OnGroupConferenceCreateError);
  }

  void OnGroupConferenceStartError(Error error)
        {
            if (error != null)
            {
               Debug.LogError("GroupConferenceError : " + error.ToString());
            }
        }

    void OnGroupConferenceCreateError(Error error)
        {
            if (error != null)
            {
               Debug.LogError("GroupConferenceError : " + error.ToString());
            }
        }

### Disconnecting Voice Chat

Disconnect the voice chat session using the following method. Any voice session will end when the host disconnect from that group. Guest can individually disconnect from the session.

  public static bool Leave()

###　Incoming Voice Chat

The behavior for incoming voice chat all depends on the settings of IncomingVoiceChatBehavior. If you choose to use Ask or AutoAccept, the SDK will handle all of the incoming process, so no extra implementation is needed.

If you choose to use DoNothing, you need to handle the incoming notification event and carry out the connection process. Please check the following sample code.

#### Incoming Process Sample Code for DoNothing

  // 1. Register event for group conference created notification
  {
    FASEvent.OnGroupConferenceCreated += OnGroupConferenceCreated;
  }

  // 2. Trigger group conference created notification event on incoming call
  void OnGroupConferenceCreated(GroupConference groupConference)
  {
    // Join group conference as a geust
    FASConference.JoinConference(groupConference, OnGroupConferenceJoinError);

    // Register event for errors during the conference
    FASConference.OnError += OnGroupConferenceError;
  }

  // Error handling when joining the group
  void OnGroupConferenceJoinError(Error error)
  {
       if (error != null)
    {
      Debug.LogError("GroupConferenceError : " + error.ToString());
    }
  }

  // Error handling during the conference
  void OnGroupConferenceError(Error error)
  {
    Debug.LogError("GroupConferenceError : " + error.ToString());
  }


### Other functions
Please check [Class FASConference](Specs/Spec-FASConference.md) for more information.
