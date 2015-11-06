# FASPlayVideo Specifications

last update at　2015/10/21

----------

## Introduction

## <a name ="FASPlayVideo">FASPlayVideo Class</a>
**<font color='red'>This class can only be used in iOS for Ver.1.0.7. Android is not supported.</font>**

Class to operate record, play and upload game play video.

**AppSteroid currently support Open GL ES 3.0 for recording function.
If you are using Unity 4.6.2p2 or later, go to Player Setting -> Other Settings and change the Graphics API to Open GL ES 3.0.
**


![](../Images/VideoRecordingSetting.png)
----------

## Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASPlayVideo](#FASPlayVideo)|Class to operate record, play and upload game play video.|

----------

### Methods

|Name|Description|
|------|-----|
|[FASPlayVideo.InitializeRecording](#FASPlayVideo.InitializeRecording)| Initialize the video recording function|
|[FASPlayVideo.StartRecording](#FASPlayVideo.StartRecording)| Start video recording|
|[FASPlayVideo.StopRecording](#FASPlayVideo.StopRecording)| End video recording|
|[FASPlayVideo.ShowLatestVideoSharingGUIWithUGUI](#FASPlayVideo.ShowLatestVideoSharingGUIWithUGUI)| Show GUI to share the latest recorded video. Show dialog on UGUI. |
|[FASPlayVideo.ShowLatestVideoSharingGUIWithLegacyGUI](#FASPlayVideo.ShowLatestVideoSharingGUIWithLegacyGUI)|Show GUI to share the latest recorded video. Show dialog on LegacyGUI. |
|[FASPlayVideo.LatestVideoExists](#FASPlayVideo.LatestVideoExists)|Check whether the recorded video exists or not|
|[FASPlayVideo.SetMaxRecordingSecondsLength](#FASPlayVideo.SetMaxRecordingSecondsLength)|Set maximum length for video recording in second|
|[FASPlayVideo.GetMaxRecordingSecondsLength](#FASPlayVideo.GetMaxRecordingSecondsLength)|Get maximum length for video recording (sec)|
|[FASPlayVideo.IsRecording](#FASPlayVideo.IsRecording)|Get status for video recording|
|[FASPlayVideo.GetLatestRecordedVideoPath](#FASPlayVideo.GetLatestRecordedVideoPath)|Get pass for the latest recorded video|


### <a name ="FASPlayVideo.InitializeRecording">FASPlayVideo.InitializeRecording</a>
To work the video recording function properly, you must initialize it before recording.
If you allow the screen to rotate during game play, you must initialize the function before the video recording is done. If the user rotate the device after initialization, the recording will not work properly. To avoid this problem, please initialize the video recording function every time after screen rotation is done. Also, make sure you do not allow the screen to rotate during video recording. 

    public static bool InitializeRecording(bool withAudio = true)

#### Return
|Type|Description|
|------|-----|
|bool| Success and failure of initializing video recording |

#### Parameters
|Name|Type|Description|
|------|------|-----|
|withAudio|bool|Select whether to turn audio recording on or off. Default is true (on)|


### <a name ="FASPlayVideo.StartRecording">FASPlayVideo.StartRecording</a>
Start video recording. Video recording will stop if the length reaches the maximum time, or by calling `StopRecording`.  Recorded video will be saved in the app temporally storage area. Call `ShowLatestVideoSharingGUI` to upload the video on AppSteroid server after recording the game. Recorded video will automatically be deleted after closing the app.

  public static bool StartRecording()

#### Return
|Type|Description|
|------|-----|
|bool|Success or failure of recording|

### <a name ="FASPlayVideo.StopRecording">FASPlayVideo.StopRecording</a>
End video recording

  public static void StopRecording()

### <a name ="FASPlayVideo.ShowLatestVideoSharingGUI">FASPlayVideo.ShowLatestVideoSharingGUI</a>
Show GUI to share the latest recorded video

  public static bool ShowLatestVideoSharingGUI(string returnSceneName)
  public static bool ShowLatestVideoSharingGUI(string returnSceneName, Action guiEndedCallback)
  public static bool ShowLatestVideoSharingGUI(string returnSceneName, Action guiEndedCallback, bool sceneTransition)

#### Return
|Type|Description|
|------|-----|
|bool| false = the latest video file does not exists, true = successfully displayed the GUI|

#### Parameters
|Name|Type|Description|
|------|------|-----|
|returnSceneName| string | Scene name to return when the GUI screen ends. If no scene is set, it will return to the caller scene. |
|guiEndedCallback| Action | GUI is called at the end. Video share and upload will be shown on uGUI.  If you are preforming an operation other than legacy GUI or uGUI under modal GUI of uGUI, please use it to suppress the game input process until the callback is called. |
|sceneTransition| bool | Select whether to move to the AppSteroid GUI or not after completing the video sharing.  Default = true. If true, upload completion GUI will be shown after the video share, and the user will have a choice to either move to the AppSteroid community GUI scene or stay in the same game scene. If false, completion dialog will be shown after video share without giving a choice to the user to move the scene. Instead, the user is forced to stay in the same game scene |


### <a name ="FASPlayVideo.LatestVideoExists">FASPlayVideo.LatestVideoExists</a>
Check whether the recorded video exists or not

  public static bool LatestVideoExists()

#### Return
|Type|Description|
|------|-----|
|bool| false = the latest video file does not exists, true = the latest video file do exist |


### <a name ="FASPlayVideo.IsRecording">FASPlayVideo.IsRecording</a>
Get status for video recording

  public static bool IsRecording()

#### Return
|Type|Description|
|------|-----|
|bool| true = recording video |


### <a name ="FASPlayVideo.SetMaxRecordingSecondsLength">FASPlayVideo.SetMaxRecordingSecondsLength</a>
Set maximum length for video recording in second. Maximum length must be under 30 second.

  public static void SetMaxRecordingSecondsLength(float sec)

### <a name ="FASPlayVideo.GetMaxRecordingSecondsLength">FASPlayVideo.GetMaxRecordingSecondsLength</a>
Get maximum length for video recording (sec)

  public static float GetMaxRecordingSecondsLength()

### <a name ="FASPlayVideo.GetLatestRecordedVideoPath">FASPlayVideo.GetLatestRecordedVideoPath</a>
Get pass for the latest recorded video

  public static string GetLatestRecordedVideoPath()

#### Return
|Type|Description|
|------|-----|
|string| Video file pass. If it does not exists, an empty string (""). |
