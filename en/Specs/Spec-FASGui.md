# FASGui Specifications

last update at 2016/01/04

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
|[FASGui.ShowMatchMakingGui](#FASGui.ShowMatchMakingGui)| Specify a matchmaking parameter to show GUI for matchmaking. |
|[FASGui.ShowMatchMakingGuiWithLogin](#FASGui.ShowMatchMakingGuiWithLogin)| Process logn with a specified user, specify matchmaking parameter and show matchmaking GUI. |
|[FASGui.ShowLeaderboard](#FASGui.ShowLeaderboard)| Specify a leaderboard ID to show that leaderboard GUI. |
|[FASGui.SetLeaderboardsOrder](#FASGui.SetLeaderboardsOrder)|Define the sort order of leaderboard. |
|[FASGui.ClearLeaderboardsOrder](#FASGui.ClearLeaderboardsOrder)|Clear the sorting settings for leaderboard list. Sort order will be the same as the sort order on the Web Console. |
|[FASGui.HasNotifications](#FASGui.HasNotifications)|Get whether the notification was received or not. |


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

### <a name ="FASGui.ShowLeaderboard">FASGui.ShowLeaderboard</a>

Show leaderboard. If the argument isModal = true, the scene will be loaded without scene transition.
If the user is not logged in, automatically login with the previous user ID.

    public static void ShowLeaderboard(string leaderboardId, string returnSceneName = "", bool isModal = false, Action appSteroidModalGuiEnded = null)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|leaderboardId|string|Leaderboard ID|
|returnSceneName|string|(Optional) No need to use this if isModal = true, since the scene will not transit. If not, select a scene name to return when the AppSteroid GUI ends. If scene name isn't selected, it will return to the last scene out of AppSteroid.|
|isModal|bool|(Optional) Choose whether to use the modal mode. If isModal = false, show the AppSteroid GUI with scene transit. If isModal = true, load the scene without transit.|
|appSteroidModalGuiEnded|Action|(Optional) A Callback to be called when the AppSteroid GUI ends. If AppSteroid GUI was shown with isModal = true, the game controll can be inhibited.|

#### Example

    string leaderboardId = "50d8d7095ca940c6bce7dfdf1df80d44";

    FASGui.ShowLeaderboard(leaderboardId);


### <a name ="FASGui.SetLeaderboardsOrder">FASGui.SetLeaderboardsOrder</a>

Define the sort order of leaderboard.

            public static void SetLeaderboardsOrder(string[] leaderboardIds)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|leaderboardIds|string[]|Leaderboard ID. Sorting the value top to down.|

#### Example

    string[] leaderboardOrderIds =
    {"50d8d7095ca940c6bce7dfdf1df80d44",
      "0c09e56de3a148d4806e263f01fa572d",
      "5c969d304dc543acac66fb4f552e13d9"};

    FASGui.SetLeaderboardsOrder(leaderboardOrderIds);

### <a name ="FASGui.SetLeaderboardsOrder">FASGui.SetLeaderboardsOrder</a>

Clear the sorting settings for leaderboard list. Sort order will be the same as the sort order on the Web Console.

    public static void ClearLeaderboardsOrder()

### <a name ="FASGui.HasNotifications">FASGui.HasNotifications</a>

Get whether the notification was received or not.
    
    public static void HasNotifcations(Action<bool> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|callback|Action<bool>|Callback with the argument of notification (true / false)|

#### Example
    Fresvii.AppSteroid.FASGui.HasNotifcations((hasNotifications) =>
    {
        if (hasNotifications)
        {
            //  Has notification
        }
    });
