# AppSteroid for Unity Release Notes
------
## 1.0.3
- New Feature
    - Group hiding. App users can hide groups.
    - Ability to setup default context for SNS sharing.
    - Leaderboard filtering. Developer can specify which leaderboard to show.
    
- Performance improvements
    - Layout fix and GUI improvements
    
- Fixed
    - Error on Play Stats metric.
    - Can not save image on certain threads.
    - [Android] App do not launch when tapping on a push notification. Changed Manifest file settings.

- Existing problem
	  - iOS Devices will crash when using Group Conference (Voice Chat) on Unity5. For those who are using Unity 5, please use the SDK without Voice Chat. Android devices will operate correctly.

## 1.0.2
- Performance improvements
    - GUI layout on certain pages are tweaked
    
- Fixed
    - Page view bugs on few more pages.
    - App icon do not show up on Apps tab when launching the app at the very first time.
    
- Existing problem
    - iOS Devices will crash when using Group Conference (Voice Chat) on Unity5. For those who are using Unity 5, please use the SDK without Voice Chat. Android devices will operate correctly.

#1.0.1
- Performance improvements
    - GUI layout on certain pages are tweaked
    
- Fixed
    - Page view bug
    
- Existing problem
	  - iOS Devices will crash when using Group Conference (Voice Chat) on Unity5. For those who are using Unity 5, please use the SDK without Voice Chat. Android devices will operate correctly.

#1.0.0
- Performance improvements
    - New GUI

## 0.7.3
- Fix
	  - GUI bug occurs when canceling image selection on iOS.
  
- Existing problem
	  - iOS Devices will crash when using Group Conference (Voice Chat) on Unity5. For those who are using Unity 5, please use the SDK without Voice Chat. Android devices will operate correctly.

## 0.7.2
- New Feature
    - Ability to control user name duplication. 

- Existing problem
	  - iOS Devices will crash when using Group Conference (Voice Chat) on Unity5. For those who are using Unity 5, please use the SDK without Voice Chat. Android devices will operate correctly.

## 0.7.1
- New Feature
    - App launch count and play time tracker. 
  
- Performance improvements
	  - Function to determine whether the [iOS] APNS certificate is for Development or Production.
	  - Replaced message button on the official user profile page.

- Existing problem
	  - iOS Devices will crash when using Group Conference (Voice Chat) on Unity5. For those who are using Unity 5, please use the SDK without Voice Chat. Android devices will operate correctly.

## 0.7.0
- New Feature
	  - CSR Chat (Live Help, Customer Support).
	  - Ability to continue voice chat even after the app moves to the background. Please check the document ["Use Group Conference(VoiceChat)"](Use Group Conference(VoiceChat).md) for details.

- Performance improvements
	  - Ability to set timeframe for ranking on leaderboard on the WebConsole.

- Fix
	  - Cannot post video on thread comment.

- Existing problem
    - iOS Devices will crash when using Group Conference (Voice Chat) on Unity5. For those who are using Unity 5, please use the SDK without Voice Chat. Android devices will operate correctly.

## 0.6.1
- New Feature
	- EULA (end user license agreement), for first time AppSteroid GUI user, is now available. This can be setup from the Fresvii Web Console. 
- Performance improvements
	- [iOS] Improve post build process.
	- Error message for matchmake have changed.
- Fix
	- Unable to sign up when using Unity 5.
	- Error occurs when installing AppSteroid on Unity 4.6.
	- Player who sent a match invitation crashes on certain circumstance.

## 0.6.0
- New Feature
	- Ability to open a link when an URL was included in a comment.
	- Flagging and reporting an inappropriate comment.
	- Matchmaking filter.
	- Ability to edit score format on leaderboards.
	- Valid/Invalid settings for functions related to video recording.
	- [iOS] Save videos on camera roll.
	- [iOS] Show Play back count and Like count on Video list.
- Fixed
	- Progress circle doesn't disappear on AppSteroid GUI. 
	- The scene to return after video share was  not determined.
	- User icon doesn't appear on the GUI to edit group members.
	- Error message text.
  
## 0.4.2
- Performance improvements
	- Add FASGui.ShowGUIWithLogin method, shorten load time to display the GUI
- Fixed
	- Minor bugs on unread message management for group message
	- Scroll view disappears from the screen
	- Layout in the forum sometime does not switch from landscape to portrait.

## 0.4.1
- New Feature
  - GUI for Direct Message
  - Call back for video share and upload GUI
- Performance improvements
  - Unread message management for friend request and direct message.
- Fixed
  - Scroll view disappearing from the screen.
  - Thumbnail on video list doesn't operate correctly.
- Important Notes
  - In Unity 4.6.3, make sure that you force graphics to be OpenGL ES in the player settings. (For iOS)

## 0.4.0
- Performance improvements
  - Show unread messages on group messenger.
  - Retry button on matchmaking.
- Fixed
  - Players name don't show up on matchmaking screen.
  - Can not post a new thread with image and text.

## 0.3.1
- Performance improvements
  - Show GUI with tab on MyVideo page after uploading the game video.
  - Fixed error when sharing video on Twitter
  - Game title will automatically be added to the game video title when sharing them on Youtube

## 0.3.0
- New Feature
  - [iOS] Game play video recorder, and share.
