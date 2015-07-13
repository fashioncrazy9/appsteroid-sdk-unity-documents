# FASCustomMessage Specifications

last update at 2014/10/15

----------

## Introduction

## <a name ="FASCustomMessage">FASCustomMessage Class</a>
カスタムメッセージの操作に関するクラスです。カスタムメッセージはカスタマイズされたメッセージをプッシュ通知で送受信する機能です。

----------

## Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASCustomMessage](#FASCustomMessage)|グループカンファレンス（ボイスチャット）の操作に関するクラス|

----------

### Methods

|Name|内容|
|------|-----|
|[FASCustomMessage.SendCustomMessage](#FASCustomMessage.SendCustomMessage)| カスタムメッセージを送信します。|
|[FASCustomMessage.GetCustomMessageList](#FASCustomMessage.GetCustomMessageList)| カスタムメッセージ一覧を取得します。|

-----------------
### <a name ="FASCustomMessage.SendCustomMessage">FASCustomMessage.SendCustomMessage</a>
カスタムメッセージを送信します。

    public static void SendCustomMessage(string channelName, string action, Action<CustomMessage, Error> callback)
    public static void SendCustomMessage(string channelName, string action, string channelParams, string parameters, string subject, string sound, bool apnsEnabled, bool gcmEnabled, Action<CustomMessage, Error> callback)


#### Parameters
|Name|Type|内容|
|------|------|-----|
|channelName|string|送信先チャネル名|
|action| string |アクション名 [a-zA-Z]のみ使用可能|
|channelParams|string| [optional] チャネルのクエリに指定したバインド変数の値をJSON形式で指定する|
|parameters|string|[optional] Pushメッセージのカスタムデータ部をJSON形式で指定する|
|subject|string|[optional]Pushメッセージの件名。iOSではalert, androidではtilteパラメータとなる, 未指定の場合は非表示|
|sound|string|[optional] Pushメッセージのサウンドファイル名, 未指定の場合は無音|
|apnsEnabled|bool|[optional] iOS端末へのPush配信をおこなうか。(true:行う、false:行わない、デフォルト: true)|
|gcmEnabled|bool|[optional] Android端末へのPush配信をおこなうか。(true:行う、false:行わない、デフォルト: true)|
|callback|Action<CustomMessage, Error>|カスタムメッセージ送信処理完了後、CutomMessage と Error を引数に呼び出されるデリゲート|

-----------------
### <a name ="FASCustomMessage.GetCustomMessageList">FASCustomMessage.GetCustomMessageList</a>
カスタムメッセージ一覧を取得します。

    public static void GetCustomMessageList(Action<IList<CustomMessage>, ListListMeta, Error> callback)
    public static void GetCustomMessageList(uint? page, System.DateTime startTime, Action<IList<CustomMessage>, ListListMeta, Error> callback)


#### Parameters
|Name|Type|内容|
|------|------|-----|
|page|uint?| [optional] 取得するページ番号|
|startTime|System.DateTime| [optional] メッセージ作成日時、指定日時以降に作成されたメッセージを取得|
|callback|Action<IList<CustomMessage>, ListListMeta, Error>|カスタムメッセージ一覧取得処理完了時に、CustomMessage 一覧とListListMeta情報、Errorを引数に呼び出されるデリゲート|
