# FASMatchMaking Specifications

last update at 2015/07/07

----------

## Introduction

マッチメイキングの機能に関する仕様書です。
一緒にゲームを行いたいユーザーを探すことが出来ます。
また、AppSteroidが提供するマッチメイキングのGUIも表示することが出来ます。
詳しい利用方法に関しては[マッチメイキングの利用方法](../マッチメイキングの利用方法.md)を参照してください。

---

## Sequence

#### マッチメイク開始時（一般対戦）
![MatchMaking1](../Images/diagram_match_making_start.png)

- 1.1 ユーザによる新規マッチメイクリクエストの作成
- 1.2 リクエストの作成結果レスポンス Matchのstatus: FASMatchStatusWating
- 2.1 他のユーザによる新規マッチメイクリクエストの作成
- 3.1 (参加できるマッチが存在する場合) マッチに参加
- 3.2 (参加者がマッチの最大人数に達した場合) マッチが完了
- 2.2 リクエストの作成結果レスポンス Matchのstatus: FASMatchStatusComplete
- 4 マッチの参加者全員にマッチの完了イベントを通知
- 5.1 最新のマッチ招待情報を取得
- 5.2 マッチ詳細のレスポンス

#### マッチメイク開始時（招待による友人対戦）
![MatchMaking2](../Images/diagram_match_making_invitation.png)

- 1.1 ユーザによる新規マッチメイクリクエストの作成
- 1.2 リクエストの作成結果レスポンス Matchのstatus: FASMatchStatusInviting
- 2. 被招待者にマッチメイク招待イベントを通知
- 3.1 招待の承認
- 3.2 (参加者がマッチの最大人数に達した場合) マッチが完了
- 4 マッチの参加者全員にマッチの完了イベントを通知
- 5.1 最新のマッチ招待情報を取得
- 5.2 マッチ詳細のレスポンス

![MatchMaking3](../Images/diagram_match_making_end.png)

- 1.1 不要になったマッチの破棄
- 1.2 マッチ破棄の結果レスポンス Matchのstatus: FASMatchStatusDisposed


## <a name ="FASMatchMaking">FASMatchMaking Class</a>
マッチメイキングに関連する操作をするクラスです。


----------

## Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASMatchMaking](#FASMatchMaking)|マッチメイキングに関連する操作をするクラス|

----------

### Methods

