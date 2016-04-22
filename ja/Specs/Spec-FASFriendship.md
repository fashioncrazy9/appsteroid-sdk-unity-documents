# FASFriendship Specifications

last update at 2014/10/29

----------

## Introduction

## <a name ="FASFriendship">FASFriendship Class</a>
フレンドに関連する操作をするクラスです。

----------

## Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASFriendship](#FASFriendship)|フレンドに関連する操作をするクラス|

----------

### Methods

|Name|内容|
|------|-----|
|[FASFriendship.GetAccountFriendList](#FASFriendship.GetAccountFriendList)| ログイン中のユーザーのフレンド一覧を取得します |
|[FASFriendship.GetUserFriendList](#FASFriendship.GetUserFriendList)| ユーザーのフレンド一覧を取得します |
|[FASFriendship.SendFriendshipRequest](#FASFriendship.SendFriendshipRequest)| フレンドリクエストを送信します |
|[FASFriendship.AcceptFriendshipRequest](#FASFriendship.AcceptFriendshipRequest)| フレンドリクエストを許可します |
|[FASFriendship.HideFriendshipRequest](#FASFriendship.HideFriendshipRequest)| フレンドリクエストを隠します |
|[FASFriendship.GetFriendshipRequestingUsersList](#FASFriendship.GetFriendshipRequestingUsersList)| フレンドリクエスト送信中のユーザー一覧を取得します |
|[FASFriendship.GetFriendshipRequestedUsersList](#FASFriendship.GetFriendshipRequestedUsersList)| フレンドリクエスト受信中のユーザー一覧を取得します |
|[FASFriendship.GetHiddenFriendshipRequestedUsersList](#FASFriendship.GetHiddenFriendshipRequestedUsersList)| 隠したフレンドリクエスト一覧を取得します |
|[FASFriendship.UnFriend](#FASFriendship.UnFriend)| フレンド状態を解除します |

----------

### <a name ="FASFriendship.GetAccountFriendList">FASFriendship.GetAccountFriendList</a>

ログイン中のユーザーのフレンド一覧を取得します。

    public static void GetAccountFriendList(Action<IList<Friend>, ListMeta, Error> callback)
    public static void GetAccountFriendList(uint page, Action<IList<Friend>, ListMeta, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|page| uint |（オプション）ページ番号（未指定の場合は最新ページを取得）|
|callback| Action\<IList\<Friend>, ListMeta, Error>|フレンド一覧取得処理完了時に、Friend モデルリスト、メタ情報、エラー情報を引数に呼び出されるデリゲート|

----------

### <a name ="FASFriendship.GetUserFriendList">FASFriendship.GetUserFriendList</a>

ユーザーのフレンド一覧を取得します。

    public static void GetUserFriendList(string userId, Action<IList<Friend>, ListMeta, Error> callback)
    public static void GetUserFriendList(string userId, uint page, Action<IList<Friend>, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|page| uint |（オプション）ページ番号（未指定の場合は最新ページを取得）|
|callback| Action\<IList\<Friend>, ListMeta, Error>|フレンド一覧取得処理完了時に、Friend モデルリスト、メタ情報、エラー情報を引数に呼び出されるデリゲート|

----------
### <a name ="FASFriendship.SendFriendshipRequest">FASFriendship.SendFriendshipRequest</a>

フレンドリクエストを送信します。

    public static void SendFriendshipRequest(string userId, Action<FriendshipRequest, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|userId| string |　フレンドリクエストを送信するユーザーID|
|callback| Action\<FriendshipRequest, Error>|フレンドリクエスト送信処理完了時に、FriendshipRequest、エラー情報を引数に呼び出されるデリゲート|

----------
### <a name ="FASFriendship.AcceptFriendshipRequest">FASFriendship.AcceptFriendshipRequest</a>

フレンドリクエストを許可します。

    public static void AcceptFriendshipRequest(string userId, Action<FriendshipRequest, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|userId| string |　フレンドリクエストを許可するユーザーID|
|callback| Action\<FriendshipRequest, Error>|フレンドリクエスト許可処理完了時に、FriendshipRequest、エラー情報を引数に呼び出されるデリゲート|

----------
### <a name ="FASFriendship.HideFriendshipRequest">FASFriendship.HideFriendshipRequest</a>

フレンドリクエストを隠します。

    public static void HideFriendshipRequest(string userId, Action<FriendshipRequest, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|userId| string |　フレンドリクエストを隠すユーザーID|
|callback| Action\<FriendshipRequest, Error>|フレンドを隠す処理完了時に、FriendshipRequest、エラー情報を引数に呼び出されるデリゲート|

----------
### <a name ="FASFriendship.GetFriendshipRequestingUsersList">FASFriendship.GetFriendshipRequestingUsersList</a>

フレンドリクエスト送信中のユーザー一覧を取得します。

    public static void GetFriendshipRequestingUsersList(string userId, Action<IList<Friend>, ListMeta, Error> callback)
    public static void GetFriendshipRequestingUsersList(string userId, uint page, Action<IList<Friend>, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|userId| string |　フレンドリクエスト送信中のユーザー一覧を取得するユーザーID|
|page| uint |（オプション）ページ番号（未指定の場合は最新ページを取得）|
|callback| Action\<IList\<Friend>, ListMeta, Error>|ユーザー一覧取得処理完了時に、Friend モデルリスト、メタ情報、エラー情報を引数に呼び出されるデリゲート|

----------
### <a name ="FASFriendship.GetFriendshipRequestedUsersList">FASFriendship.GetFriendshipRequestedUsersList</a>

フレンドリクエスト受信中のユーザー一覧を取得します。

    public static void GetFriendshipRequestedUsersList(string userId, Action<IList<Friend>, ListMeta, Error> callback)
    public static void GetFriendshipRequestedUsersList(string userId, uint page, Action<IList<Friend>, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|userId| string |　フレンドリクエスト受信中のユーザー一覧を取得するユーザーID|
|page| uint |（オプション）ページ番号（未指定の場合は最新ページを取得）|
|callback| Action\<IList\<Friend>, ListMeta, Error>|ユーザー一覧取得処理完了時に、Friend モデルリスト、メタ情報、エラー情報を引数に呼び出されるデリゲート|

----------
### <a name ="FASFriendship.GetHiddenFriendshipRequestedUsersList">FASFriendship.GetHiddenFriendshipRequestedUsersList</a>

隠したフレンドリクエスト一覧を取得します

    public static void GetHiddenFriendshipRequestedUsersList(uint page, Action<IList<Friend>, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|page| uint |ページ番号|
|callback| Action\<IList\<Friend>, ListMeta, Error>|ユーザー一覧取得処理完了時に、Friend モデルリスト、メタ情報、エラー情報を引数に呼び出されるデリゲート|

----------
### <a name ="FASFriendship.UnFriend">FASFriendship.UnFriend</a>

フレンド状態を解除します。

    public static void UnFriend(string userId, Action<Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|userId| string |　フレンド状態を解除するユーザーID|
|callback|  Action\<Error>|フレンド状態解除処理完了時にエラー情報を引数に呼び出されるデリゲート|
