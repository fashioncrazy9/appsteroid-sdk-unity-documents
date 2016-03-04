# FASUser Specifications

----------

## Introduction

Specification for handling functions related to User settings.

----------

## Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASUser](#FASUserClass)|Basic settings and user setting class|

----------

## <a name ="FASUserClass">FASUser Class</a>

Basic settings and user setting class

### Methods

|Name|Description|
|------|-----|
|[FASUser.SignUp](#FASUser.SignUp)| Sign up a user associated with the app |
|[FASUser.LogIn](#FASUser.LogIn)| Returns a session token necessary for the user created with SignUp to perform an operation |
|[FASUser.LogOut](#FASUser.LogOut)| Logout |
|[FASUser.LoadSignedUpUsers](#FASUser.LoadSignedUpUsers)|Gets the list of signed up users|
|[FASUser.GetSnsAccountList](#FASUser.GetSnsAccountList)| Gets the list of SNS authentication information registered for the user |
|[FASUser.SetSnsAccount](#FASUser.SetSnsAccount)| Save the uid, identifies users in the SNS, acquired through SNS authentication and SNS service name associating with signed in user |
|[FASUser.DeleteSnsAccount](#FASUser.DeleteSnsAccount)| Delete the SNS authentication information specified by the id |
|[FASUser.GetAccount](#FASUser.GetAccount)|Get the signed in users status |
|[FASUser.PatchAccount](#FASUser.PatchAccount)| Change the signed in users status |
|[FASUser.GetUser](#FASUser.GetUser)| Get the users status specified by id |
|[FASUser.GetUserList](#FASUser.GetUserList)| Get the user list specified by conditions |

-----------------
### <a name ="FASUser.SignUp">FASUser.SignUp</a>
Creates an user associated with the app. The result is returned by the callback with the arguments of User and Error. The created user ID is encrypted and saved in the local storage.
For the behavior of when an user name is not setup, or when an `userName` is `null` or empty, please check the "[name duplication](../DuplicatedUserName.md)" document.

    ```C#
    public static void SignUp(Action<User, Error> callback)
    public static void SignUp(string userName, Action<User, Error> callback)
    public static void SignUp(string userName, string description, Action<User, Error> callback)
    public static void SignUp(string userName, Texture2D profileImage, Action<User, Error> callback)
    public static void SignUp(string userName, string description, Texture2D profileImage, Action<User, Error> callback)
        

```

#### Parameters
|Name|Type|Description|
|------|------|-----|
|userName|string|(Optional) Name of the signup user. If there is no user name, set null. |
|description|string|(Optional) Profile of the signup user. If there is no comment, set null. |
|profileImage|Texture2D|(Optional) Image of the signup user. If there is no image, set null. |
|callback|Action<User, Error>|Delegate to be called after the signup process. |

#### Errors
|Fresvii.AppSteroid.Models.Error.ErrorCode|Description|
|------|------|-----|
|NameHasAlredyBeenTaken|User name has already been taken (When signing up or changing user name)|


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
Gets a session token necessary for the user created with SignUp to perform an operation. The acquired access token is retained in the SDK. The result is returned by the callback with the argument of Error.

    public static void LogIn(string userId, string userToken, Action<Error> callback)
    public static void LogIn(string userId, string userToken, int lifeTime, Action<Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|userId|string|User ID of who is going to login|
|userToken|string|User Token of who is going to login|
|lifeTime|int|Effective time for the access token (in seconds.) If this parameter is not specified, the default value applies.|
|callback|Action\<Error\> |Delegate to be called after the sign-in process|

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
Log out

    public static void LogOut()

#### Example

    FASUser.LogOut();
    
-----------------
### <a name ="FASUser.LoadSignedUpUsers">FASUser.LoadSignedUpUsers</a>
Gets the list of signed up users. Only ID and token are stored in the device.

    public static List<User> LoadSignedUpUsers()

#### Example
    List<User> users = FASUser.LoadSignedUpUsers();
    
    if (users.Count > 0)
    {
        currentUser = users[users.Count - 1];
    }

-----------------
### <a name ="FASUser.GetSnsAccountList">FASUser.GetSnsAccountList</a>
Get the list of SNS authentication information linked to each registered user. The result is returned by the callback with the arguments of IList of SnsAccount and Error.

     public static void GetSnsAccountList(Action<IList<SnsAccount>, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|callback|Action<IList<SnsAccount>, Error> |Delegate to be called after acquiring the SNS authentication information list|
|lifeTime|int|Effective time for the access token (in seconds.) If this parameter is not specified, the default value applies.|

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
Save the uid, identifies users in the SNS, acquired through SNS authentication and SNS service name associating with signed in user. The result is returned by the callback with the arguments of SnsAccount and Error.

    public static void SetSnsAccount(string uid, string provider, Action<SnsAccount, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|uid|string|ID to identify the user in SNS|
|provider|string|Provider string such as "Facebook" or "Twitter"|
|accessToken|string|Access token|
|callback|Action<SnsAccount, Error>|Delegate to be called after the process|

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
Delete the SNS authentication information specified by the id. The result is returned by the callback with the argument of Error.

    public static void DeleteSnsAccount(string id, Action<Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|id|string|ID to identify the user in SNS|
|callback|Action\<Error\>|Delegate to be called after process|

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
Get the signed in users status. The result is returned by the callback with the arguments of User and Error.

    public static void GetAccount(Action<User, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|callback|Action\<Error\>|Delegate to be called after acquisition|

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
Set up the name and profile image of the signed in user. The result is returned by the callback with the arguments of User and Error.
Please also check the "[duplicated user name](../DuplicatedUserName.md)" document.

    public static void PatchAccount(string name,　Action<User, Error> callback)
    public static void PatchAccount(Texture2D profileImage,　Action<User, Error> callback)
    public static void PatchAccount(string name,　Texture2D profileImage, Action<User, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|callback|Action\<Error\>|Delegate to be called after setting|

#### Errors
|Fresvii.AppSteroid.Models.Error.ErrorCode|Description|
|------|------|-----|
|NameHasAlredyBeenTaken|If the user name is already been taken|

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
Get the users status specified by id. The result is returned by the callback with the arguments of User and Error.

    public static void GetUser(string id, Action<User, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|id|string|ID to identify the user in SNS|
|callback|Action\<Error\>|Delegate to be called after acquisition|

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
Get the user list specified by conditions. The result is returned by the callback with the arguments of IList of User and Error.

    public static void GetUserList(string uid, string provider, Action<IList<User>, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|uid|string|ID to identify the user in SNS|
|provider|string|Provider string such as "Facebook" or "Twitter"|
|callback| Action<IList<User>, Error> |Delegate to be called after the process|

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