|Name|内容|
|------|-----|
|[FASMatchMaking.CreateMatchMakingRequest](#FASMatchMaking.CreateMatchMakingRequest)| マッチメイクリクエストを作成します。 |
|[FASMatchMaking.CancelMatchMakingRequest](#FASMatchMaking.CancelMatchMakingRequest)| マッチメイクリクエストをキャンセルします。 |
|[FASMatchMaking.GetMatchMakingRequest](#FASMatchMaking.GetMatchMakingRequest)| マッチリクエストを取得します。 |
|[FASMatchMaking.AcceptMatchMakingInvitation](#FASMatchMaking.AcceptMatchMakingInvitation)| マッチリクエストの招待を受理します。 |
|[FASMatchMaking.GetMatch](#FASMatchMaking.GetMatch)| マッチを取得します。 |
|[FASMatchMaking.GetMatchList](#FASMatchMaking.GetMatchList)| マッチ一覧を取得します。 |
|[FASMatchMaking.JoinMatch](#FASMatchMaking.JoinMatch)| マッチに参加します。 |
|[FASMatchMaking.GetGameContext](#FASMatchMaking.GetGameContext)| ゲームコンテクストを取得します。 |
|[FASMatchMaking.UpdateGameContext](#FASMatchMaking.UpdateGameContext)| ゲームコンテクストを更新（新規作成）します。 |
|[FASMatchMaking.DisposeMatch](#FASMatchMaking.DisposeMatch)| マッチを破棄します。 |
|[FASMatchMaking.SetMatchMakingTimeOutSeconds](#FASMatchMaking.SetMatchMakingTimeOutSeconds)| マッチメイキングのタイムアウト秒数を設定します。（デフォルト３０秒） |

### <a name ="FASMatchMaking.CreateMatchMakingRequest">FASMatchMaking.CreateMatchMakingRequest</a>

マッチメイクリクエストを作成します。

マッチメイキングタイムアウトの設定秒後、マッチが最少参加人数に達している場合はマッチを成立させます。
マッチ成立時は、FASEvent.OnMatchMakingMatchCompleted イベントが発火します。
マッチ不成立時は、マッチリクエストがキャンセルされます。

    public static void CreateMatchMakingRequest(Action<MatchMakingRequest, Error> callback)
    public static void CreateMatchMakingRequest(uint? minNumberOfPlaysers, Action<MatchMakingRequest, Error> callback)
    public static void CreateMatchMakingRequest(string[] inviteUsers, Action<MatchMakingRequest, Error> callback)
    public static void CreateMatchMakingRequest(string invitationMessage, Action<MatchMakingRequest, Error> callback)
    public static void CreateMatchMakingRequest(string invitationMessage, string segment, Action<MatchMakingRequest, Error> callback)
    public static void CreateMatchMakingRequest(string[] inviteUsers, string invitationMessage, Action<MatchMakingRequest, Error> callback)
    public static void CreateMatchMakingRequest(string[] inviteUsers, string invitationMessage, string segment, Action<MatchMakingRequest, Error> callback)
    public static void CreateMatchMakingRequest(uint? minNumberOfPlaysers, string[] inviteUsers, string invitationMessage, string segment, Action<MatchMakingRequest, Error> callback)
    public static void CreateMatchMakingRequest(uint? minNumberOfPlaysers, uint? maxNumberOfPlaysers, string[] inviteUsers, string invitationMessage, string segment, Action<MatchMakingRequest, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|callback|Action<MatchMakingRequest, Error>|マッチメイキングリクエスト送信完了時に MatchMakingRequest, Error を引数に呼び出されるデリゲート|
|minNumberOfPlaysers|uint?|（オプション）最小参加者数 [2 - 16] 省略時: 2|
|maxNumberOfPlaysers|uint?|（オプション）最大参加者数 [2 - 16] 省略時: min_number_of_playersと同じ|
|inviteUsers|string[]|（オプション）招待するユーザのIDリスト|
|invitationMessage|string|（オプション）招待メッセージ|
|segment|string|（オプション）マッチ区分|

### <a name ="FASMatchMaking.CancelMatchMakingRequest">FASMatchMaking.CancelMatchMakingRequest</a>

マッチメイクリクエストをキャンセルします。

    public static void CancelMatchMakingRequest(string requestId, Action<Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|requestId|string|キャンセルするマッチメイキングリクエストID|
|callback|Action<Error>|マッチメイキングリクエストキャンセル送信完了時に Error を引数に呼び出されるデリゲート|

### <a name ="FASMatchMaking.GetMatchMakingRequest">FASMatchMaking.GetMatchMakingRequest</a>

マッチリクエストを取得します。

    public static void GetMatchMakingRequest(Action<MatchMakingRequest, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|callback|Action<MatchMakingRequest, Error>|マッチメイキングリクエスト取得処理完了時に MatchMakingRequest, Error を引数に呼び出されるデリゲート|


### <a name ="FASMatchMaking.AcceptMatchMakingInvitation">FASMatchMaking.AcceptMatchMakingInvitation</a>

マッチリクエストの招待を受理します。

    public static void AcceptMatchMakingInvitation(string requestId, Action<MatchMakingRequest, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|requestId|string|受理するマッチリクエストID|
|callback|Action<MatchMakingRequest, Error>|マッチリクエストの招待を受理処理完了時に MatchMakingRequest, Error を引数に呼び出されるデリゲート|

### <a name ="FASMatchMaking.GetMatch">FASMatchMaking.GetMatch</a>

指定したIDのマッチを取得します。

    public static void GetMatch(string matchId, Action<Match, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|matchId|string|マッチID|
|callback|Action<Match, Error> |マッチ取得処理完了時に Match, Error を引数に呼び出されるデリゲート|


### <a name ="FASMatchMaking.GetMatchList">FASMatchMaking.GetMatchList</a>

マッチ一覧を取得します。

    public static void GetMatchList(Action<IList<Match>, Error> callback)
    public static void GetMatchList(uint page, Action<IList<Match>, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|page|uint|（オプション）ページ|
|callback|Action<Match, Error> |マッチ一覧取得処理完了時に IList<Match>, Error を引数に呼び出されるデリゲート|


### <a name ="FASMatchMaking.JoinMatch">FASMatchMaking.JoinMatch</a>

マッチに参加します。

    public static void JoinMatch(string matchId, Action<MatchMakingRequest, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|matchId|string|参加するマッチID|
|callback|Action<MatchMakingRequest, Error> |マッチ参加処理完了時に MatchMakingRequest, Error を引数に呼び出されるデリゲート|


### <a name ="FASMatchMaking.GetGameContext">FASMatchMaking.GetGameContext</a>

ゲームコンテクストを取得します。

    public static void GetGameContext(string matchId, Action<GameContext, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|matchId|string|マッチID|
|callback|Action<GameContext, Error> |ゲームコンテクスト取得完了時に GameContext, Error を引数に呼び出されるデリゲート|



### <a name ="FASMatchMaking.UpdateGameContext">FASMatchMaking.UpdateGameContext</a>

ゲームコンテクストを更新（最新ゲームコンテクストを作成）します。

    public static void UpdateGameContext(string matchId, string json, uint updatedCount, Action<GameContext, Error> callback)
    public static void UpdateGameContext(string matchId, string json, string nextPlayerId, Action<GameContext, Error> callback)
    public static void UpdateGameContext(string matchId, string json, Action<GameContext, Error> callback)
    public static void UpdateGameContext(string matchId, string json, string nextPlayerId, uint? updatedCount, Action<GameContext, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|matchId|string|マッチID|
|json|string|ゲームコンテキストのJSON形式。root要素はオブジェクト|
|nextPlayerId|string|（オプション）次のユーザーID|
|updatedCount|uint?|（オプション）更新カウント|
|callback|Action<GameContext, Error>|ゲームコンテクスト更新完了時に GameContext, Error を引数に呼び出されるデリゲート|
