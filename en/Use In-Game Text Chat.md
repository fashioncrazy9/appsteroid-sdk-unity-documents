# About In-Game Text Chat

## Introduction
In-game text chat is a solution to have realtime communication with another player during game play. In-game text chat can be implemented using group message.
In-game chat can be used within the game, or text balloon from a character. Therefore, AppSteroid do not provide any GUI for in-game chat. 
To use the chat GUI provided by AppSteroid, please use the AppSteroid group message GUI.

## Steps and Sample

### Preparation
* To use functions provided by AppSteroid, follow the document [GetStarted](GetStarted.md) and complete the initial setup.
* Group message will function through push message, so please complete the settings referring to these documents [iOS]([Unity-iOS]Setting Up PushNotification.md)/[Android]([Unity-Android]Setting Up PushNotification.md) as well.

### Steps to Implement In-game Text Chat

1. Get a group ID to use in in-game text chat
2. Send a group message with in-game chat
3. Receive group message with in-game chat

## 1. Get a Group ID to Use in In-game Text Chat
Use [Get Group API](Specs/Spec-FASGroup.md#FASGroup.GetGroupList) to get group list. Select a group from the list to use in in-game chat.

## 2. Send a Group Message with In-game Chat

Use the [Send group message API](Specs/Spec-FASGroup.md#FASGroup.SendGroupMessageInGames) to send group message with in-game chat.

### Sample Code

    // Sending group message
    FASGroup.SendGroupMessageInGames(groupId, "chat text", (groupMessage, error)=>
    {
        if (error != null) // error
        {
            Debug.LogError(error.ToString());
        }
        else // success
        {
            Debug.Log(groupMessage.Text);
        }
    });

## 3. Receive Group Message with In-game Chat

Handle the reception of group message with [Reception Event](Specs/Spec-FASEvent.md#fasevent-specifications).
Steps to handle the reception of in-game chat is;

1. Register an event that triggers when a group message is created.
2. Process group message creation event.

##### Sample Code

In this sample code, a method `OnGroupMessageInGameCreated` is registered to output the log to the console when an event occurs.

  void OnEnable()
  {
    // enable group message creation event
    FASEvent.OnGroupMessageInGameCreated += OnGroupMessageInGameCreated;
  }

  void OnDisable()
  {
    // disable group message creation event
    FASEvent.OnGroupMessageInGameCreated -= OnGroupMessageInGameCreated;
  }

  // call group message model as an argument when creating new group message
  void OnGroupMessageInGameCreated(GroupMessage groupMessage)
  {
    Debug.Log("In Game chat : " + groupMessage.User.Name + " : " + groupMessage.Text);
  }
