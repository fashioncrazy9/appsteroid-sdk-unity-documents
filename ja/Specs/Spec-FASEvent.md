# FASEvent Specifications

last update at 2014/10/15

----------

## Introduction

## <a name ="FASEvent">FASEvent Class</a>
PushNotificationによるイベント発生を受け取るためのクラスです。イベントを登録して、通知を受け取ります。

----------

## Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASEvent](#FASEvent)|PushNotificationによるイベント発生を受け取るためのクラス|

----------

### Events
||Type|Name|Description|
|---|---|---|---|
|public static event| Action\<Comment>| OnForumCommentCreated |購読スレッドでコメントが作成されたときに Comment モデルを引数として呼び出されます。|
|public static event| Action\<Thread>| OnForumOfficialThreadCreated |オフィシャルユーザーがスレッドを作成したときに Thread モデルを引数として呼び出されます。|
|public static event| Action\<GroupMessage>| OnGroupMessageImageCreated |画像グループメッセージが作成されたときに GroupMessage モデルを引数として呼び出されます。|
|public static event| Action\<GroupMessage>| OnGroupMessageTextCreated |テキストグループメッセージが作成されたときに GroupMessage モデルを引数として呼び出されます。|
|public static event| Action\<GroupMessage>| OnGroupMessageInGameCreated |インゲームチャットのメッセージが作成されたときに GroupMessage モデルを引数として呼び出されます。|
|public static event| Action\<DirectMessage>| OnDirectMessageCreated |ダイレクトメッセージが作成されたときに DirectMessage モデルを引数として呼び出されます。|
|public static event| Action\<User>| OnFriendshipRequestCreated |フレンドシップリクエストが作成されたときに、 相手ユーザーモデルを引数として呼び出されます。|
|public static event| Action\<User>| OnFriendshipRequestUpdated |フレンドシップリクエストが更新されたときに、相手ユーザーモデルを引数として呼び出されます。|
|public static event| Action\<GameContext>| OnMatchMakingGameContextCreated |マッチメイクのゲームコンテクストが更新（作成）されたときに、GameContext を引数として呼び出されます。|
|public static event| Action\<GroupConference>| OnGroupConferenceCreated |グループカンファレンスが作成されたときに、GroupConferenceモデルを引数として呼び出されます。|
|public static event| Action\<GroupConferenceParticipant>| OnGroupConferenceParticipantCreated |グループカンファレンスの参加者が作成されたときに、GroupConferenceParticipant　モデルを引数として呼び出されます。|

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
        // イベントの処理を行う
    }
