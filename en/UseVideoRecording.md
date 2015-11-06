# How to use Video Recording
last update at　2015/11/04

----------
Please see [Spec-FASPlayVideo](Specs/Spec-FASPlayVideo.md) for more details about functions in the sample code.

## Graphics API Settings

AppSteroid currently support video recording with Open GL ES 3.0.
Please set Player Setting -> Other Settings -> Graphics API to Open GL ES 3.0.

- Unity 4.6.*
![](Images/VideoRecordingSetting.png)

- Unity 5.1.*
![](Images/VideoRecordingSettingUnity5.png)

## Steps After the Build

### On Unity 4.6.*
In the generated Xcode project, in GLESHelper. mm, find CreateSystemRenderingSurfaceGLES, and change:

    [NSNumber numberWithBool:FALSE], kEAGLDrawablePropertyRetainedBacking,

to

    [NSNumber numberWithBool:TRUE], kEAGLDrawablePropertyRetainedBacking,

FALSE --> TRUE.

### On Unity 5.1.*
In the generated Xcode project, in `GLESHelper. mm` file, find the following code,

    if(surface->allowScreenshot && UnityIsCaptureScreenshotRequested())
    {
        GLint targetFB = surface->targetFB ? surface->targetFB : surface->systemFB;
        UnityBindFramebuffer(kReadFramebuffer, targetFB);
        UnityCaptureScreenshot();
    }

and change to the code below.

    if(surface->allowScreenshot)
    {
        GLint targetFB = surface->targetFB ? surface->targetFB : surface->systemFB;
        UnityBindFramebuffer(kReadFramebuffer, targetFB);
        _FASCaptureScreenshot();
        if (UnityIsCaptureScreenshotRequested())
            UnityCaptureScreenshot();
    }

Also, add the following code to `GLESHelper. mm` file.
    
    extern "C" void _FASCaptureScreenshot();

## About Initializing Video Recording Function
To work the video recording function properly, you must [initialize](Specs/Spec-FASPlayVideo.md#FASPlayVideo.InitializeRecording) it before the recording starts.

If you allow the screen to rotate during game play, you must initialize the function before the video recording starts. If the user rotate the device after initialization, the recording will not work properly. To avoid this problem, please initialize the video recording function every time after screen rotation is done. Also, make sure you do not allow the screen to rotate during video recording. 

Initialization process may take some time to complete. If the initialization is done during game play, delay may occur.  Please make sure the process is executed in the proper timing.

If the check under Menu -> Fresvii -> FAS Setting -> iOS Settings / Initialize video recording is On, initialization will automatically be executed when the app launch. If you do not want to automate this execution, please check it off.