# FASCustomMessage Specifications

Last update at 2014/10/15

----------

##  Introduction

## <a name ="FASCustomMessage">FASCustomMessage Class</a>
Class to operate custom message.

----------

##  Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASCustomMessage](#FASCustomMessage)|Class to operate custom message |

----------

### Methods

|Name|Description|
|------|-----|
|[FASCustomMessage.SendCustomMessage](#FASCustomMessage.SendCustomMessage)| Send custom message|
|[FASCustomMessage.GetCustomMessageList](#FASCustomMessage.GetCustomMessageList)| Get custom message list|

-----------------
### <a name ="FASCustomMessage.SendCustomMessage">FASCustomMessage.SendCustomMessage</a>
Send custom message.

  public static void SendCustomMessage(string channelName, string action, Action<CustomMessage, Error> callback)
  public static void SendCustomMessage(string channelName, string action, string channelParams, string parameters, string subject, string sound, bool apnsEnabled, bool gcmEnabled, Action<CustomMessage, Error> callback)


#### Parameters
|Name|Type|Description|
|------|------|-----|
|channelName|string|Destination channel name|
|action| string |Action name. Only [a-zA-Z] are available |
|channelParams|string| [optional] Specify the bind variable value in JSON format, which is specified in the query under channel.|
|parameters|string|[optional] Specify push message's custom data in JSON format.|
|subject|string|[optional]Subject name of Push message. Alert in iOS, title parameter in android. It will not appear when noting is selected.|
|sound|string|[optional] Sound file name for Push message. It will be silent when noting is selected.|
|apnsEnabled|bool|[optional] Whether to deliver push notification to iOS devices or not. (true:deliver, false:Don't deliver, Default: true)|
|gcmEnabled|bool|[optional] Whether to deliver push notification to Android devices or not. (true:deliver, false:Don't deliver, Default: true)|
|callback|Action<CustomMessage, Error>|Delegate to be called after process of sending custom message is completed. The delegate contains CustomMessage and Error as an argument.|

-----------------
### <a name ="FASCustomMessage.GetCustomMessageList">FASCustomMessage.GetCustomMessageList</a>
Get list of custom message

  public static void GetCustomMessageList(Action<IList<CustomMessage>, ListListMeta, Error> callback)
  public static void GetCustomMessageList(uint? page, System.DateTime startTime, Action<IList<CustomMessage>, ListListMeta, Error> callback)


#### Parameters
|Name|Type|Description|
|------|------|-----|
|page|uint?| [optional] Page number to get|
|startTime|System.DateTime| [optional] Get messages that were added after the selected data and time. |
|callback|Action<IList<CustomMessage>, ListListMeta, Error>|Delegate to be called after the process of getting list of custom message. The delegate contains CustomMessage list, ListMeta information and Error as an argument.|