- Performance improvements
  - Show maximum player capacity on matchmaking GUI.
  - Add time out function for matchmaking.
- Fixed
  - [Android] App sometime does not launch from push notification.
  - [Android] Push notification icon do not display correctly on Lollipop.


## 0.2.7

- Fixed
  - [iOS] aps-environment being evaluated as development when publishing on the store.

## 0.2.6

- New Feature
  - Show Dialog box after tapping the push notification for direct message.
  - GroupMessage Tab
- Performance improvements
  - Delete unnecessary GUI for official user.
  - Go back to the previous GUI screen when Group Conference ends.
  - GUI improvements on thread screen.
  - Switched the Dialog design to "Holo Dark" for Android.
  - Movement improvements for push notification.
- Fixed
  - Host URL can not be acquired if a communication error occurred during initial launch.
  - Dialog error message.
  - Push notification icon settings for Android.

## 0.2.5

- New Feature
  - Provisioning API
  - Automated login function when relaunching the application.
- Fixed
  - [iOS]Auto rotation for image picker.

## 0.2.4

- Fixed
  - Changed the core part of AppSteroid to DLL

## 0.2.3

- New Feature
   - [iOS] Post-process function
   - Documents: How to use Leaderboard
- Performance improvements
  - Gray out the Call button during voice chat conference.
  - Add FASUser class for user management. (Separated from FAS class)
  - Add FASNotification Class for Push Notification management. (Separated from FAS class)
  - Add FASFriendship Class for friend management. (Separated from FAS class)
  - Add function to delete all messages on pair group automatically when unfriending a player.
- Fixed issue
    - [Android] Fixed bugs on push notification icon setting.
    - Fixed operation to update the profile on leaderboard after a player changes their own profile.

## 0.2.2

- Performance improvements
  - Ability to move around scene during voice chat.
  - Modified error message for voice chat on unity editor.
  - Trigger to delete pair group automatically when unfriending a player.
  - Smoother movements for scroll view.
  - Replaced icon shown on group message list.
  - Automatically create a pair group when forming a group with only two players.
  - Ability to transit to players profile from chat message GUI in pair group.

- Fixed issue
  - Error code listed on the documents.

## 0.2.1

- New Feature
    - Add function to add/edit images on a comment.
    - Pop up action sheet by press and hold on Group message and Group member.
    - Ability to copy user name and user code by press and hold on the text.
- Performance improvements
    - Updated context and improved timing to pop up error dialog.
    - Do not display deleted thread on Forum anymore.
- Fixed issue
    - Fixed system glitch showing unnecessary white lines on Forum GUI.
    - Fixed bug of not reflecting the changes on the screen when a user replace their profile image to a smaller image.
    - Add action to display an error message before accessing to the server when there was an invalid parameter.

## 0.2.0

- New Features
  - Matchmaking
    - Matchmaking Sample
  - Group Conference (Voice Chat)
  - Custom Message
  - Leaderboard Paging
  - Auto-save function for singed up users
  - Settings for the tab position when there are multiple tabs (Added selectedMode argument in FASGui.ShowGUI)
  - [Android] Auto generation function by GUI of the manifest file
- Fixed Issues
  - Display position of loading spinner
- Performance Improvements
  - Changed GUI on Profile

### 0.1.6

- New Features
  - Ability to display Leaderboard
  - Group Messaging
  - Color customization for GUI
  - Function to process event for each push notification operation. (In game chat, Direct Message, etc.)
- Performance Improvements
  - Add ability to unfriend
  - Precise display of GUI and improvements in performance

## 0.1.5

- New Features
  - Friendship Management
  -[Android] Documents and feature to save users information with backup manager.
- Fixed Issues
  - Changed MyProfile to appear on modal window.
  - [Android] Fixed an error of failing to get image when the display rotate while taking a photo.
  - [Android] Changed implementing method to not to override Unity Activity.
  - [Android] Fixed documents about creation of a manifest file.
- Performance Improvements
  - Precise display of GUI and improvements in management.

## 0.1.4

- New Features
  - Support landscape mode on screen.
- Fixed Issues
  - Fixed problem with push notification on Android.
- Performance Improvements
  - Precise display of GUI and improvements in management.

## 0.1.3

- New Features
  - Add function to save images on a comment.
- Fixed Issues
  - Fixed bug introduced when accessing a deleted thread.
- Performance Improvements
  - Precise display of GUI and improvements in management.


## 0.1.2

- New Features
  - Function to load and save user information who signed up previously.(FGC.LoadSignedUpUsers)
- Fixed Issues
  - [Android] Fixed transaction, so it will not get token for "Notification register" when GCM project ID and API is not setted.
  - Fixed the progress circle improperly displaying when returning to the app after suspending it with the home button.
  - Fixed deleted thread improperly displaying when switching to another thread after destroying it.
- Performance Improvements
  - Precise display of GUI and improvements in management.


## 0.1.1

- New Features
  - [Android] Display push notification message on screen.
  - [iOS] Function to save user information with keychain.
- Fixed Issues
  - Fixed broken image data [back_icon@2x]
- Performance Improvements
  - Don't have to set up host server URL anymore.
  - Precise display of GUI and improvements in management.


## 0.1.0
First Release
