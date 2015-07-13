# FASNotification Specifications

last update at 2014/10/29

----------

## Introduction

プッシュ通知設定に関する仕様書です。

----------

## Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASNotification](#FASNotificationClass)|プッシュ通知設定操作に関するクラス|

----------

## <a name ="FASNotificationClass">FASNotification Class</a>

プッシュ通知設定に関する仕様書です。

### Methods

|Name|内容|
|------|-----|
|[FASNotification.RegisterRemoteNotification](#FASNotification.RegisterRemoteNotification)| プッシュ通知を設定する |
|[FASNotification.UnregisterRemoteNotification](#FASNotification.UnregisterRemoteNotification)| プッシュ通知を解除する |

-----------------
### <a name ="FASNotification.RegisterRemoteNotification">FASNotification.RegisterRemoteNotification</a>
プッシュ通知を設定する。

    public static void RegisterRemoteNotification(Action<Error> callback)
    public static void RegisterRemoteNotification(Action<NotificationRegistryInformation, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|callback| Action\<Error\> |処理後に呼び出されるデリゲート|

#### Example

    FASNotification.RegisterRemoteNotification((info, error)=>
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
プッシュ通知を解除する。

    public static void UnregisterRemoteNotification(Action<Error> callback)
    public static void UnregisterRemoteNotification(Action<NotificationRegistryInformation, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|callback| Action\<Error\> |処理後に呼び出されるデリゲート|

#### Example

    FASNotification.UnregisterRemoteNotification((info, error)=>
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
