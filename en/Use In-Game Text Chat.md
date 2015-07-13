# About In-Game Text Chat

## Introduction
In-game text chat is a solution to have realtime communication with another player during game play. In-game text chat can be implemented using group message.

## Steps and Sample

#### Preparation
* To use functions provided by AppSteroid, follow the document [GetStarted](GetStarted.md) and complete the initial setup.
* Group message will function through push message, so please complete the settings referring to these documents [iOS]([Unity-iOS]Setting Up PushNotification.md)/[Android]([Unity-Android]Setting Up PushNotification.md) as well.

#### Receive Group Message
1. Register an event that triggers when a group message is created.
2. process group message creation event.

##### Sample Code

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


#### Send Group Message

##### Sample Code

  {
    // send group message
    FASGroup.SendGroupMessageInGames(groupId, "chat text", (groupMessage, error)=>
    {
      if (error != null) // transition error
      {
        Debug.LogError(error.ToString());
      }
      else // transition success
      {
        Debug.Log(groupMessage.Text);
      }
    });
  }
