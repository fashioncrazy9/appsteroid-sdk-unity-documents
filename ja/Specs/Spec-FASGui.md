# FASGui Specifications

last update at 2015/11/03

----------

## Introduction

## <a name ="FASGui">FASGui Class</a>
GUI シーンの表示操作をするクラスです。

----------

## Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASGui](#FASGui)|GUI シーンの表示操作をするクラス|

----------

### Defines
|Name|Type|Value|
|------|-----|-----|
|Mode|enum|Forum = (1 << 0), <br> Leaderboards = (1 << 1), <br> MyProfile = (1 << 2), <br> GroupMessage = (1 << 3), <br>MatchMaking = (1 << 4), <br> All = 0xFFFF

### Methods

|Name|内容|
|------|-----|
|[FASGui.ShowGUI](#FASGui.ShowGUI)| GUIを表示します。このメソッドを呼び出しGUIのシーンをロードします。このメソッドを利用する際は、ビルド設定に "AppSteroidUI" を加えてください。 |
|[FASGui.ShowGUIWithLogin](#FASGui.ShowGUIWithLogin)| 指定したユーザーでログインを行い、GUIを表示します。このメソッドを利用する際は、ビルド設定に "AppSteroidUI" を加えてください。 |
|[FASGui.ShowMatchMakingGui](#FASGui.ShowMatchMakingGui)| マッチメイキングパラメータを指定してマッチメイキングGUIを表示します。|
|[FASGui.ShowMatchMakingGuiWithLogin](#FASGui.ShowMatchMakingGuiWithLogin)| 指定したユーザーでログインを行い、マッチメイキングパラメータを指定してマッチメイキングGUIを表示します。|


### <a name ="FASGui.ShowGUI">FASGui.ShowGUI</a>

GUIを表示するシーンをロードします。 引数として、isModal = true の場合は、シーンを追加ロードするため、シーンの遷移は行いません。
ユーザーがログインしていない場合は、最後にログインしたユーザーで自動的にログインして GUI を表示します。

            public static void ShowGUI(FASGui.Mode guiMode = Mode.All, string returnSceneName = "", FASGui.Mode selectedMode = Mode.LastSelected, bool isModal = false, Action appSteroidModalGuiEnded = null)


#### Parameters
|Name|Type|内容|
|------|------|-----|
|guiMode|FASGui.Mode|（オプション）Forum, Leaderboards, MyProfile, GroupMessage, All から選択。GroupMessage と MatchMaking 以外は複数選択ができます。|
|returnSceneName|string|（オプション）isModal = true の場合はシーン遷移をしないので、設定は不要です。 GUI終了時（アプリアイコン押下時）に復帰するシーン名称。復帰するシーンが未設定の場合は、呼び出し元のシーンに戻ります。|
|selectedMode|FASGui.Mode|（オプション）複数GUIモード表示選択時に最初に表示するタブを設定します。|
|isModal|bool|（オプション）モーダル表示を行う是非を指定します。isModal = false の場合は、シーン遷移を行い、GUIを表示します。 isModal = true の場合は、シーン遷移を行わずに、シーンを追加ロードします。|
|appSteroidModalGuiEnded|Action|（オプション）GUIが表示終了時に呼び出されるコールバックです。isModal = true でGUIを表示した場合に、ゲームの操作を抑制する際に利用します。|

#### Example

##### デフォルト設定で表示する
    FASGui.ShowGUI();

##### モーダル表示をする
    FASGui.ShowGUI(isModal:true, appSteroidModalGuiEnded:() => { Debug.Log("AppSteroid GUI Done"); });


### <a name ="FASGui.ShowGUIWithLogin">FASGui.ShowGUIWithLogin</a>

指定したユーザーでログインを行い、AppSteroid GUI を表示します。

        public static void ShowGUIWithLogin(string userId, string userToken, FASGui.Mode guiMode = Mode.All, string returnSceneName = "", FASGui.Mode selectedMode = Mode.MoreApps, bool isModal = false, Action appSteroidModalGuiEnded = null)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|userId|string|ログインするユーザーのID|
|userToken|string|ログインするユーザーのトークン|
|guiMode|FASGui.Mode|（オプション）Forum, Leaderboards, MyProfile, GroupMessage, All から選択。GroupMessage と MatchMaking 以外は複数選択ができます。|
|returnSceneName|string|（オプション）(isModal = true の場合はシーン遷移をしませんので、設定は不要) GUI終了時（アプリアイコン押下時）に復帰するシーン名称。復帰するシーンが未設定の場合は、呼び出し元のシーンに戻ります。|
|selectedMode|FASGui.Mode|（オプション）複数GUIモード表示選択時に最初に表示するタブを設定します。|
|isModal|bool|（オプション）モーダル表示を行う是非を指定します。isModal = false の場合は、シーン遷移を行い、GUIを表示します。 isModal = true の場合は、シーン遷移を行わずに、シーンを追加ロードします。|
|appSteroidModalGuiEnded|Action|（オプション）GUIが表示終了時に呼び出されるコールバックです。isModal = true でGUIを表示した場合に、ゲームの操作を抑制する際に利用します。|

#### Example
	
    FASGui.ShowGUIWithLogin(userId, userToken);

---
### <a name ="FASGui.ShowMatchMakingGui">FASGui.ShowMatchMakingGui</a>

マッチメイキングパラメータを指定してマッチメイキングGUIを表示します。

        public static void ShowMatchMakingGui(uint? minNumberOfPlaysers = 2, uint? maxNumberOfPlaysers = 2, string[] inviteUsers = null, string invitationMessage = "", string segment = "", FASMatchMaking.Recipient recipent = FASMatchMaking.Recipient.Everyone, string returnSceneName = "", bool isModal = false, Action appSteroidModalGuiEnded = null)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|minNumberOfPlaysers|uint?|（オプション）最小参加者数 [2 - 16] null 指定の場合デフォルト: 2|
|maxNumberOfPlaysers|uint?|（オプション）最大参加者数 [2 - 16] null指定の場合 min_number_of_playersと同じ|
|inviteUsers|string[]|（オプション）招待するユーザのIDリスト。 null 指定で招待ユーザーなし|
|invitationMessage|string|（オプション）招待メッセージ。 null もしくは 空文字列で招待メッセージなし|
|segment|string|（オプション）マッチ区分。null もしくは 空文字列でマッチ区分なし。マッチリクエストのこの文字列が一致しているリクエスト同士がマッチします。|
|recipient|FASMatchMaking.Recipient|（オプション）enum Recipient { Everyone, FriendOnly }のいずれかを指定。デフォルトは Everyone|
|returnSceneName|string|（オプション）isModal = true の場合はシーン遷移をしないので、設定は不要です。 GUI終了時（アプリアイコン押下時）に復帰するシーン名称。復帰するシーンが未設定の場合は、呼び出し元のシーンに戻ります。|
|isModal|bool|（オプション）モーダル表示を行う是非を指定します。isModal = false の場合は、シーン遷移を行い、GUIを表示します。 isModal = true の場合は、シーン遷移を行わずに、シーンを追加ロードします。|
|appSteroidModalGuiEnded|Action|（オプション）GUIが表示終了時に呼び出されるコールバックです。isModal = true でGUIを表示した場合に、ゲームの操作を抑制する際に利用します。|

#### Example

    FASGui.ShowMatchMakingGui(minNumberOfPlaysers:2, maxNumberOfPlaysers: 4);

---
### <a name ="FASGui.ShowMatchMakingGuiWithLogin">FASGui.ShowMatchMakingGuiWithLogin</a>

マッチメイキングパラメータを指定してマッチメイキングGUIを表示します。

    public static void ShowMatchMakingGuiWithLogin(string userId, string userToken, uint? minNumberOfPlaysers = 2, uint? maxNumberOfPlaysers = 2, string[] inviteUsers = null, string invitationMessage = "", string segment = "", FASMatchMaking.Recipient recipient = FASMatchMaking.Recipient.Everyone, string returnSceneName = "")


#### Parameters
|Name|Type|内容|
|------|------|-----|
|userId|string|ログインするユーザーのID|
|userToken|string|ログインするユーザーのトークン|
|minNumberOfPlaysers|uint?|（オプション）最小参加者数 [2 - 16] null 指定の場合デフォルト: 2|
|maxNumberOfPlaysers|uint?|（オプション）最大参加者数 [2 - 16] null指定の場合 min_number_of_playersと同じ|
|inviteUsers|string[]|（オプション）招待するユーザのIDリスト。 null 指定で招待ユーザーなし|
|invitationMessage|string|（オプション）招待メッセージ。 null もしくは 空文字列で招待メッセージなし|
|segment|string|（オプション）マッチ区分。null もしくは 空文字列でマッチ区分なし。マッチリクエストのこの文字列が一致しているリクエスト同士がマッチします。|
|recipient|FASMatchMaking.Recipient|（オプション）enum Recipient { Everyone, FriendOnly }のいずれかを指定。デフォルトは Everyone|
|returnSceneName|string|（オプション）isModal = true の場合はシーン遷移をしないので、設定は不要です。 GUI終了時（アプリアイコン押下時）に復帰するシーン名称。復帰するシーンが未設定の場合は、呼び出し元のシーンに戻ります。|
|isModal|bool|（オプション）モーダル表示を行う是非を指定します。isModal = false の場合は、シーン遷移を行い、GUIを表示します。 isModal = true の場合は、シーン遷移を行わずに、シーンを追加ロードします。|
|appSteroidModalGuiEnded|Action|（オプション）GUIが表示終了時に呼び出されるコールバックです。isModal = true でGUIを表示した場合に、ゲームの操作を抑制する際に利用します。|

#### Example

    FASGui.ShowMatchMakingGuiWithLogin(userId, userToken);
