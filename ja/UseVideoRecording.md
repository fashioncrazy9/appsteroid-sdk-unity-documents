# プレイ動画録画の利用方法
last update at　2015/11/04

----------
コード内での各機能の利用については、[Spec-FASPlayVideo](Specs/Spec-FASPlayVideo.md)をご参照ください。

## Graphics API の設定

現在、AppSteroidでは Open GL ES 3.0 の録画機能に対応しています。
Player Setting -> Other Settings -> Graphics API を Open GL ES 3.0 に設定してください。

- Unity 4.6.*
![](Images/VideoRecordingSetting.png)

- Unity 5.1.*
![](Images/VideoRecordingSettingUnity5.png)

## ビルド後の処理

### Unity 4.6.* の場合
Unityでビルド後のXcodeプロジェクトにて、`GLESHelper. mm` ファイルの `CreateSystemRenderingSurfaceGLES` 内の

    [NSNumber numberWithBool:FALSE], kEAGLDrawablePropertyRetainedBacking,

という行を以下のように FALSE -> TRUE に編集してください。

    [NSNumber numberWithBool:TRUE], kEAGLDrawablePropertyRetainedBacking,

### Unity 5.1.* の場合
Unityでビルド後のXcodeプロジェクトにて、`GLESHelper. mm` ファイルの下記の該当箇所を

    if(surface->allowScreenshot && UnityIsCaptureScreenshotRequested())
    {
        GLint targetFB = surface->targetFB ? surface->targetFB : surface->systemFB;
        UnityBindFramebuffer(kReadFramebuffer, targetFB);
        UnityCaptureScreenshot();
    }

下記に書き換えてください。

    if(surface->allowScreenshot)
    {
        GLint targetFB = surface->targetFB ? surface->targetFB : surface->systemFB;
        UnityBindFramebuffer(kReadFramebuffer, targetFB);
        _FASCaptureScreenshot();
        if (UnityIsCaptureScreenshotRequested())
            UnityCaptureScreenshot();
    }

また、`GLESHelper. mm` ファイルに以下を追加してください。
    
    extern "C" void _FASCaptureScreenshot();