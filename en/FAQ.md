# Frequently asked questions about AppSteroid for Unity #


----------

#### Which versions of Unity are supported?

The supported versions of Unity are 4.6.7 and later. Unity Pro is not required.
If you are using Unity 5, please use version 5.1.2 or higher.

#### What do I need to do to update the AppSteroid SDK?
Please check [Updating the SDK](Updating AppSteroidSDK.md) for instructions.

#### GUI texture looks blurry on the screen. How can I fix it?

Go to "QualitySettings" on Unity and change the Texture Quality to Full Res.

#### What should I do when an error occurs after installing the updated AppSteroid SDK package?

When an error occurs right after the installation, existing old files or duplicated classes may be causing the error. Please delete the Assets/Fresvii folder and reinstall the latest AppSteroid SDK package.

**<span style="color:red">Your previous settings for FASSetting will be lost when deleting the Assets/Fresvii folder.</span>** So, please save your AppID, Secret key or GCM Project Number on a note. Also, you can save the `FASSettings.asset` file on the side and save it over the new file after installing the latest SDK package.

#### Error occurs on iOS build. What should I do?

If you see an error on `FASGTMHTPFetcher` like the following image, Set the `Enable Objective-C Exception` to `YES`.  Type exception in search box to find it.

![](Images/FASGTMHTPFetcher-Error.png)

![](Images/BuildSetting-Objectvie-exception.png)

#### Play video is alway black after the video capture on iOS. Any solution?

AppSteroid currently support Open GL ES 3.0 for recording function.
Go to Player Setting -> Other Settings and change the Graphics API to Open GL ES 3.0.

- Unity 4.6.7
![](Images/VideoRecordingSetting.png)


- Unity 5.1.2
![](Images/VideoRecordingSettingUnity5.png)

In the generated Xcode project, in GLESHelper. mm, find CreateSystemRenderingSurfaceGLES, and change:

    [NSNumber numberWithBool:FALSE], kEAGLDrawablePropertyRetainedBacking,

to:

    [NSNumber numberWithBool:TRUE], kEAGLDrawablePropertyRetainedBacking,


#### Screen transition is very slow when loading a new scene. Any solution to speed it up?

AppSteroid for Unity do provide a method to speed up scene loading.  Please check [FASGui.ShowGUIWithLogin](https://github.com/fresvii/appsteroid-sdk-unity-documents/blob/master/en/Specs/Spec-FASGui.md#FASGui.ShowGUIWithLogin) for detail.
Also, if you are using Unity pro, you can speed up screen transition with asynchronous process.

#### Error occurs right after installing the AppSteroid package. What should I do? 

**Case 1.** AppSteroid supports iOS and Android platform. If your are selecting any other platform besides iOS or Android, an error may occur.  Select iOS or Android after checking the build settings to avoid any error.

**Case 2.** If you see either of these two error, `'Fresvii.AppSteroid.FASConfig' is defined multiple times` or `'FASConfig' could not be found.`, it is likely that you have installed the AppSteroid SDK that does not match with your Unity version. Please reinstall either of the correct package, AppSteroid SDK for Unity4.6 or AppSteroid SDK for Unity 5.

![](Images/invalid_SDK_Version.png)

![](Images/invalid_SDK_Version2.png)

**Case 3.** If you see an error indicating that there is a missing file or class does not exist, you may have failed importing the package and the files. Please try reinstalling it again.

Please check the document, [SDK Update](Updating AppSteroidSDK.md), for error involved on updating the SDK. 

#### <a name="apsanddatabase">- Where and How will the data be stored?</a>
Since AppSteroid is operated on AWS, all data created through the API calls will be managed on the AWS database.  We may cache data locally for non connected use of the AppSteroid platform, or to improve performance. Part of these persistence user data can be exported from the Web Console.


All AppSteroid user data is basically managed on the same database, and individual data can be distinguish by linking them to the application or the user. If you want the database to be private, we also offer a separate plan to support.


#### <a name="commonsystem">- If the system is going to co-exist with our database, how should it be done? (Especially User Data)</a>
All AppSteroid user data are ensured to be unique and also can be identified by the ID.  If users are managed on your system, you must have a solution to relate your own user data with the AppSteroid user data.  If you are using any other third party services, we recommend you to treat one of the user data as a master, and link the other user data to it.

The data used in each service should be held by each service.  If you want to link the data between each services, you can preform it by calling the API provided by the service from the app. We currently do not provide any interface to communicate directly between the servers.