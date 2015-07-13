# FASConference Specifications

last update at 2014/10/15

----------

## Introduction

## <a name ="FASConference">FASConference Class</a>
グループカンファレンス（ボイスチャット）に関する操作をするクラスです。

----------

## Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASConference](#FASClass)|グループカンファレンス（ボイスチャット）の操作に関するクラス|

----------

### Methods

|Name|内容|
|------|-----|
|[FASConference.StartConference](#FASConference.StartConference)| グループカンファレンスをホストとして開始します（ボイスチャットを発信）|
|[FASConference.JoinConference](#FASConference.JoinConference)| グループカンファレンスにゲストとして参加します（ボイスチャットを受信）|
|[FASConference.Leave](#FASConference.Leave)| グループカンファレンスから退席します（ボイスチャットを切断）|
|[FASConference.Mute](#FASConference.Mute)| マイクをミュートします |
|[FASConference.Unmute](#FASConference.Unmute)| マイクのミュートを解除します |
|[FASConference.Volume](#FASConference.Volume)| マイクとスピーカーの音量を設定します |
|[FASConference.GetConferenceElapsedTime](#FASConference.GetConferenceElapsedTime)|通話中のグループカンファレンスの経過時間を取得します。未通話では常に0を返します。|
|[FASConference.SetIncomingVoiceChatBehavior](#FASConference.SetIncomingVoiceChatBehavior)|グループカンファレンス開始プッシュ通知取得時の動作を設定します|
|[FASConference.GetIncomingVoiceChatBehavior](#FASConference.GetIncomingVoiceChatBehavior)|グループカンファレンス開始プッシュ通知取得時の動作設定を取得します|
|[FASConference.GetConferenceRole](#FASConference.GetConferenceRole)|グループカンファレンスの役割を取得します|
|[FASConference.GetGroupConferenceParticipants](#FASConference.GetGroupConferenceParticipants)|グループカンファレンスの参加者を取得します|
|[FASConference.GetCurrentConference](#FASConference.GetCurrentConference)|現在参加しているグループカンファレンスを取得します|

### Defines

#### <a name ="FASConference.ConferenceStates">enum ConferenceStates</a>
グループカンファレンスの状態

|Value|description|
|-----|-----|
|None|なし|
|Destroyed|カンファレンスが破棄された|
|Created|カンファレンスが作成された|

#### <a name ="FASConference.ConferenceRole">enum ConferenceRole</a>
グループカンファレンスにおけるユーザーの役割

|Value|description|
|-----|-----|
|None|なし|
|Host|ホスト|
|Guest|ゲスト|
|HostOrGuest|ホストまたはゲスト|

#### <a name ="FASConference.CallStates">enum CallStates</a>

グループカンファレンスのユーザーの応答状態

|Value|description|
|------|-----|
|Idle| 非通話状態|
|Progressing|通話開始処理中|
|Calling|発信中|
|Connected|通話中|
|Ending|終話処理中|

#### <a name ="FASConference.IncomingVoiceChatBehavior">enum IncomingVoiceChatBehavior</a>
グループカンファレンス作成プッシュ通知を受信したときの応答方法

|Value|description|
|-----|-----|
|Ask|確認ダイアログを表示してユーザーの応答を待ってカンファレンスへ接続する|
|AutoAccept|自動的にカンファレンスへ接続する|
|DoNothing|何もしない|

### Events
||Type|Name|Description|
|---|---|---|---|
|public static event| Action\<[ConferenceStates](#FASConference.ConferenceStates)>| OnConferenceStateChanged | ConferenceStates　が変化したときに呼び出されます |
|public static event| delegate void CallStateChangeDelegate(string groupId, string partnerId, [CallStates](#FASConference.CallStates) </a>callState) | OnCallStateChanged | CallStates　が変化したときに呼び出されます |
|public static event| Action\<Error>| OnError | エラー発生時に呼び出されます |


### <a name ="FASConference.StartConference">FASConference.StartConference</a>
グループカンファレンスをホストとして開始します（ボイスチャットを発信します）。

    public static void StartConference(string groupId, Action<Error> startConferenceCallback, Action<Error> createConferenceCallback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|groupId| string |グループカンファレンスを開始するグループID|
|startConferenceCallback| Action\<Error> |グループカンファレンス開始処理完了時にエラー情報を引数に呼び出されるデリゲート|
|createConferenceCallback| Action\<Error> |グループカンファレンス作成処理完了時にエラー情報を引数に呼び出されるデリゲート|

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
グループカンファレンスにゲストとして参加します（ボイスチャットを受信）。グループカンファレンス作成のプッシュ通知受信イベント(FASEvent.OnGroupConferenceCreated)をきっかけに、グループカンファレンスに参加します。

    public static void JoinConference(GroupConference groupConference, Action<Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|groupConference| GroupConference |参加する GroupConference モデル。FASEvent.OnGroupConferenceCreated イベントにより取得する。|
|callback| Action\<Error> |グループカンファレンス参加処理完了時にエラー情報を引数に呼び出されるデリゲート|

#### Example

    // 1. グループカンファレンス作成通知のイベントを登録
    
    {
        FASEvent.OnGroupConferenceCreated += OnGroupConferenceCreated;
    }
    
    // 2. グループカンファレンス作成通知イベントが発火
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
グループカンファレンスから退席します（ボイスチャットを切断します）。

    public static bool Leave()

#### Return
|Type|内容|
|------|-----|
| bool | 処理の成否（true:成功、false: エラー）|

### <a name ="FASConference.Mute">FASConference.Mute</a>
マイクをミュートします。

    public static bool Mute()

#### Return
|Type|内容|
|------|-----|
| bool | 処理の成否（true:成功、false: エラー）|

### <a name ="FASConference.Unmute">FASConference.Unmute</a>
マイクのミュートを解除します。

    public static bool Unmute()

#### Return
|Type|内容|
|------|-----|
| bool | 処理の成否（true:成功、false: エラー）|

### <a name ="FASConference.Volume">FASConference.Volume</a>
マイクとスピーカーのボリュームを設定します。設定値は、0.0（最小）~1.0（最大）のレンジです。

    public static bool Volume(float volumeMicrophone, float volumeSpeaker)

#### Return
|Type|内容|
|------|-----|
| bool | 処理の成否（true:成功、false: エラー）|

#### Parameters
|Name|Type|内容|
|------|------|-----|
|volumeMicrophone| float |マイクボリューム|
|volumeSpeaker|　float　|スピーカーボリューム|


### <a name ="FASConference.GetConferenceElapsedTime">FASConference.GetConferenceElapsedTime</a>
通話中のグループカンファレンスの経過時間を取得します。未通話では常に 0 を返します。

    public static long GetConferenceElapsedTime()

#### Return
|Type|内容|
|------|-----|
| long | 通話経過時間 (ms) |


### <a name ="FASConference.SetIncomingVoiceChatBehavior">FASConference.SetIncomingVoiceChatBehavior</a>
グループカンファレンス開始プッシュ通知取得時の動作を設定します

    public static void SetIncomingVoiceChatBehavior(IncomingVoiceChatBehavior incomingVoiceChatBehavior)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|incomingVoiceChatBehavior| [IncomingVoiceChatBehavior](#FASConference.IncomingVoiceChatBehavior) |グループカンファレンス開始プッシュ通知取得時の動作|

### <a name ="FASConference.GetIncomingVoiceChatBehavior">FASConference.GetIncomingVoiceChatBehavior</a>
グループカンファレンス開始プッシュ通知取得時の動作設定を取得します

    public static IncomingVoiceChatBehavior GetIncomingVoiceChatBehavior()

#### Return
|Type|内容|
|------|-----|
|[IncomingVoiceChatBehavior](#FASConference.IncomingVoiceChatBehavior)| グループカンファレンス開始プッシュ通知取得時の動作|


### <a name ="FASConference.GetConferenceRole">FASConference.GetConferenceRole</a>
グループカンファレンスの役割を取得します

    public static ConferenceRole GetConferenceRole()

#### Return
|Type|内容|
|------|-----|
|[ConferenceRole](#FASConference.ConferenceRole)| カンファレンスの役割|


### <a name ="FASConference.GetGroupConferenceParticipants">FASConference.GetGroupConferenceParticipants</a>
グループカンファレンスの参加者を取得します

    public static void GetGroupConferenceParticipants(string groupId, Action<IList<GroupConferenceParticipant>, ListMeta, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|groupId| string|グループID|
|callback| Action\<IList\<GroupConferenceParticipant>, ListMeta, Error>|グループカンファレンスの参加者を取得処理後に呼び出されるデリゲート|


### <a name ="FASConference.GetCurrentConference">FASConference.GetCurrentConference</a>
現在参加しているグループカンファレンスを取得します

    public static void GetCurrentConference(string groupId, Action<GroupConference, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|groupId| string|グループID|
|callback| Action\<GroupConference, Error>|グループカンファレンス取得処理後に呼び出されるデリゲート|
