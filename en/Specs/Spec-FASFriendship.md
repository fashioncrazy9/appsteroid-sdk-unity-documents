# FASFriendship Specifications

last update at 2014/10/29

----------

## Introduction

## <a name ="FASFriendship">FASFriendship Class</a>
Class to operate function related to Friend management.

----------

## Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASFriendship](#FASFriendship)|Class to operate function related to Friend management. |

----------

### Methods

|Name|Description|
|------|-----|
|[FASFriendship.GetAccountFriendList](#FASFriendship.GetAccountFriendList)| Get friend list of logged in user |
|[FASFriendship.GetUserFriendList](#FASFriendship.GetUserFriendList)| Get users friend list |
|[FASFriendship.SendFriendshipRequest](#FASFriendship.SendFriendshipRequest)| Send friend request |
|[FASFriendship.AcceptFriendshipRequest](#FASFriendship.AcceptFriendshipRequest)| Accept Friend request |
|[FASFriendship.HideFriendshipRequest](#FASFriendship.HideFriendshipRequest)| Hide Friend request |
|[FASFriendship.GetFriendshipRequestingUsersList](#FASFriendship.GetFriendshipRequestingUsersList)| Get list of users sending friend request |
|[FASFriendship.GetFriendshipRequestedUsersList](#FASFriendship.GetFriendshipRequestedUsersList)| Get list of users receiving friend request |
|[FASFriendship.GetHiddenFriendshipRequestedUsersList](#FASFriendship.GetHiddenFriendshipRequestedUsersList)| Get list of hidden friend request |
|[FASFriendship.UnFriend](#FASFriendship.UnFriend)| Unfriend a friendship |

----------

### <a name ="FASFriendship.GetAccountFriendList">FASFriendship.GetAccountFriendList</a>

Get friend list of logged in user.

    public static void GetAccountFriendList(Action<IList<Friend>, ListMeta, Error> callback)
    public static void GetAccountFriendList(uint page, Action<IList<Friend>, ListMeta, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|page| uint |(Optional) Page number (It will get the latest page when no values are selected)|
|callback| Action\<IList\<Friend>, ListMeta, Error>|This is a Delegate with an argument of Friend model list, meta info and error info that will be called when the process to get friend list is completed.|

----------

### <a name ="FASFriendship.GetUserFriendList">FASFriendship.GetUserFriendList</a>

Get users friend list

    public static void GetUserFriendList(string userId, Action<IList<Friend>, ListMeta, Error> callback)
    public static void GetUserFriendList(string userId, uint page, Action<IList<Friend>, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|page| uint |(Optional) Page number (It will get the latest page when no values are selected)|
|callback| Action\<IList\<Friend>, ListMeta, Error>|This is a Delegate with an argument of Friend model list, meta info and error info that will be called when the process to get friend list is completed.|

----------
### <a name ="FASFriendship.SendFriendshipRequest">FASFriendship.SendFriendshipRequest</a>

Send friend request

    public static void SendFriendshipRequest(string userId, Action<FriendshipRequest, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|userId| string | User ID to send friend request|
|callback| Action\<FriendshipRequest, Error>|This is a Delegate with an argument of FriendshipRequest and error info that will be called when the process to send a FriendRequest is completed.|

----------
### <a name ="FASFriendship.AcceptFriendshipRequest">FASFriendship.AcceptFriendshipRequest</a>

Accept Friend Request

    public static void AcceptFriendshipRequest(string userId, Action<FriendshipRequest, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|userId| string |　User ID to accept the friend request|
|callback| Action\<FriendshipRequest, Error>|This is a Delegate with an argument of FriendshipRequest and error info that will be called when the process to accept a FriendRequest is completed.|

----------
### <a name ="FASFriendship.HideFriendshipRequest">FASFriendship.HideFriendshipRequest</a>

Hide Friend Request

    public static void HideFriendshipRequest(string userId, Action<FriendshipRequest, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|userId| string |　User ID to hide the friend request|
|callback| Action\<FriendshipRequest, Error>|This is a Delegate with an argument of FriendshipRequest and error info that will be called when the process to hide a FriendRequest is completed.|

----------
### <a name ="FASFriendship.GetFriendshipRequestingUsersList">FASFriendship.GetFriendshipRequestingUsersList</a>

Get list of users sending friend request

    public static void GetFriendshipRequestingUsersList(string userId, Action<IList<Friend>, ListMeta, Error> callback)
    public static void GetFriendshipRequestingUsersList(string userId, uint page, Action<IList<Friend>, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|userId| string |　User ID to get the list of users sending a friend request.|
|page| uint |(Optional) Page number (It will get the latest page when no values are selected)|
|callback| Action\<IList\<Friend>, ListMeta, Error>|This is a Delegate with an argument of Friend model list, meta info and error info that will be called when the process to get friend list is completed.|

----------
### <a name ="FASFriendship.GetFriendshipRequestedUsersList">FASFriendship.GetFriendshipRequestedUsersList</a>

Get list of users receiving friend request

    public static void GetFriendshipRequestedUsersList(string userId, Action<IList<Friend>, ListMeta, Error> callback)
    public static void GetFriendshipRequestedUsersList(string userId, uint page, Action<IList<Friend>, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|userId| string |　User ID to get the list of users receiving a friend request.|
|page| uint |(Optional) Page number (It will get the latest page when no values are selected)|
|callback| Action\<IList\<Friend>, ListMeta, Error>|This is a Delegate with an argument of Friend model list, meta info and error info that will be called when the process to get friend list is completed.|

----------
### <a name ="FASFriendship.UnFriend">FASFriendship.UnFriend</a>

Unfriend a friendship

    public static void UnFriend(string userId, Action<Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|userId| string |　User ID to unfriend a frinedship|
|callback|  Action\<Error>|This is a Delegate with an argument of error info that will be called when the process of unfriending is completed.|
