# FASConference Specifications

Last update at 2014/10/15

----------

##  Introduction

## <a name ="FASConference">FASConference Class</a>
Class to operate GroupConference (VoiceChat).

----------

##  Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASConference](#FASConference)|Class to operate Group conference (Voice Chat) |

----------

### Methods

|Name|Description|
|------|-----|
|[FASConference.StartConference](#FASConference.StartConference)|Start a group conference as a Host (Send Voice Chat).|
|[FASConference.JoinConference](#FASConference.JoinConference)|Join a group conference as a guest (Receive Voice Chat).|
|[FASConference.Leave](#FASConference.Leave)|Leave group conference (Hang up Voice Chat).|
|[FASConference.Mute](#FASConference.Mute)|Mute mic |
|[FASConference.UnMute](#FASConference.UnMute)|Unmute mic |
|[FASConference.Volume](#FASConference.Volume)|Setup Volume for mic and speaker |
|[FASConference.GetConferenceElapsedTime](#FASConference.GetConferenceElapsedTime)|Get duration time of an ongoing group conference. It will always return 0 when there aren't any ongoing call. |
|[FASConference.SetIncomingVoiceChatBehavior](#FASConference.SetIncomingVoiceChatBehavior)|Setup a behavior for when receiving group conference push notification.|
|[FASConference.GetIncomingVoiceChatBehavior](#FASConference.GetIncomingVoiceChatBehavior)|Get set upped behavior for when receiving group conference push notification.|
|[FASConference.GetConferenceRole](#FASConference.GetConferenceRole)|Get role for group conference.|
|[FASConference.GetGroupConferenceParticipants](#FASConference.GetGroupConferenceParticipants)|Get participants of group conference.|
|[FASConference.GetCurrentConference](#FASConference.GetCurrentConference)|Get the current participated group conference.|

### Defines

#### <a name ="FASConference.ConferenceStates">enum ConferenceStates</a>
Group Conference Status

|Value|description|
|-----|-----|
|None|None|
|Destroyed|Conference is destroyed |
|Created|Conference is created |

#### <a name ="FASConference.ConferenceRole">enum ConferenceRole</a>
Roles for user on group conference

|Value|description|
|-----|-----|
|None|None|
|Host|Host|
|Guest|Guest|
|HostOrGuest|Host or Guest|

#### <a name ="FASConference.CallStates">enum CallStates</a>

Response status of user on group conference

|Value|description|
|------|-----|
|Idle|Non-call state|
|Progressing|In-process of starting a call|
|Calling|Calling|
|Connected|Connected|
|Ending|Ending a call|

#### <a name ="FASConference.IncomingVoiceChatBehavior">enum IncomingVoiceChatBehavior</a>
Response method when receiving a push notification for creating a new group conference.

|Value|description|
|-----|-----|
|Ask|Connect to the conference after the user response to the confirmation dialog|
|AutoAccept|Automatically connect to the conference|
|DoNothing|Do nothing|

### Events
||Type|Name|Description|
|---|---|---|---|
|public static event| Action\<[ConferenceStates](#FASConference.ConferenceStates)>| OnConferenceStateChanged | It is called when there are changes on ConferenceStates |
|public static event| delegate void CallStateChangeDelegate(string groupId, string partnerId, [CallStates](#FASConference.CallStates) </a>callState) | OnCallStateChanged | It is called when there are changes on CallStates |
|public static event| Action\<Error>| OnError | It is called when an error occurs |


### <a name ="FASConference.StartConference">FASConference.StartConference</a>
Start a group conference as a host (Send Voice Chat).

  public static void StartConference(string groupId, Action<Error> startConferenceCallback, Action<Error> createConferenceCallback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|groupId| string |A Group ID, starting a group conference|
|startConferenceCallback| Action\<Error> |This is a delegate that will be called when the process to start group conference is completed. The delegate contains a error code argument. |
|createConferenceCallback| Action\<Error> |This is a delegate that will be called when the process to create group conference is completed. The delegate contains a error code argument. |

#### Example

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

### <a name ="FASConference.JoinConference">FASConference.JoinConference</a>
Join group conference as a guest (receive voice chat). Receiving a push notification event about group conference being created will trigger to join to the conference.

  public static void JoinConference(GroupConference groupConference, Action<Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|groupConference| GroupConference | GroupConference model to join. Get from FASEvent.OnGroupConferenceCreated Event. |
|callback| Action\<Error> |This is a delegate that will be called when the process to join group conference is completed. The delegate contains a error code argument. |

#### Example

  // 1. Set up an event for group conference creation notice
  {
    FASEvent.OnGroupConferenceCreated += OnGroupConferenceCreated;
  }

  // 2. group conference creation notice event occurs
  void OnGroupConferenceCreated(GroupConference groupConference)
  {
    FASConference.JoinConference(groupConference, OnGroupConferenceJoinError);

    FASConference.OnError += OnGroupConferenceError;
  }

  void OnGroupConferenceJoinError(Error error)
  {
       if (error != null)
    {
      Debug.LogError("GroupConferenceError : " + error.ToString());
    }
  }

  void OnGroupConferenceError(Error error)
  {
    Debug.LogError("GroupConferenceError : " + error.ToString());
  }


### <a name ="FASConference.Leave">FASConference.Leave</a>
Leave group conference (Hang up Voice Chat)

  public static bool Leave()

#### Return
|Type|Description|
|------|-----|
| bool | Result of process (true:success, false:Error)|

### <a name ="FASConference.Mute">FASConference.Mute</a>
Mute mic

  public static bool Mute()

#### Return
|Type|Description|
|------|-----|
| bool | Result of process (true:success, false:Error)|

### <a name ="FASConference.UnMute">FASConference.UnMute</a>
Unmute mic

  public static bool UnMute()

#### Return
|Type|Description|
|------|-----|
| bool | Result of process (true:success, false:Error)|

### <a name ="FASConference.Volume">FASConference.Volume</a>
Setup Volume for mic and speaker. Value rage from 0.0 (Minimum) up to 1.0 (Max).

  public static bool Volume(float volumeMicrophone, float volumeSpeaker)

#### Return
|Type|Description|
|------|-----|
| bool | Result of process (true:success, false:Error)|

#### Parameters
|Name|Type|Description|
|------|------|-----|
|volumeMicrophone| float |Mic Volume|
|volumeSpeaker|　float　|Speaker Volume|


### <a name ="FASConference.GetConferenceElapsedTime">FASConference.GetConferenceElapsedTime</a>
Get duration time of an ongoing group conference. It will always return 0 when there aren't any ongoing call.

  public static long GetConferenceElapsedTime()

#### Return
|Type|Description|
|------|-----|
| long | Duration time for conference (ms) |


### <a name ="FASConference.SetIncomingVoiceChatBehavior">FASConference.SetIncomingVoiceChatBehavior</a>
Setup a behavior for when receiving group conference push notification.

        public static void SetIncomingVoiceChatBehavior(IncomingVoiceChatBehavior incomingVoiceChatBehavior)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|incomingVoiceChatBehavior| [IncomingVoiceChatBehavior](#FASConference.IncomingVoiceChatBehavior) |Behavior for when receiving push notification about group conference.|

### <a name ="FASConference.GetIncomingVoiceChatBehavior">FASConference.GetIncomingVoiceChatBehavior</a>
Get set upped behavior for when receiving group conference push notification.

        public static IncomingVoiceChatBehavior GetIncomingVoiceChatBehavior()

#### Return
|Type|Description|
|------|-----|
|[IncomingVoiceChatBehavior](#FASConference.IncomingVoiceChatBehavior)| Behavior for when receiving push notification about group conference.|


### <a name ="FASConference.GetConferenceRole">FASConference.GetConferenceRole</a>
Get role for group conference.

        public static ConferenceRole GetConferenceRole()

#### Return
|Type|Description|
|------|-----|
|[ConferenceRole](#FASConference.ConferenceRole)| Role in conference |


### <a name ="FASConference.GetGroupConferenceParticipants">FASConference.GetGroupConferenceParticipants</a>
Get participants of group conference.

        public static void GetGroupConferenceParticipants(string groupId, Action<IList<GroupConferenceParticipant>, ListMeta, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|groupId| string|Group ID|
|callback| Action\<IList\<GroupConferenceParticipant>, ListMeta, Error>|Delegate to be called after the process of getting participants in group conference is completed.|


### <a name ="FASConference.GetCurrentConference">FASConference.GetCurrentConference</a>
Get the current participated group conference.

        public static void GetCurrentConference(string groupId, Action<GroupConference, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|groupId| string|Group ID|
|callback| Action\<GroupConference, Error>|Delegate to be called after the process of getting group conference.|
