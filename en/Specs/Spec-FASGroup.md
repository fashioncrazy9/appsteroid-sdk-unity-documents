# FASGroup Specifications

last update at 2014/10/15

----------

## Introduction

## <a name ="FASGroupClass">FASGroup Class</a>
Class to operate Group functions

----------

## Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASGroup](#FASGroupClass)|Class to operate group |

----------

### Methods

|Name|Description|
|------|-----|
|[FASGroup.CreateGroup](#FASGroup.CreateGroup)| Create a group |
|[FASGroup.GetGroupList](#FASGroup.GetGroupList)| Get list of group |
|[FASGroup.GetGroup](#FASGroup.GetGroup)| Get group |
|[FASGroup.EditGroup](#FASGroup.EditGroup)| Edit group name |
|[FASGroup.DeleteGroup](#FASGroup.DeleteGroup)| Delete group name |
|[FASGroup.Subscribe](#FASGroup.Subscribe)| Subscribe to a group to receive notification about group message |
|[FASGroup.Unsubscribe](#FASGroup.Unsubscribe)| Unsubscribe from a group to cancel receiving notification about the group |
|[FASGroup.GetGroupMemberList](#FASGroup.GetGroupMemberList)| Get member list of a group |
|[FASGroup.AddMember](#FASGroup.AddMember)| Add member to a group |
|[FASGroup.DeleteMember](#FASGroup.DeleteMember)| Delete member from a group |
|[FASGroup.CreatePair](#FASGroup.CreatePair)| Create pair group |
|[FASGroup.SendGroupMessage](#FASGroup.SendGroupMessage)| Send group message |
|[FASGroup.GetGroupMessageList](#FASGroup.GetGroupMessageList)| Get list of group message |
|[FASGroup.SendGroupMessageInGames](#FASGroup.SendGroupMessageInGames)| Send text for in-game chat |

### <a name ="FASGroup.CreateGroup">FASGroup.CreateGroup</a>

Create a group

  public static void CreateGroup(Action<Group, Error> callback)
  public static void CreateGroup(string name, Action<Group, Error> callback)
  public static void CreateGroup(string[] userIds, Action<Group, Error> callback
  public static void CreateGroup(string name, string[] userIds, Action<Group, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|name|string| (Optional) Group name|
|userIds|string[] | (Optional) User Id array of a user to be added to the group|
|callback| Action\<Rank, Error>|Delegate to be called when a process to create group is completed. This delegate contains Group model and error information as an argument.|


### <a name ="FASGroup.GetGroupList">FASGroup.GetGroupList</a>

Get list of group

  public static void GetGroupList(Action<IList<Group>, Error> callback)
  public static void GetGroupList(uint page, Action<IList<Group>, Error> callback)
  public static void GetGroupList(Action<IList<Group>, ListListMeta, Error> callback)
  public static void GetGroupList(uint page, Action<IList<Group>, ListMeta, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|page| uint | (optional) page number|
|callback| Action\<IList\<Group>|Delegate to be called when a process to get group list is completed. This delegate contains Group model list and error information as an argument.|
|callback| Action\<IList\<Group>, ListMeta, Error>|Delegate to be called when a process to get list is completed. This delegate contains Group model list, meta info about the list and error information as an argument.|


### <a name ="FASGroup.GetGroup">FASGroup.GetGroup</a>

Get Group

  public static void GetGroup(string groupId, Action<Group, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|groupId| string |Group ID|
|callback| Action\<Group, Error>|Delegate to be called when a process to get a group is completed. This delegate contains Group model and error information as an argument.|


### <a name ="FASGroup.EditGroup">FASGroup.EditGroup</a>

Edit Group name

  public static void EditGroup(string groupId, string name, Action<Group, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|groupId| string |Group ID|
|name| string |Group name|
|callback| Action\<Group, Error>|Delegate to be called when a process to edit group is completed. This delegate contains Group model and error information as an argument.|

### <a name ="FASGroup.DeleteGroup">FASGroup.DeleteGroup</a>

Delete a group

  public static void DeleteGroup(string groupId, Action<Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|groupId| string |Group ID|
|callback| Action\<Error>|Delegate to be called when a process to delete group is completed. This delegate contains Group model and error information as an argument.|


### <a name ="FASGroup.Subscribe">FASGroup.Subscribe</a>

Subscribe to a group to receive notification about group message.

  public static void Subscribe(string groupId, Action<Group, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|groupId| string |Group ID|
|callback| Action\<Group, Error>|Delegate to be called when a process, subscribing to a group is completed. This delegate contains Group model and error information as an argument.|


### <a name ="FASGroup.Unsubscribe">FASGroup.Unsubscribe</a>

Unsubscribe from a group to cancel receiving notification about the group.

  public static void Unsubscribe(string groupId, Action<Group, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|groupId| string |Group ID|
|callback| Action\<Group, Error>|Delegate to be called when a process, unsubscribing from a group is completed. This delegate contains Group model and error information as an argument.|


### <a name ="FASGroup.GetGroupMemberList">FASGroup.GetGroupMemberList</a>

Get member list of a group

  public static void GetGroupMemberList(string groupId, Action<IList<Member>, Error> callback)
  public static void GetGroupMemberList(string groupId, Action<IList<Member>, ListMeta, Error> callback)
  public static void GetGroupMemberList(string groupId, uint page, Action<IList<Member>, Error> callback)
  public static void GetGroupMemberList(string groupId, uint page, Action<IList<Member>, ListMeta, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|groupId| string |Group ID|
|callback| Action\<IList\<Member>, Error>|Delegate to be called when a process to get group member is completed. This delegate contains Group model list and error information as an argument. |
|callback| Action\<IList\<Member>, ListMeta, Error>|Delegate to be called when a process to get group member is completed. This delegate contains Group model list, meta information about the list and error information as an argument.|


### <a name ="FASGroup.AddMember">FASGroup.AddMember</a>

Add member to a group

  public static void AddMember(string groupId, string userId, Action<Member, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|groupId| string |Group ID|
|userId| string |User ID|
|callback| Action\<Member, Error>|Delegate to be called when a process, adding a member to a group is completed. This delegate contains Member model and error information as an argument.|


### <a name ="FASGroup.DeleteMember">FASGroup.DeleteMember</a>

Delete member from a group

  public static void DeleteMember(string groupId, string userId, Action<Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|groupId| string |Group ID|
|userId| string |User ID|
|callback| Action\<Error>|Delegate to be called when a process, deleting a member from a group is completed. This delegate contains error information as an argument.|


### <a name ="FASGroup.CreatePair">FASGroup.CreatePair</a>

Create pair group

  public static void CreatePair(string userId, Action<Group, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|userId| string |User ID|
|callback| Action\<Group, Error>|Delegate to be called when a process, creating a pair group is completed. This delegate contains Group model and error information as an argument.|


### <a name ="FASGroup.SendGroupMessage">FASGroup.SendGroupMessage</a>

Send group message

  public static void SendGroupMessage(string groupId, string text, Action<GroupMessage, Error> callback)
  public static void SendGroupMessage(string groupId, Texture2D clipImage, Action<GroupMessage, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|groupId| string |Group ID|
|text| string |text message|
|clipImage| Texture2D |Clip image|
|callback| Action\<GroupMessage, Error>|Delegate to be called when a process to send group message is completed. This delegate contains GroupMessage model and error information as an argument.|


### <a name ="FASGroup.GetGroupMessageList">FASGroup.GetGroupMessageList</a>

Get list of group message.

  public static void GetGroupMessageList(string groupId, Action<IList<GroupMessage>, Error> callback)
  public static void GetGroupMessageList(string groupId, Action<IList<GroupMessage>, ListMeta, Error> callback)
  public static void GetGroupMessageList(string groupId, uint page, Action<IList<GroupMessage>, Error> callback)
  public static void GetGroupMessageList(string groupId, uint page, Action<IList<GroupMessage>, ListMeta, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|groupId| string |Group ID|
|page| uint |(Optional) Page number (It will get the latest page when no specific page was selected).|
|callback| Action\<IList\<GroupMessage>|Delegate to be called when a process to get GroupMessage list is completed. This delegate contains GroupMessage model list and error information as an argument.|
|callback| Action\<IList\<GroupMessage>, ListMeta, Error>|Delegate to be called when a process to get GroupMessage list is completed. This delegate contains GroupMessage model list, meta information and error information as an argument.|


### <a name ="FASGroup.SendGroupMessageInGames">FASGroup.SendGroupMessageInGames</a>

Send text for in-game chat.

  public static void SendGroupMessageInGames(string groupId, string text, Action<GroupMessage, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|groupId| string |Group ID|
|text| string |Text to be send|
|callback| Action\<GroupMessage, Error> |Delegate to be called when a process to send in-game chat is completed. This delegate contains GroupMessage and error information as an argument.|
