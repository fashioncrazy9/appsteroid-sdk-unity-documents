# FASNotification Specifications

last update at 2014/10/29

----------

## Introduction

Specification for PushNotification settings.

----------

## Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASNotification](#FASNotificationClass)|Class to operate PushNotification settings.|

----------

## <a name ="FASNotificationClass">FASNotification Class</a>

PushNotification Settings

### Methods

|Name|Description|
|------|-----|
|[FASNotification.RegisterRemoteNotification](#FASNotification.RegisterRemoteNotification)| Register PushNotification |
|[FASNotification.UnregisterRemoteNotification](#FASNotification.UnregisterRemoteNotification)| Unregister PushNotification |

-----------------
### <a name ="FASNotification.RegisterRemoteNotification">FASNotification.RegisterRemoteNotification</a>
Register PushNotification

    public static void RegisterRemoteNotification(Action<Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|callback| Action\<Error\> |Delegate to be called after the process|

#### Example

  FASNotification.RegisterRemoteNotification((error)=>
  {
    if (error != null)
    {
      Debug.LogError(error.ToString());
    }
    else
    {
      Debug.Log("Success to register notification");
    }
  });

-----------------
### <a name ="FASNotification.UnregisterRemoteNotification">FASNotification.UnregisterRemoteNotification</a>
Unregister PushNotification

    public static void UnregisterRemoteNotification(Action<Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|callback| Action\<Error\> |Delegate to be called after the process|

#### Example

  FASNotification.UnregisterRemoteNotification((error)=>
  {
    if (error != null)
    {
      Debug.LogError(error.ToString());
    }
    else
    {
      Debug.Log("Success to unregister notification");
    }
  });
