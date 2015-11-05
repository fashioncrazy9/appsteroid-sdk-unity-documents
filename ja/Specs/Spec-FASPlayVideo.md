# FASPlayVideo Specifications

last update at　2015/10/21

----------

## Introduction

## <a name ="FASPlayVideo">FASPlayVideo Class</a>
**<font color='red'>このクラスは、Ver.1.0.8 現在、iOS のみ利用可能です。Android は未対応です。</font>**

ゲームプレイビデオの録画、再生、アップロードなどを操作するクラスです。

**現在、AppSteroidでは Open GL ES 3.0 の録画機能に対応しています。
Unity 4.6.2p2 以降をご利用の場合は、Player Setting -> Other Settings -> Graphics API を Open GL ES 3.0 に設定してください。**


![](../Images/VideoRecordingSetting.png)
----------

## Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASPlayVideo](#FASPlayVideo)|ゲームプレイビデオの録画、再生、アップロードなどを操作するクラス|

----------

### Methods

|Name|内容|
|------|-----|
|[FASPlayVideo.InitializeRecording](#FASPlayVideo.InitializeRecording)| ビデオ録画機能を初期化する|
|[FASPlayVideo.StartRecording](#FASPlayVideo.StartRecording)| ビデオ録画を開始する|
|[FASPlayVideo.StopRecording](#FASPlayVideo.StopRecording)| ビデオ録画を終了する|
|[FASPlayVideo.ShowLatestVideoSharingGUIWithUGUI](#FASPlayVideo.ShowLatestVideoSharingGUIWithUGUI)| 録画した最新ビデオをシェアするGUIを表示する。UGUIの上にダイアログを表示する。 |
|[FASPlayVideo.ShowLatestVideoSharingGUIWithLegacyGUI](#FASPlayVideo.ShowLatestVideoSharingGUIWithLegacyGUI)|録画した最新ビデオをシェアするGUIを表示する。LegacyGUIの上にダイアログを表示する。|
|[FASPlayVideo.LatestVideoExists](#FASPlayVideo.LatestVideoExists)| 録画したビデオが存在するか確認する |
|[FASPlayVideo.SetMaxRecordingSecondsLength](#FASPlayVideo.SetMaxRecordingSecondsLength)| ビデオ録画を最大時間（秒）を設定する|
|[FASPlayVideo.GetMaxRecordingSecondsLength](#FASPlayVideo.GetMaxRecordingSecondsLength)| ビデオ録画を最大時間（秒）を取得する|
|[FASPlayVideo.IsRecording](#FASPlayVideo.IsRecording)| ビデオ録画の録画状態を取得する|
|[FASPlayVideo.GetLatestRecordedVideoPath](#FASPlayVideo.GetLatestRecordedVideoPath)| 録画した最新ビデオのパスを取得する|


### <a name ="FASPlayVideo.InitializeRecording">FASPlayVideo.InitializeRecording</a>
ビデオ録画機能を初期化します。ビデオ録画開始前に、初期化する必要があります。
初期化後、端末を回転した場合、録画が正常に行われなくなります。端末の回転を許可している場合は、端末の回転後の適切なタイミングで録画開始前に初期化を行ってください。また、ビデオ録画中は端末の回転を行わないように設定してください。
初期化処理には多少時間がかかります。そのため、ゲームプレイ中などに初期化を行うと遅延が発生します。適切なタイミングで初期化を行うようにご注意ください。

    public static bool InitializeRecording(bool withAudio = true)

#### Return
|Type|内容|
|------|-----|
|bool| 録画機能の初期化処理の成否|

#### Parameters
|Name|Type|内容|
|------|------|-----|
|withAudio|bool|オーディオの録音の有無を指定します。デフォルト true|

### <a name ="FASPlayVideo.StartRecording">FASPlayVideo.StartRecording</a>
ビデオ録画を開始します。ビデオ録画最大時間に達するか、`StopRecording`　を呼び出すと、ビデオ録画は終了します。録画したビデオは、アプリの一時保存領域に保存されます。録画処理終了後、`ShowLatestVideoSharingGUI` を呼び出してビデオをAppSteroidサーバにアップロードします。録画したビデオはアプリを閉じるとOSが任意のタイミングで削除します。

    public static bool StartRecording()

#### Return
|Type|内容|
|------|-----|
|bool| 録画開始処理の成否|

### <a name ="FASPlayVideo.StopRecording">FASPlayVideo.StopRecording</a>
ビデオ録画を終了します。

    public static void StopRecording()

### <a name ="FASPlayVideo.ShowLatestVideoSharingGUI">FASPlayVideo.ShowLatestVideoSharingGUI</a>
録画した最新のビデオをシェアするGUIを表示します。

    public static bool ShowLatestVideoSharingGUI(string returnSceneName)
    public static bool ShowLatestVideoSharingGUI(string returnSceneName, Action guiEndedCallback)
    public static bool ShowLatestVideoSharingGUI(string returnSceneName, Action guiEndedCallback, bool sceneTransition)

#### Return
|Type|内容|
|------|-----|
|bool| false = 最新のビデオファイルが存在しない場合, true = GUIの表示に成功 |

#### Parameters
|Name|Type|内容|
|------|------|-----|
|returnSceneName| string | AppSteroid 画面に遷移した場合、GUI画面終了時（アプリアイコン押下時）に復帰するシーン名称。復帰するシーンが未設定の場合は、呼び出し元のシーンに戻ります。|
|guiEndedCallback| Action | GUI表示が終了時に呼び出されます。ビデオシェアおよびアップロードはuGUIで表示されます。このとき、uGUI のモーダルGUIの下でuGUI, legacy GUI 以外の操作を行っている場合は、コールバックが呼び出されるまでゲーム入力処理を抑制するために使用してください。|
|sceneTransition| bool | ビデオシェア完了後、GUIからAppSteroidのGUIへの遷移するかどうかを選択します。デフォルト = true です。 true の場合、ビデオシェアのアップロード処理完了後、アップロード完了GUIが表示され、ユーザーがコミュニティへの遷移を選択した場合にAppSteroidのGUIシーンに遷移します。false の場合は、ビデオシェアのアップロード完了後、完了ダイアログが表示されるのみでAppSrteroidのGUIシーンへの遷移しません。|

### <a name ="FASPlayVideo.LatestVideoExists">FASPlayVideo.LatestVideoExists</a>
録画した最新のビデオが存在するか確認します。

    public static bool LatestVideoExists()

#### Return
|Type|内容|
|------|-----|
|bool| false = 最新のビデオファイルが存在しない, true = 最新のビデオファイルが存在する |


### <a name ="FASPlayVideo.IsRecording">FASPlayVideo.IsRecording</a>
ビデオ録画の録画状態を取得します。

    public static bool IsRecording()

#### Return
|Type|内容|
|------|-----|
|bool| true = ビデオ録画中 |

### <a name ="FASPlayVideo.SetMaxRecordingSecondsLength">FASPlayVideo.SetMaxRecordingSecondsLength</a>
ビデオ録画を最大時間（秒）を設定します。ただし、最大録画時間は３０秒以下です。

    public static void SetMaxRecordingSecondsLength(float sec)

### <a name ="FASPlayVideo.GetMaxRecordingSecondsLength">FASPlayVideo.GetMaxRecordingSecondsLength</a>
ビデオ録画を最大時間（秒）を取得します。

    public static float GetMaxRecordingSecondsLength()

### <a name ="FASPlayVideo.GetLatestRecordedVideoPath">FASPlayVideo.GetLatestRecordedVideoPath</a>
録画した最新ビデオのパスを取得します。

    public static string GetLatestRecordedVideoPath()

#### Return
|Type|内容|
|------|-----|
|string| ビデオファイルパス。存在しない場合、空文字列（""）。 |
