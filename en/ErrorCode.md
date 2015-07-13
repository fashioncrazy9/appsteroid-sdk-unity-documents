## Error Class

If an error occurs in an FAS method, the error class of the Fresvii.AppSteroid.Models namespace will be returned in the relevant delegate.
The error codes are defined below, followed by the descriptions of the properties.

### Properties
|Type|Name|Description|
|---|---|---|
|int|Code|Error code (int value of ErrorCode)|
|string|Detail|Error detail|
|Method|ToString()|Error string|

### Fields

#### enum ErrorCode

|Name|Value|Description|
|-----|-----|-----|
|Unknown|-1|Unknown error|
|NotInitialized|1|Happens when the FAS was not initialized|
|NotLogIn|2|Happens when calling the API without logging in|
|InvalidJson|3|Invalid JSON is returned from the server|
|UnableToRegisterNotification|4|Failed to register push notification|
|NetworkNotReachable|5|Can not connect to the Network|
|InvalidTypeOfKeyValueStore|6|Happens when trying to save an invalid type to key value store|
|AccessingLoacalDatabaseFailed|7|Failed to access local database of key value store|
|AndroidNotificationRegisterTokenIsNotReady|8|Happens when trying to register push notification token for Android without completing the process to get that token|
|InitializingGroupConferenceFailed|9|Failed to initialize group conference|
|CreatingVoiceChatEngineFailed|10|Failed to create voice chat engine for group conference|
|InvalidParameters|11|Happens when accessing API with an invalid parameter|
|WWWTimeOut|12|WWW access time out|
|TextTooLong|13|Setting up a too long text for API|
|TooManyGroupMember|14|Happens when creating a group with over 100 user|
|ProvisioningSettingIsInvalid|15|Invalid APNS settings|
|OtherSignUpProcessIsRunning|16|Other signup process is running|
|OtherLoginProcessIsRunning|17|Other login process is running|
|GoogleLoginFailed|18|Failed to login to google when uploading a content to Youtube|
|YoutubeUploadingFailed|19|Failed to upload to Youtube|
|NotAuthorized|100|Access token is not authorized|
|CannotCancelMatch|202|Failed to cancel match request|
|Banned|204|User are banned and do not have access|
|Unauthorized|401|Unauthorized User (Is not logged in)|
|NameHasAlredyBeenTaken|402|User name has already been taken (When signing up or changing user name)|