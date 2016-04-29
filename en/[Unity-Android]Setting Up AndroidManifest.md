#  AndroidManifest setting for Android

You are required to set up AndroidManifest.xml to use the functions in AppSteroid.

## Automatically Generate Manifest File

If you do not have an unique manifest settings using outsourcing plugins, you can automatically generate AndroidManifest by the following steps.

On the Unity menu, go to Fresvii -> FASSetting and click "Generate Android.manifest" to generate the Plugins/Android/AndroidManifest.xml file. If a Manifest file with a same name already exists, the previous file will be backup by a different filename in the same folder.

Since the generator will refer to the parameters of the "Bundle Identifier" and "FASSetting" during automatic generation, if you make changes to the "Bundle Identifier" and "FASSetting" parameters, please regenerate a new Manifest file.

![](Images/AndroidManifestAutoGenerate.png)

----
# Manually Setup Manifest File

If you are using an outsourcing plugin or have setup an unique manifest setting and can not generate the manifest file automatically, follow the steps below to manually setup the AndroidManifest.

## Setting up Push Notification

Add the XML listed below in the  \<application\> tag in your AndroidManifest.xml file to use Push Notification.  Replace “INPUT_YOUR_BUNDLE_IDENTIFIER" to your apps bundle Identifier.

    <receiver android:name="com.fresvii.sdk.unity.GCMReceiver"
     android:permission="com.google.android.c2dm.permission.SEND" >
        <intent-filter>
            <action android:name="com.google.android.c2dm.intent.RECEIVE" />
            <action android:name="com.google.android.c2dm.intent.REGISTRATION" />
            <category android:name="INPUT_YOUR_BUNDLE_IDENTIFIER" />
        </intent-filter>
    </receiver>

    <service android:name="com.fresvii.sdk.unity.GCMIntentService" />

    <receiver android:name="com.fresvii.sdk.unity.BcReceiver">
      <intent-filter>
        <action android:name="INPUT_YOUR_BUNDLE_IDENTIFIER.NotificationTap" />
      </intent-filter>
    </receiver>


Add the XML listed below in the \<activity\> tag in your apps main activity.  This is required to launch the main activity when tapping on the notification message. Replace "INPUT_YOUR_BUNDLE_IDENTIFIER" to your apps bundle Identifier.

    <intent-filter>
          <action android:name="INPUT_YOUR_BUNDLE_IDENTIFIER.NotificationAction"/>
          <category android:name="android.intent.category.DEFAULT"/>
    </intent-filter>

Set launchMode in your apps main activity to "singleTask". This will prevent launching the main activity duplicately when tapping the push massage.

    android:launchMode="singleTask"

##Setting up BackupManager

Fresvii AppSteroid use BackupManager to store user data.  You can restore user data in the application linked to Goggle account by using BackupManager.  BackupManager will assure you to use the same user data even after the app is deleted or the user changes their devices.  To use BackupManager, please access to the link below and register for Android Backup Service provided by Google.

https://developer.android.com/google/backup/signup.html

After the registration process, you will get XML similar to the one below.  Please add this XML to your AndroidManifest.xml file.

    <meta-data android:name="com.google.android.backup.api_key"
         android:value="XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX_XXXXXXXXXXXXXXXXX" />

Add the attribute related to backup in \<application\> tag in your AndroidManifest.xml file.

    <application
        android:allowBackup="true"
        android:backupAgent="com.fresvii.sdk.unity.TheBackupAgent">


If you are already registered and using BackupManager, please backup the SharedPreferences.

## Adding ImagePickerActivity

With AppSteroid, you can to access the album to get images or use the camera to post users profile pictures and game screens on the forum. Add the XML listed below in the \<application\> tag to use activity for get image and camera.

    <activity android:name="com.fresvii.sdk.unity.ImagePickerActivity"/>

## Add Activity for video playback

Please add the following XML to application tag, in order to use video playback with Fresvii AppSteroid.

    <activity android:name="com.fresvii.sdk.unity.VideoPlayerActivity" android:configChanges="orientation|screenSize"/>

## Add Activity for video recording

Please add the following XML to application tag, in order to use video recording with Fresvii AppSteroid.

    <activity android:name="com.fresvii.sdk.unity.VideoRecordActivity" android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" android:configChanges="orientation|screenSize|keyboardHidden" />

Add the following code to \<application\> tag in AndroidManifest.xml

    <application
      android:largeHeap="true" >
## Setting up permission

Add the XML listed below in the \<application\> tag in your AndroidManifest.xml file to use push notification and to save/load images.

 <!— Required to receive push notification  -->
 <permission android:name="INPUT_YOUR_BUNDLE_IDENTIFIER.permission.C2D_MESSAGE"
         android:protectionLevel="signature" />
 <uses-permission android:name="INPUT_YOUR_BUNDLE_IDENTIFIER.permission.C2D_MESSAGE" />
 <uses-permission android:name="com.google.android.c2dm.permission.RECEIVE" />

 <!— Required to receive push notification while the device is in sleep mode. -->
 <uses-permission android:name="android.permission.WAKE_LOCK" />

 <!— “option” Required to get Google Account used for push notification.  Not necessary for Android 4.0.4 and higher. -->
 <uses-permission android:name="android.permission.GET_ACCOUNTS" />

 <!— “option” Required to set a vibration for push notification. -->
 <uses-permission android:name="android.permission.VIBRATE"/>

 <!— Required to access and to get users network states. -->
 <uses-permission android:name="android.permission.INTERNET" />
 <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />

 <!— Required to load/save images -->
 <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
 <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
 <uses-permission android:name="android.permission.MANAGE_DOCUMENTS" />

 <!-- Group Conference（Voice Chat -->
 <uses-permission android:name="android.permission.RECORD_AUDIO" />

