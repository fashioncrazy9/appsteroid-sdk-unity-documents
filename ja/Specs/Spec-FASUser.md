# FASUser Specifications

----------

## Introduction

ユーザー設定に関する機能の仕様書です。

----------

## Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASUser](#FASUserClass)|ユーザー設定に関するクラス|

----------

## <a name ="FASUserClass">FASUser Class</a>

ユーザー設定に関するクラスです。

### Methods

|Name|内容|
|------|-----|
|[FASUser.SignUp](#FASUser.SignUp)| アプリに紐付けられたユーザが作成される |
|[FASUser.LogIn](#FASUser.LogIn)| サインアップで作成したユーザで何らかの操作をするための Session Token を返す |
|[FASUser.LogOut](#FASUser.LogOut)| ログアウトする |
|[FASUser.LoadSignedUpUsers](#FASUser.LoadSignedUpUsers)|サインアップ済みのユーザー一覧を取得する|
|[FASUser.GetSnsAccountList](#FASUser.GetSnsAccountList)| ユーザに登録されている SNS 認証情報一覧を取得する |
|[FASUser.SetSnsAccount](#FASUser.SetSnsAccount)| SNS 認証で得られた SNS 内でユーザを識別するための uid と SNS サービス名をサインインユーザと結びつけて保存する |
|[FASUser.DeleteSnsAccount](#FASUser.DeleteSnsAccount)| id で指定した、SNS 認証情報を削除する |
|[FASUser.GetAccount](#FASUser.GetAccount)|サインインしているユーザ情報を取得する |
|[FASUser.PatchAccount](#FASUser.PatchAccount)| サインインしているユーザ情報を設定する |
|[FASUser.GetUser](#FASUser.GetUser)| id で指定した、ユーザ情報を取得する |
|[FASUser.GetUserList](#FASUser.GetUserList)| 条件で指定したユーザ一覧を取得する |

-----------------
### <a name ="FASUser.SignUp">FASUser.SignUp</a>
アプリに紐付けられたユーザが作成されます。結果は、User,　Error を引数としたコールバックで返します。 作成されたユーザーIDは暗号化してローカルストレージに保存されます。

    public static void SignUp(string userName, Action<User, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|userName|string|サインアップするユーザーネーム。ユーザーネームがない場合は null を設定する|
|description|string|サインアップするユーザーのプロフィール文。コメントがない場合は、null を設定する|
|profileImage|Texture2D|サインアップするユーザー画像。画像がない場合は、 null を設定する|
|callback|Action<User, Error>|サインアップ処理後に呼び出されるデリゲート|

#### Errors
|Fresvii.AppSteroid.Models.Error.ErrorCode|内容|
|------|------|-----|
|NameHasAlredyBeenTaken|サインアップ時にすでにユーザー名が利用されている場合のエラーコード|


#### Examples

    FASUser.SignUp(”username”, "description",  profileImage,  (user, error)=>
    {
        if (error != null)
        {
            Debug.LogError(error.ToString());
        }
        else
        {       
            Debug.Log(user.name + ", " + user.friend_code + ", " + user.id + ", " + user.created_at + ", " + user.updated_at);
        }
    });

-----------------
### <a name ="FASUser.LogIn">FASUser.LogIn</a>
サインアップで作成したユーザで何らかの操作をするための Session Token を取得します。 取得したアクセストークンはSDKの内部にて保持されます。処理結果は、Error を引数としたコールバックで返します。

    public static void LogIn(string userId, string userToken, Action<Error> callback)
    public static void LogIn(string userId, string userToken, int lifeTime, Action<Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|userId|string|ログインするユーザーID|
|userToken|string|ログインするユーザートークン|
|lifeTime|int|（オプション）アクセストークンの有効時間（秒）。指定なしの場合はデフォルト値が適用される。|
|callback|Action\<Error\> |サインイン処理後に呼び出されるデリゲート|

#### Example

    FASUser.LogIn((error)=>
    {
        if (error != null)
        {
            Debug.LogError(error.ToString());
        }            
    });

-----------------
### <a name ="FASUser.LogOut">FASUser.LogOut</a>
ログアウトします。

    public static void LogOut()

#### Example

    FASUser.LogOut();
    
-----------------
### <a name ="FASUser.LoadSignedUpUsers">FASUser.LoadSignedUpUsers</a>
サインアップ済みのユーザー一覧を取得します。端末にはIDとトークンのみ保存されています。

    public static List<User> LoadSignedUpUsers()

#### Example
    List<User> users = FASUser.LoadSignedUpUsers();
    
    if (users.Count > 0)
    {
        currentUser = users[users.Count - 1];
    }

-----------------
### <a name ="FASUser.GetSnsAccountList">FASUser.GetSnsAccountList</a>
ユーザに登録されている SNS 認証情報一覧を取得します。結果は、SnsAccount の IList,　Error を引数としたコールバックで返します。

    public static void GetSnsAccountList(Action<IList<SnsAccount>, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|callback|Action<IList<SnsAccount>, Error> |SNS 認証情報一覧を取得後に呼び出されるデリゲート|
|lifeTime|int|アクセストークンの有効時間（秒）。指定なしの場合はデフォルト値が適用される。|

#### Example

    FASUser.GetSnsAccountList(snsAccountList, error)=>
    {
        if (error != null)
        {
            Debug.LogError(error.ToString());
        }
    });

-----------------
### <a name ="FASUser.SetSnsAccount">FASUser.SetSnsAccount</a>
SNS 認証で得られた SNS 内でユーザを識別するための uid と SNS サービス名をサインインユーザと結びつけて保存します。結果は、SnsAccount,　Error を引数としたコールバックで返します。

    public static void SetSnsAccount(string uid, string provider, Action<SnsAccount, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|uid|string|SNS内でユーザを識別するためのID|
|provider|string|プロバイダ文字列。"facebook", "twitter" など。|
|accessToken|string|サービスプロバイダのアクセストークン|
|callback|Action<SnsAccount, Error>|処理後に呼び出されるデリゲート|

#### Example
    FASUser.SetSnsAccount("1111", "facebook", "abcdefghijklmn", (snsAccount, error)=>
    {
        if (error != null)
        {
            Debug.LogError(error.ToString());
        }    
    });

-----------------
### <a name ="FASUser.DeleteSnsAccount">FASUser.DeleteSnsAccount </a>
id で指定した、SNS 認証情報を削除します。結果は、Error を引数としたコールバックで返します。

    public static void DeleteSnsAccount(string id, Action<Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|id|string|SNS内でユーザを識別するためのID|
|callback|Action\<Error\>|処理後に呼び出されるデリゲート|

#### Example
    FASUser.SetSnsAccount("1111", "facebook", (error)=>
    {
        if (error != null)
        {
            Debug.LogError(error.ToString());
        }
        else
        {        
            Debug.Log("Delete Success");
        }
    });

-----------------
### <a name ="FASUser.GetAccount">FASUser.GetAccount</a>
サインインしているユーザ情報を取得します。結果は、User,　Error を引数としたコールバックで返します。

    public static void GetAccount(Action<User, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|callback|Action\<Error\>|取得後に呼び出されるデリゲート|

#### Example

    FASUser.GetAccount((user, error)=>
    {
        if (error != null)
        {
            Debug.LogError(logMessage);
        }
        else
        {        
            Debug.Log(user.Name + ", " + user.FriendCode + ", " + user.Id + ", " + user.CreatedAt + ", " + user.UpdatedAt);
        }
    });

-----------------
### <a name ="FASUser.PatchAccount">FASUser.PatchAccount</a>
サインインしているユーザの名前、プロフィール画像を設定します。結果は、User,　Error を引数としたコールバックで返します。

    public static void PatchAccount(string name,　Action<User, Error> callback)
    public static void PatchAccount(Texture2D profileImage,　Action<User, Error> callback)
    public static void PatchAccount(string name,　Texture2D profileImage, Action<User, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|callback|Action\<Error\>|設定後に呼び出されるデリゲート|

#### Errors
|Fresvii.AppSteroid.Models.Error.ErrorCode|内容|
|------|------|-----|
|NameHasAlredyBeenTaken|すでにユーザー名が利用されている場合のエラーコード|

#### Example

    FASUser.PatchAccount("username",　profileImage, (user, error)=>
    {
         if (error != null)
        {
            Debug.LogError(logMessage);
        }
        else
        {        
            Debug.Log(user.Name + ", " + user.FriendCode + ", " + user.Id + ", " + user.CreatedAt + ", " + user.UpdatedAt);
        }
    });

-----------------
### <a name ="FASUser.GetUser">FASUser.GetUser</a>
id で指定した、ユーザ情報を取得します。結果は、User,　Error を引数としたコールバックで返します。

    public static void GetUser(string id, Action<User, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|id|string|SNS内でユーザを識別するためのID|
|callback|Action\<Error\>|取得後に呼び出されるデリゲート|

#### Example

    FASUser.GetUser(userId, (user, error)=>
    {
        if (error != null)
        {
            Debug.LogError(logMessage);
        }
        else
        {        
            Debug.Log(user.Name + ", " + user.FriendCode + ", " + user.Id + ", " + user.CreatedAt + ", " + user.UpdatedAt);
        }
    });


-----------------
### <a name ="FASUser.GetUserList">FASUser.GetUserList</a>
条件で指定したユーザ一覧を取得します。 結果は、User の IList,　Error を引数としたコールバックで返します。

    public static void GetUserList(string uid, string provider, Action<IList<User>, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|uid|string|SNS内でユーザを識別するためのID|
|provider|string|プロバイダ文字列。"facebook", "twitter" など。|
|callback| Action<IList<User>, Error> |処理後に呼び出されるデリゲート|

#### Example

    FASUser.GetUser(userId, (users, error)=>
    {
        if (error != null)
        {
            Debug.LogError(error.ToString());
        }
        else
        {
            foreach (User user in users)
            {
                Debug.Log(user.Name + ", " + user.FriendCode + ", " + user.Id + ", " + user.CreatedAt + ", " + user.UpdatedAt);
            }
        }
    });
