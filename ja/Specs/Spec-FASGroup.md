# FASGroup Specifications

last update at 2014/10/15

----------

## Introduction

## <a name ="FASGroup">FASGroup Class</a>
グループに関連する操作をするクラスです。

----------

## Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASGroup](#FASGroup)|グループに関連する操作をするクラス|

----------

### Methods

|Name|内容|
|------|-----|
|[FASGroup.CreateGroup](#FASGroup.CreateGroup)| グループを作成する |
|[FASGroup.GetGroupList](#FASGroup.GetGroupList)| グループ一覧を取得する |
|[FASGroup.GetGroup](#FASGroup.GetGroup)| グループを取得する |
|[FASGroup.EditGroup](#FASGroup.EditGroup)| グループ名を編集する |
|[FASGroup.DeleteGroup](#FASGroup.DeleteGroup)| グループ名を削除する |
|[FASGroup.Subscribe](#FASGroup.Subscribe)| グループのメッセージの通知を受ける |
|[FASGroup.Unsubscribe](#FASGroup.Unsubscribe)| グループのメッセージの通知を解除する|
|[FASGroup.GetGroupMemberList](#FASGroup.GetGroupMemberList)| グループのメンバー一覧を取得する|
|[FASGroup.AddMember](#FASGroup.AddMember)| グループにメンバーを追加する|
|[FASGroup.DeleteMember](#FASGroup.DeleteMember)| グループからメンバーを削除する|
|[FASGroup.CreatePair](#FASGroup.CreatePair)| ペアグループを作成する|
|[FASGroup.SendGroupMessage](#FASGroup.SendGroupMessage)| グループメッセージを送信する|
|[FASGroup.GetGroupMessageList](#FASGroup.GetGroupMessageList)| グループメッセージ一覧を取得する|
|[FASGroup.SendGroupMessageInGames](#FASGroup.SendGroupMessageInGames)| インゲームチャットのテキストを送信する|

### <a name ="FASGroup.CreateGroup">FASGroup.CreateGroup</a>

グループを作成します。

    public static void CreateGroup(Action<Group, Error> callback)
    public static void CreateGroup(string name, Action<Group, Error> callback)
    public static void CreateGroup(string[] userIds, Action<Group, Error> callback
    public static void CreateGroup(string name, string[] userIds, Action<Group, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|name|string|（オプション）グループ名|
|userIds|string[] |（オプション）グループに加えるユーザーIDの配列|
|callback| Action\<Rank, Error>|グループ作成処理完了時に、Group モデル、エラー情報を引数に呼び出されるデリゲート|


### <a name ="FASGroup.GetGroupList">FASGroup.GetGroupList</a>

グループ一覧を取得します。

    public static void GetGroupList(Action<IList<Group>, Error> callback)
    public static void GetGroupList(uint page, Action<IList<Group>, Error> callback)
    public static void GetGroupList(Action<IList<Group>, ListListMeta, Error> callback)
    public static void GetGroupList(uint page, Action<IList<Group>, ListMeta, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|page| uint |（オプション）ページ番号|
|callback| Action\<IList\<Group>|グループ一覧取得処理完了時に、Group モデルのリスト、エラー情報を引数に呼び出されるデリゲート|
|callback| Action\<IList\<Group>, ListMeta, Error>|グループ一覧取得処理完了時に、Group モデルのリスト、リストのメタ情報、エラー情報を引数に呼び出されるデリゲート|


### <a name ="FASGroup.GetGroup">FASGroup.GetGroup</a>

グループを取得します。

    public static void GetGroup(string groupId, Action<Group, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|groupId| string |グループID|
|callback| Action\<Group, Error>|グループ取得処理完了時に、Group モデル、エラー情報を引数に呼び出されるデリゲート|


### <a name ="FASGroup.EditGroup">FASGroup.EditGroup</a>

グループを取得します。

    public static void EditGroup(string groupId, string name, Action<Group, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|groupId| string |グループID|
|name| string |グループ名|
|callback| Action\<Group, Error>|グループ編集処理完了時に、Group モデル、エラー情報を引数に呼び出されるデリゲート|

### <a name ="FASGroup.DeleteGroup">FASGroup.DeleteGroup</a>

グループを削除します。

    public static void DeleteGroup(string groupId, Action<Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|groupId| string |グループID|
|callback| Action\<Error>|グループ削除処理完了時に、Group モデル、エラー情報を引数に呼び出されるデリゲート|


### <a name ="FASGroup.Subscribe">FASGroup.Subscribe</a>

グループのメッセージの通知を受ける設定をします。

    public static void Subscribe(string groupId, Action<Group, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|groupId| string |グループID|
|callback| Action\<Group, Error>|グループのメッセージの通知設定処理完了時に、Group モデル、エラー情報を引数に呼び出されるデリゲート|


### <a name ="FASGroup.Unsubscribe">FASGroup.Unsubscribe</a>

グループのメッセージの通知を解除します。

    public static void Unsubscribe(string groupId, Action<Group, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|groupId| string |グループID|
|callback| Action\<Group, Error>|グループのメッセージの通知解除処理完了時に、Group モデル、エラー情報を引数に呼び出されるデリゲート|


### <a name ="FASGroup.GetGroupMemberList">FASGroup.GetGroupMemberList</a>

グループのメンバー一覧を取得します。

    public static void GetGroupMemberList(string groupId, Action<IList<Member>, Error> callback)
    public static void GetGroupMemberList(string groupId, Action<IList<Member>, ListMeta, Error> callback)
    public static void GetGroupMemberList(string groupId, uint page, Action<IList<Member>, Error> callback)
    public static void GetGroupMemberList(string groupId, uint page, Action<IList<Member>, ListMeta, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|groupId| string |グループID|
|callback| Action\<IList\<Member>, Error>|グループメンバー取得処理完了時に、Group モデルの一覧、エラー情報を引数に呼び出されるデリゲート|
|callback| Action\<IList\<Member>, ListMeta, Error>|グループメンバー取得処理完了時に、Group モデルの一覧、リストのメタ情報、エラー情報を引数に呼び出されるデリゲート|


### <a name ="FASGroup.AddMember">FASGroup.AddMember</a>

グループにメンバーを追加します。

    public static void AddMember(string groupId, string userId, Action<Member, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|groupId| string |グループID|
|userId| string |ユーザーID|
|callback| Action\<Member, Error>|グループメンバー追加処理完了時に、Member モデル、エラー情報を引数に呼び出されるデリゲート|


### <a name ="FASGroup.DeleteMember">FASGroup.DeleteMember</a>

グループからメンバーを削除します。

    public static void DeleteMember(string groupId, string userId, Action<Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|groupId| string |グループID|
|userId| string |ユーザーID|
|callback| Action\<Error>|グループメンバー削除処理完了時に、エラー情報を引数に呼び出されるデリゲート|


### <a name ="FASGroup.CreatePair">FASGroup.CreatePair</a>

ペアグループを作成します。

    public static void CreatePair(string userId, Action<Group, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|userId| string |ユーザーID|
|callback| Action\<Group, Error>|ペアグループ作成処理完了時に、Group モデル、エラー情報を引数に呼び出されるデリゲート|


### <a name ="FASGroup.SendGroupMessage">FASGroup.SendGroupMessage</a>

グループメッセージを送信します。

    public static void SendGroupMessage(string groupId, string text, Action<GroupMessage, Error> callback)
    public static void SendGroupMessage(string groupId, Texture2D clipImage, Action<GroupMessage, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|groupId| string |グループID|
|text| string |メッセージテキスト|
|clipImage| Texture2D |添付画像|
|callback| Action\<GroupMessage, Error>|グループメッセージ送信処理完了時に、GroupMessage モデル、エラー情報を引数に呼び出されるデリゲート|


### <a name ="FASGroup.GetGroupMessageList">FASGroup.GetGroupMessageList</a>

グループメッセージ一覧を取得します。

    public static void GetGroupMessageList(string groupId, Action<IList<GroupMessage>, Error> callback)
    public static void GetGroupMessageList(string groupId, Action<IList<GroupMessage>, ListMeta, Error> callback)
    public static void GetGroupMessageList(string groupId, uint page, Action<IList<GroupMessage>, Error> callback)
    public static void GetGroupMessageList(string groupId, uint page, Action<IList<GroupMessage>, ListMeta, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|groupId| string |グループID|
|page| uint |（オプション）ページ番号（未指定の場合は最新ページを取得）|
|callback| Action\<IList\<GroupMessage>|グループメッセージ一覧取得処理完了時に、GroupMessage モデルリスト、エラー情報を引数に呼び出されるデリゲート|
|callback| Action\<IList\<GroupMessage>, ListMeta, Error>|グループメッセージ一覧取得処理完了時に、GroupMessage モデルリスト、メタ情報、エラー情報を引数に呼び出されるデリゲート|


### <a name ="FASGroup.SendGroupMessageInGames">FASGroup.SendGroupMessageInGames</a>

インゲームチャットのテキストを送信します。

    public static void SendGroupMessageInGames(string groupId, string text, Action<GroupMessage, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|groupId| string |グループID|
|text| string |送信するテキスト|
|callback| Action\<GroupMessage, Error> |インゲームチャット送信処理完了時に、GroupMessage 、エラー情報を引数に呼び出されるデリゲート|