# General AndroidManifest.xml for Unity

The AndroidManifest.xml file in a general Unity application which uses AppSteroid is as follows.  Replace “INPUT_YOUR_BUNDLE_IDENTIFIER" to your apps bundle Identifier "6 places".
Replace "backup.api_key" to the key strings you get.

    <?xml version="1.0" encoding="utf-8"?>

    <manifest xmlns:android="http://schemas.android.com/apk/res/android" package="INPUT_YOUR_BUNDLE_IDENTIFIER" android:installLocation="preferExternal" android:versionCode="1" android:versionName="1.0">

    <supports-screens android:smallScreens="true"
            android:normalScreens="true"
               android:largeScreens="true"
               android:xlargeScreens="true"
               android:anyDensity="true" />

    <permission android:name="INPUT_YOUR_BUNDLE_IDENTIFIER.permission.C2D_MESSAGE"
                android:protectionLevel="signature" />
    <uses-permission android:name="INPUT_YOUR_BUNDLE_IDENTIFIER.permission.C2D_MESSAGE" />
    <uses-permission android:name="com.google.android.c2dm.permission.RECEIVE" />
    <uses-permission android:name="android.permission.WAKE_LOCK" />
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.GET_ACCOUNTS" />
    <uses-permission android:name="android.permission.VIBRATE"/>
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.RECORD_AUDIO" />
    <uses-permission android:name="android.permission.MANAGE_DOCUMENTS" />

      <application android:theme="@android:style/Theme.NoTitleBar"
        android:icon="@drawable/app_icon"
        android:label="@string/app_name"
        android:debuggable="true"
        android:largeHeap="true"
        android:allowBackup="true"
        android:backupAgent="com.fresvii.sdk.unity.TheBackupAgent">

      <receiver android:name="com.fresvii.sdk.unity.GCMReceiver"
                  android:permission="com.google.android.c2dm.permission.SEND" >

        <intent-filter>
          <action android:name="com.google.android.c2dm.intent.RECEIVE" />
          <action android:name="com.google.android.c2dm.intent.REGISTRATION" />
          <category android:name="INPUT_YOUR_BUNDLE_IDENTIFIER" />
        </intent-filter>

      </receiver>

      <service android:name="com.fresvii.sdk.unity.GCMIntentService" />

      <receiver android:name="com.fresvii.sdk.unity.BcReceiver">
         <intent-filter>
            <action android:name="com.fresvii.fresvii_sdk_unity_production.NotificationTap" />
         </intent-filter>
      </receiver>

      <meta-data android:name="com.google.android.backup.api_key"
        android:value="XXXXXXXXXXXXXXXXXX_XXXXXXXXXXXXXXXXXX" />

    <!-- Unity 4.6 -->
      <activity android:name="com.unity3d.player.UnityPlayerNativeActivity"
                    android:label="@string/app_name"
                    android:launchMode="singleTask"
                    android:configChanges="fontScale|keyboard|keyboardHidden|locale|mnc|mcc|navigation|orientation|screenLayout|screenSize|smallestScreenSize|uiMode|touchscreen">

    <!-- Unity 5 -->
      <!--
    <activity android:name="com.unity3d.player.UnityPlayerActivity"
                    android:label="@string/app_name"
                    android:launchMode="singleTask"
                    android:configChanges="fontScale|keyboard|keyboardHidden|locale|mnc|mcc|navigation|orientation|screenLayout|screenSize|smallestScreenSize|uiMode|touchscreen">
     -->

        <meta-data android:name="android.app.lib_name" android:value="unity" />

        <meta-data android:name="unityplayer.ForwardNativeEventsToDalvik" android:value="false" />

        <intent-filter>
          <action android:name="android.intent.action.MAIN" />
          <category android:name="android.intent.category.LAUNCHER" />
        </intent-filter>

        <intent-filter>
          <action android:name="INPUT_YOUR_BUNDLE_IDENTIFIER.NotificationAction"/>
          <category android:name="android.intent.category.DEFAULT"/>
        </intent-filter>

      </activity>

      <activity android:name="com.unity3d.player.VideoPlayer"
        android:label="@string/app_name"
        android:configChanges="fontScale|keyboard|keyboardHidden|locale|mnc|mcc|navigation|orientation|screenLayout|screenSize|smallestScreenSize|uiMode|touchscreen">
      </activity>

      <activity android:name="com.fresvii.sdk.unity.ImagePickerActivity"/>
      <activity android:name="com.fresvii.sdk.unity.VideoPlayerActivity" android:configChanges="orientation|screenSize"/>
      <activity android:name="com.fresvii.sdk.unity.VideoRecordActivity" android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" android:configChanges="orientation|screenSize|keyboardHidden" />

    </application>

    <uses-feature android:glEsVersion="0x00020000" />

    <uses-sdk android:minSdkVersion="10" android:targetSdkVersion="14" />