# FASGui Specifications

last update at 2015/3/15

----------

## Introduction

## <a name ="FASGuiClass">FASGui Class</a>
Class to operate display GUI Scene. GUI will be load as a scene. Save the scene data before you call it during the game. Select the GUI to be displayed with an argument.

----------

## Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASGui](#FASGuiClass)|Fresvii GUI operation display class |

----------

### Defines
|Name|Type|Value|
|------|-----|-----|
|Mode|enum|Forum = (1 << 0), <br> Leaderboards = (1 << 1), <br> MyProfile = (1 << 2), <br> GroupMessage = (1 << 3), <br>MatchMaking = (1 << 4), <br> All = 0xFFFF

### Methods

|Name|Description|
|------|-----|
|[FASGui.ShowGUI](#FASGui.ShowGUI)| Method to Show GUI. Call this method and load GUI scene. To use this method, add "AppSteroidUI" to build setting. |
|[FASGui.ShowGUIWithLogin](#FASGui.ShowGUIWithLogin)| Process login with a specific user and show GUI. Call this method and than load the "AppSteroidUI" scene. To use this method, please add "AppSteroidUI" to build settings. |
|[FASGui.ShowMatchMakingGui](#FASGui.ShowMatchMakingGui)| Specify a matchmaking parameter to show GUI for matchmaking.|
|[FASGui.ShowMatchMakingGuiWithLogin](#FASGui.ShowMatchMakingGuiWithLogin)| Process logn with a specified user, specify matchmaking parameter and show matchmaking GUI.
|

### <a name ="FASGui.ShowGUI">FASGui.ShowGUI</a>

Load a scene to show GUI. If isModal = ture, the scene will be loaded in stead of transition.
If a user is not logged in, automatically login the last user and show GUI.

            public static void ShowGUI(FASGui.Mode guiMode = Mode.All, string returnSceneName = "", FASGui.Mode selectedMode = Mode.LastSelected, bool isModal = false, Action appSteroidModalGuiEnded = null)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|guiMode|FASGui.Mode|(Optional) Select from Forum, Leaderboards, MyProfile, GroupMessage or All. You can select multiple mode except for GroupMessage. |
|returnSceneName|string|(Optional) If isModal = true, no setting is required. A Scene name to return after closing GUI (When pressing app icon). When the scene to return is not selected, it will return to the root cause scene.|
|selectedMode|FASGui.Mode|(Optional) Select a specific tab to display first when you have selected a mode to show multiple GUIs.|
|isModal|bool|(Optional) Select whether to use modal or not. If isModal = false, execute scene transition to show  the GUI. If isModal = true, load the scene without executing scene transition. |
|appSteroidModalGuiEnded|Action|This is a callback which will be called after GUI loading end. Use to restrain game input from end-users when isModal = true.|

#### Example

##### Show with default setting
    FASGui.ShowGUI();

##### Use Modal
    FASGui.ShowGUI(isModal:true, appSteroidModalGuiEnded:() => { Debug.Log("AppSteroid GUI Done"); });


### <a name ="FASGui.ShowGUIWithLogin">FASGui.ShowGUIWithLogin</a>

Load the scene to show GUI with login.

        public static void ShowGUIWithLogin(string userId, string userToken, FASGui.Mode guiMode = Mode.All, string returnSceneName = "", FASGui.Mode selectedMode = Mode.MoreApps, bool isModal = false, Action appSteroidModalGuiEnded = null)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|userId|string|User ID, of a user who is going to login|
|userToken|string|User token, of a user who is going to login|
|modeMode|FASGui.Mode|(Optional) Select from Forum, Leaderboards, MyProfile, GroupMessage or All. Multiple GUI can be selected except GroupMessage and MatchMaking. |
|returnSceneName|string|(Optional) If isModal = true, no setting is required. A Scene name to return after closing GUI (When pressing app icon). When the scene to return is not selected, it will return to the root cause scene.|
|selectedMode|FASGui.Mode|(Optional) Select a specific tab to display first when you have selected a mode to show multiple GUIs.|
|isModal|bool|(Optional) Select whether to use modal or not. If isModal = false, execute scene transition to show  the GUI. If isModal = true, load the scene without executing scene transition. |
|appSteroidModalGuiEnded|Action|This is a callback which will be called after GUI loading end. Use to restrain game input from end-users when isModal = true.|

#### Example
	
	FASGui.ShowGUIWithLogin(userId, userToken);

---
### <a name ="FASGui.ShowMatchMakingGui">FASGui.ShowMatchMakingGui</a>

Specify a matchmaking parameter to show GUI for matchmaking.

        public static void ShowMatchMakingGui(uint? minNumberOfPlaysers = 2, uint? maxNumberOfPlaysers = 2, string[] inviteUsers = null, string invitationMessage = "", string segment = "", FASMatchMaking.Recipient recipent = FASMatchMaking.Recipient.Everyone, string returnSceneName = "", bool isModal = false, Action appSteroidModalGuiEnded = null)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|minNumberOfPlaysers|uint?|(Optional) Minimum players [2 - 16]. When null, the default is: 2|
|maxNumberOfPlaysers|uint?|(Optional) Maximum players [2 - 16]. When null, same as min_number_of_players.|
|inviteUsers|string[]|(Optional) list of user id of players to invite. Select null to invite none|
|invitationMessage|(Optional) string|Invitation message. Select null or empty text for no invitation message.|
|segment|string|(Optional) Match segment. Select null or empty text for no match segment. Match requests with the same string will match.|
|recipient|FASMatchMaking.Recipient|(Optional) Select either of the enum Recipient { Everyone, FriendOnly }|
|returnSceneName|string|(Optional) If isModal = true, no setting is required. A Scene name to return after closing GUI (When pressing app icon). When the scene to return is not selected, it will return to the root cause scene.|
|isModal|bool|(Optional) Select whether to use modal or not. If isModal = false, execute scene transition to show  the GUI. If isModal = true, load the scene without executing scene transition. |
|appSteroidModalGuiEnded|Action|This is a callback which will be called after GUI loading end. Use to restrain game input from end-users when isModal = true.|

#### Example

    FASGui.ShowMatchMakingGui(minNumberOfPlaysers:2, maxNumberOfPlaysers: 4);


---
### <a name ="FASGui.ShowMatchMakingGuiWithLogin">FASGui.ShowMatchMakingGuiWithLogin</a>

Select matchmaking parameter and show matchmaking GUI.

    public static void ShowMatchMakingGuiWithLogin(string userId, string userToken, uint? minNumberOfPlaysers = 2, uint? maxNumberOfPlaysers = 2, string[] inviteUsers = null, string invitationMessage = "", string segment = "", FASMatchMaking.Recipient recipient = FASMatchMaking.Recipient.Everyone, string returnSceneName = "")


#### Parameters
|Name|Type|Description|
|------|------|-----|
|userId|string|Login user ID|
|userToken|string|Login user token|
|minNumberOfPlaysers|uint?|(Optional) Minimum players [2 - 16]. When null, the default is: 2|
|maxNumberOfPlaysers|uint?|(Optional) Maximum players [2 - 16]. When null, same as min_number_of_players.|
|inviteUsers|string[]|(Optional) list of user id of players to invite. Select null to invite none|
|invitationMessage|(Optional) string|Invitation message. Select null or empty text for no invitation message.|
|segment|string|(Optional) Match segment. Select null or empty text for no match segment. Match requests with the same string will match.|
|recipient|FASMatchMaking.Recipient|(Optional) Select either of the enum Recipient { Everyone, FriendOnly }|
|returnSceneName|string|(Optional) If isModal = true, no setting is required. A Scene name to return after closing GUI (When pressing app icon). When the scene to return is not selected, it will return to the root cause scene.|
|isModal|bool|(Optional) Select whether to use modal or not. If isModal = false, execute scene transition to show  the GUI. If isModal = true, load the scene without executing scene transition. |
|appSteroidModalGuiEnded|Action|This is a callback which will be called after GUI loading end. Use to restrain game input from end-users when isModal = true.|

#### Example

    FASGui.ShowMatchMakingGuiWithLogin(userId, userToken); 