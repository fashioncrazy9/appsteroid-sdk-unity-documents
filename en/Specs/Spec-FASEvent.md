# AppSteroid for Unity

last update at 2014/10/15

----------

##  Introduction

## <a name ="FASEventClass">FASEvent Class</a>
Class to receive event caused by PushNotification. Add a event to receive a notification.

----------

##  Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASEvent](#FASEventClass)|Class to receive events that occurred through PushNotification |

----------

### Events
||Type|Name|Description|
|---|---|---|---|
|public static event| Action\<Comment>| OnForumCommentCreated |Call Comment model as an argument when a comment was posted on a subscribed thread.|
|public static event| Action\<Thread>| OnForumOfficialThreadCreated |Call Thread model as an argument when an official user created a new thread.|
|public static event| Action\<GroupMessage>| OnGroupMessageImageCreated |Call GroupMessage model as an argument when an image was posted on a group message.|
|public static event| Action\<GroupMessage>| OnGroupMessageTextCreated |Call GroupMessage model as an argument when a text group message was created.|
|public static event| Action\<GroupMessage>| OnGroupMessageInGameCreated |Call GroupMessage model as an argument when a in-game chat message was created.|
|public static event| Action\<DirectMessage>| OnDirectMessageCreated |Call DirectMessage model as an argument when a DirectMessage was created.|
|public static event| Action\<User>| OnFriendshipRequestCreated |Call User model as an argument when a friendship request was created.|
|public static event| Action\<User>| OnFriendshipRequestUpdated |Call User model as an argument when a friendship request was updated.|
|public static event| Action\<GameContext>| OnMatchMakingGameContextCreated |Call GameContext as an argument when a game context for matchmaking was updated or created.|
|public static event| Action\<GroupConference>| OnGroupConferenceCreated |Call GroupConference model as an argument when a GroupConference was created.|
|public static event| Action\<GroupConferenceParticipant>| OnGroupConferenceParticipantCreated |Call GroupConferenceParticipant a model as an argument when a participant for group conference was created.|

#### Example

    void OnEnable()
    {
    FASEvent.OnGroupMessageInGameCreated += OnGroupMessageInGameCreated;
    }
    
    void OnDisable()
    {
    FASEvent.OnGroupMessageInGameCreated -= OnGroupMessageInGameCreated;
    }
    
    void OnGroupMessageInGameCreated(GroupMessage groupMessage)
    {
            // Execute evenet process
    }
