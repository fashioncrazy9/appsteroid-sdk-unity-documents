# FASPlayVideo Specifications

last update at　2015/04/27

----------

## Introduction

## <a name ="FASPlayVideo">FASPlayVideo Class</a>
**<font color='red'>This class can only be used in iOS for Ver.0.7.0. Android is not supported.</font>**

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
|[FASPlayVideo.StartRecording](#FASPlayVideo.StartRecording)| Start video recording|
|[FASPlayVideo.StopRecording](#FASPlayVideo.StopRecording)| End video recording|
|[FASPlayVideo.ShowLatestVideoSharingGUIWithUGUI](#FASPlayVideo.ShowLatestVideoSharingGUIWithUGUI)| Show GUI to share the latest recorded video. Show dialog on UGUI. |
|[FASPlayVideo.ShowLatestVideoSharingGUIWithLegacyGUI](#FASPlayVideo.ShowLatestVideoSharingGUIWithLegacyGUI)|Show GUI to share the latest recorded video. Show dialog on LegacyGUI. |
|[FASPlayVideo.LatestVideoExists](#FASPlayVideo.LatestVideoExists)|Check whether the recorded video exists or not|
|[FASPlayVideo.SetMaxRecordingSecondsLength](#FASPlayVideo.SetMaxRecordingSecondsLength)|Set maximum length for video recording in second|
|[FASPlayVideo.GetMaxRecordingSecondsLength](#FASPlayVideo.GetMaxRecordingSecondsLength)|Get maximum length for video recording (sec)|
|[FASPlayVideo.IsRecording](#FASPlayVideo.IsRecording)|Get status for video recording|
|[FASPlayVideo.GetLatestRecordedVideoPath](#FASPlayVideo.GetLatestRecordedVideoPath)|Get pass for the latest recorded video|


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

#### Return
|Type|Description|
|------|-----|
|bool| false = the latest video file does not exists, true = successfully displayed the GUI|

#### Parameters
|Name|Type|Description|
|------|------|-----|
|returnSceneName| string | Scene name to return when the GUI screen ends. If no scene is set, it will return to the caller scene. |
|guiEndedCallback| Action | GUI is called at the end. Video share and upload will be shown on uGUI.  If you are preforming an operation other than legacy GUI or uGUI under modal GUI of uGUI, please use it to suppress the game input process until the callback is called. |


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
