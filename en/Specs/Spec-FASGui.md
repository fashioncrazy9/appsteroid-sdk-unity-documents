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
|[FASGui.ShowGUI](#FASGui.ShowGUI)| Method to Show GUI. Call this method and load "FresviiGUI" scene. To use this method, add "FresviiGUI" to build setting. |
|[FASGui.ShowGUIWithLogin](#FASGui.ShowGUIWithLogin)| Process login and show GUI. It will shorten loading time compare to "ShowGUI". Call this method and than load the "FresviiGUI" scene. To use this method, please add "FresviiGUI" and "FresviiGUILoading" to build settings. |
|[FASGui.ShowMatchMakingGui](#FASGui.ShowMatchMakingGui)| Specify a matchmaking parameter to show GUI for matchmaking.|
|[FASGui.SetLeaderboard](#FASGui.SetLeaderboard)|Setup Leaderboard that will be shown on GUI. Select a name for Leaderboard on Web Console. |

### <a name ="FASGui.ShowGUI">FASGui.ShowGUI</a>

Load a scene to show GUI

   public static void ShowGUI(FASGui.Mode modeFlgs)
   public static void ShowGUI(string returnSceneName)
   public static void ShowGUI(FASGui.Mode modeFlgs, string returnSceneName)
   public static void ShowGUI(FASGui.Mode guiMode, FASGui.Mode selectedMode)
   public static void ShowGUI(FASGui.Mode guiMode, string returnSceneName, FASGui.Mode selectedMode)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|modeFlgs|FASGui.Mode|Select from Forum, Leaderboards, MyProfile, GroupMessage or All. You can select multiple mode except for GroupMessage. |
|returnSceneName|string|A Scene name to return after closing GUI (When pressing app icon). When the scene to return is not selected, it will return to the root cause scene. |
|selectedMode|FASGui.Mode|Select a specific tab to display first when you have selected a mode to show multiple GUIs.|

#### Example

  FASGui.ShowGUI(FresviiGUI.Mode.Forum | FresviiGUI.Mode.MyProfile, "startScene");

### <a name ="FASGui.ShowGUIWithLogin">FASGui.ShowGUIWithLogin</a>

Load the scene to show GUI with login.

	 public static void ShowGUIWithLogin(string userId, string userToken, FASGui.Mode guiMode, FASGui.Mode selectedMode)
	 public static void ShowGUIWithLogin(string userId, string userToken, FASGui.Mode guiMode, FASGui.Mode selectedMode, string returnSceneName)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|userId|string|User ID, of a user who is going to login|
|userToken|string|User token, of a user who is going to login|
|modeFlgs|FASGui.Mode|Select from Forum, Leaderboards, MyProfile, GroupMessage or All. Multiple GUI can be selected except GroupMessage and MatchMaking. |
|returnSceneName|string|Scene name to return when ending GUI (when pressing app icon). When no scene is selected, it will return to the original scene.|
|selectedMode|FASGui.Mode|Set one tab to be the start scene when multiple GUI are selected. |

#### Example
	
	FASGui.ShowGUI(FASGui.Mode.Forum | FASGui.Mode.MyProfile, "startScene");

### <a name ="FASGui.ShowMatchMakingGui">FASGui.ShowMatchMakingGui</a>

Specify a matchmaking parameter to show GUI for matchmaking.

	public static void ShowMatchMakingGui(uint? minNumberOfPlaysers, uint? maxNumberOfPlaysers, string[] inviteUsers, string invitationMessage, string segment)
	
	public static void ShowMatchMakingGui(uint? minNumberOfPlaysers, uint? maxNumberOfPlaysers, string[] inviteUsers, string invitationMessage, string segment, string returnSceneName)

	public static void ShowMatchMakingGui(uint? minNumberOfPlaysers, uint? maxNumberOfPlaysers, string[] inviteUsers, string invitationMessage, string segment, FASMatchMaking.Recipient recipient)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|minNumberOfPlaysers|uint?|Minimum players [2 - 16]. When null, the default is: 2|
|maxNumberOfPlaysers|uint?|Maximum players [2 - 16]. When null, same as min_number_of_players.|
|inviteUsers|string[]|list of user id of players to invite. Select null to invite none|
|invitationMessage|string|Invitation message. Select null or empty text for no invitation message.|
|segment|string|Match segment. Select null or empty text for no match segment. Match requests with the same string will match.|
|recipient|FASMatchMaking.Recipient|Select either of the enum Recipient { Everyone, FriendOnly }|
#### Example

  FASGui.ShowMatchMakingGui(2, 2, null, null, null);


### <a name ="FASGui.SetLeaderboard">FASGui.SetLeaderboard</a>

Setup Leaderboard that will be shown on GUI. You can setup a name for the Leaderboard on Web Console.

    public static void SetLeaderboard(string leaderboardName)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|leaderboardName|string|Leaderboard Name|


#### Example

  FASGui.SetLeaderboard("MyLeaderboard");
