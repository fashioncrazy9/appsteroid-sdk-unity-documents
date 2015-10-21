#What is the AppSteroid Console, and why do I care? 

The AppSteroid console allows you to manage these major categories.

1. Your application details, including keys, certificates, and tokens.
2. The content your users generated, including forums, and videos.
3. Leaderboards, and events.
4. View user analytics, and export other server side data.
5. Perform customer service tasks for your end users.
6. Manage additional team members to access the console.
7. Billing information.



##Quick Start:  How do I get my app working, and connecting to AppSteroid?

After logging in, at the Apps Dashboard, click on the large Plus symbol, to Add New App.  In the New App Dialog, type in the name of your App.  Select a .JPG that you would like to use as the Icon for your App.  And lastly, select a Genres for your App.

This will take you to your Applications Page.  Ensure that the application you have just created is the one that is selected in the upper left hand corner of the screen.

You should be on the “Dashboard” screen, and you can see the ID, and Secret Token of your application.  This App ID is the Uuid that is required by the AppSteroid SDK to communicate with the backend service.  You must ensure that these are included in your APP.  You can find more explicit instructions on how to do this in the SDK documents.  Look at the file called GetStarted.md for your specific SDK.

At this point, you have basic functionality of AppSteroid in.  If you want push notifications, CSR support features, and some other tweaks to improve your user experience keep reading.  But this may be a good place to just test that your Application actually works, and can connect to the AppSteroid Back end services.



----------

##The Web Console

After logging in with your credentials, you will be at the Apps Dashboard.  From the Apps Dashboard you can perform these functions.

1. Create a new app
    - Click on the large Plus Sign, with “Add New App” under it.
2. Manage an existing app
    - Click on the app you want to manage.
3. Un-Delete an App
    - If you have an app that you marked to be deleted, it will show up after your live Apps.  Click on an app you want to undelete.  Apps stay here for seven days before they are purged.
4. Manage your profile with Account / Team settings.
    - Click on your developer name on the upper right side of the screen, and Select Account / Team Settings.
5. Change your identity to a team, or back to developer mode.
    - Select teams by clicking on your developer name on the upper right side of the screen.  From there you can switch to a team, create a new team, or switch back to developer mode.
6. Logout
    - To logout, click on your developer name on the upper right side of the screen, and select Logout.
    


###More App "Settings"
After you have logged in, and selected an Application from the App Dashboard, click on Settings.

######General
  * App Settings: From here you can change the app name, app icon or add more Genres to your application.  Adding genres will help people find other games that they like based on what Genres classification your game has. Note: The app name entered here will only be used on the Web Console. To change the app name shown to end-users, please go to Localization tab end edit the App Title.
  
  * User Default Settings: The Default User name is what user's names will look like when they first sign in to the game.  A number will be added to the end of this default user name, so that there are no duplicates.  Hopefully your users will customize their default user name.

######Localization
  * Locale: Select a default Language to be used in your App.
  
  * App Settings: You can edit your app title, and App description.  These information will be shown to end-users for advertisement purpose.
  
  * Text Settings on Sharing: The default message used when an end-user shares the application to major social networks.

######Push Notification
We will now set up Push Notifications for your app.  Select the Push Notifications tab at the top of the page. 

For Android devices, you need to provide your GCM API Key.  If you haven’t got a GCM Key, we would suggest go to [this page] (https://support.google.com/googleplay/android-developer/answer/2663268?hl=en) and following the directions to get your GCM API Key.

For iOS devices, you will need to enter a key for production, and if you want to use the Sandbox test environment, you will also need a key for Development as well.  You can learn about getting these keys from [this page] (https://fresvii.zendesk.com/hc/en-us/articles/203512810-APNS-Certifiate-Tutorial).

Please see [this document](https://github.com/fresvii/appsteroid-documents/blob/master/en/EventList.md) to check the definition of push event.

######CSR
Lastly, configuring your Customer Support options.  You can do this from the CSR tab.  You can select an image, choose a Name, and a Description.  This description will show up on the profile page of a CSR user within AppSteroid.

There are additional options you can set for how to manage Friend Requests, and Group messages for CSR members.

Related Document: [AppRegistration on Web Console](AppRegistrationOnWebConsole.md)


----------


##Application Panel

To get to the application panel for an individual application, just log into your account, and select  the application you want to work with.  From this Dashboard, you can get back to the Apps Dashboard, by clicking on the Fresvii Logo on the upper left corner of the pane.  To switch Apps, you can just select them from the pull down menu just below this.

If you don’t see the application you are looking for, you may need to go back to the App Dashboard, and switch to the team that manages that app. 



####App Information
Here you will see the ID of your App, also referred to as the Uuid, along with the Secret Token.  This information needs to be entered into your SDK, so that your application can communicate correctly with the AppSteroid Backend services.
Related Document: [GetStarted with AppSteroid](GetStarted.md)
Additional metrics, such as # of users, number of forum threads, number of Videos, and playback counts are also found here on this page.



####Forum
The forum pane allows you to moderate all the forum threads that have been posted by your users.  The Forum only has two levels of data.  The main thread, and comments to the thread.  There are no comments to comments.  In fact the first comment in a thread, is the main thread comment.  The forum threads are listed in order of the most recent comment to the thread.  Not the most recent creation of the thread.  You can create/delete threads or comments from this pane.  You can also play the video’s, and see the images posted by just clicking on the thumbnail of the content.  You can also view the posters user information, by clicking on his name or icon.  (See User Information below).

######How to navigate the forum?
You can select how many you want to view by clicking on the “View” button on the upper right of the screen.  To see the comments to the thread just click on the show comments button next to the thread.  For very long comments, you have to click on “Edit” to see the comment.  If you are viewing the comments, and want to go back to the listing of threads, click on the breadcrumb “Forum” at the top of the pane.

######New Threads, and Comments
To create a new thread, or comment click on the button on the upper left corner of the pane.  You must be in viewing the comments in a thread, to post a new comment to it.

######Deleting Threads, and comments.
Find the thread or comment you want to delete, and then click on the down arrow on the far left of the button on the same line, and select delete.  If you delete a thread, all the comments within it, will also be deleted.



####Videos
This page will show you all the video’s uploaded to AppSteroid, regardless of what their ultimate destination is (aka. “Reference”). 

If you want to Upload videos because your game doesn’t have the feature to automatically download them yet, you can do this by clicking on the New Video button in the Upper Right corner of the Screen.
  
You can view the Author of the video by clicking on their name, or icon.  You can also watch the video by clicking on it, or by selecting the Play button on the far right.  If the video was posted to a forum, you can click on the word “Forum” next to the video, and be taken straight to the forum comment that the video was posted on.  You can also Download, and/or delete the video, by clicking on the small down arrow next to the “Play” button on the far right.  You can navigate the video pages using the pagination controls on the bottom, and by changing the “view” number on the top right portion of the pane.



####Messages
Allows you too see and modify how APNS, and GPNS work.  From this pane you can send direct messages, or automate the sending of them.

######Direct Messages
To send a push notification manually, click on the “Send a Message” button on the far left.  This will pop up a dialog allowing you to edit this information.

  * Subject: is what the user will see as the subject of the push notification.
  * Text: is the body of the push message, what they will see after they decide to read it.
  * User Group: is whom you want the message to go out to.  If you select a users group, it will tell you the definition of this group, for example “New Users” are people that have installed the game 1-3 days.
  * Send Date: You can choose between right now, or a future time.  
  * Create / Cancel: If you click on create, this push notification will go out immediately, if it was scheduled for now.  Make sure you don’t have any typos, errors in bad judgement, etc.  Your content is now live.

#####Automated Direct Messages
Works similarly to Direct Messages, only it will keep sending these messages as the users move into the new User Group.  To create a new Automated Direct message, click on “Schedule an Automated Direct Message”.  These automated messages keep going until you decide to delete them.  To delete a scheduled automated direct message, click on the down arrow to the right of the “Edit” button, and select delete.  If you want to change the content, or timing of the message you can also edit this, by pressing the “edit “ button. 

#####Channels
Channels are way to get code to respond to a SNS push notification, and act accordingly.  Read more about Channels and push notifications [here](https://fresvii.zendesk.com/hc/en-us/articles/203866590).



####Leaderboards
If you haven’t read about Leaderboards, you can read about them [here](https://github.com/fresvii/appsteroid-sdk-ios-documents/blob/master/en/GetStarted/GetStarted-Leaderboard.md) for iOS and [here](https://github.com/fresvii/appsteroid-sdk-unity-documents/blob/master/en/Use%20Leaderboard.md) for Unity.  The important thing to note if you didn’t read those, is that Leaderboards work on a weekly basis.  And events are a different grouping of leaderboards.  You can have multiple leaderboards for you App.  All scores are kept, and the “Leaderboard”, is just a particular view and sorting order of all the scores in that leaderboards time period.

######Leaderboards
To actually see the ranking on a leaderboard, you must select it by clicking the name from the leaderboard list, or clicking on the “Show” button, and then clicking on the “Rankings” tab.  This will show you the leaderboard ranked in the configuration chosen for that leaderboard.  If you wish to change the configuration of that leaderboard, you need to click on the leaderboard tab, and then click on Edit.  Clicking on the “Scores” tab will show you all the “scores” recorded that are selected for evaluation by that particular leaderboard you have selected.

######Events
Events are a different temporal view of a leaderboard.  It also included a banner and a description of the event.



###Users
There are two main views of users.  The active users simply called “users”, and the banned users.  Banned users is just a filter, as if a user is banned, they will still show up in the users pane.  To access a bunch of CSR controls, you will want to push the CSR button at the top right of the pane.  It is documented below.

######Users and Banned Users
There are a lot of things that you can do from these pages, but the behavior is the same regardless if you are in banned or not.  Each person that has used the game will be here.  You can search for the user by using the search box in the left side of the Users Pane.  Pagination controls are on the bottom of the pane.  You can click on column headings to sort by those particularly values.  If you click on the small down arrow next to the Show User button, you can:

1. Show User Info / User Information
    - From this screen, you have several new tabs, and can see all the information about a user as well as. 
2. Send Message
    - sends the entered text to the user via Push Message Notification Service.
3. Ban
    - If the user isn’t currently banned, you will select how long the suspension will last for.  If the user is banned, you will be able to cancel the suspension for this user.
4. Friends
    - From this tab, a list of all the users friends can be seen.  This list is just like any other users list, you can click on the users, or button to the left to continue traversing the tree of friends.
5. Comments
    - This will show all the forum threads started, and comments to threads that this user has made.  Clicking on the individual comment will take you to that forum thread.
6. Received Messages
    - No navigation is available here, it just is showing you the data received.
7. Send Friend Request
    - Clicking on this will send a friend request from the apps CSR to this user.
8. Play Stats
    - All the data gathered (besides game data), that has been captured for this user.
9. Send Message 
    - This will send a chat message to the user.  After sending this chat message, it will be visible on that users Chat Message Log.

######CSR Information
This button essentially is the same as a user button, but for the CSR user.  From here you can see everything that a CSR has done in the community of your App, by navigating the same way you would for any other user. 


###Analytics
Most of the Analytics can either be viewed as a Chart, or as a table of paginated data.  The charts are at the top of the page, and you can scroll down to see the data, and select how many rows you want to see at one time.  You can also Export the data, by clicking on the Export button on the top right portion of the screen.  We have the following metrics tabs available from this screen.

1. Dau/Total Users
    - The data of when you have send push message will be marked red. You will be able to check how effective your push notification was.
2. MAU
    - Either check the regular MAU or average MAU through the year.
3. Play Stats
    - You can check/add play stats. Play stats can be seen on the player's profile page.
4. Video Playback Count
    - Check how many view did the video got.



###Settings
If you haven’t read the Quick Start, and “More Settings” section above, you can do this to get a better understanding of how these values affect your product.

######General
  * App Name: This name will only be used on the Web Console and it will not be seen by the end-users. The app title entered in "Localization" page will be seen by the end-users.
  * App Icon: This icon is used for Dashboard icon and Advertisement feature.
  * Default Locale: If your client's language setting is not supported by your App, you may set a "default" language. This "default" language will be used in this condition.
  * App Genres: You can add your app to multiple Genres, just click on the + button to open up more category space
  * Banner Image: This banner is used for the advertisement feature

######Default User Name 
The Default Username is what user's names will look like when they first launch the app.  A number will be added to the end of this default user name, so that there are no duplicates.  Hopefully your users will customize their default user name.

  * Default Username: This default user name is automatically used when a new user is created.
  * On Name Duplication: Select to either return an error, or add a serial number. We recommend to add serial number.
  * Default User Profile Image: User's default profile picture when they launch the app.

######Localization
You can set up each content on this page per local language. Click the "Add New Local Settings" to add local language. Once you add a new local language, you can select it from the dropdown manu.

  * Locale: Select a default Language to be used in your App. 
  * App Settings: You can edit your app title, and App description.  These information will be shown to end-users for advertisement purpose.
  * Text Settings on Sharing: The default message used when an end-user shares the application to major social networks.

** Regards to the Facebook privacy policy, default message will not be shown on Facebook share. Users will have to enter text manually.

  * App: Default message used when an end-user shares an App to SNS from the app description page.
  * Event: Default message used when an end-user shares an App to SNS from the Event page.  If the event contains a URL, that URL will be included in the share text. If not, the URL to the app store will be used instead.
  * Video: Default message used when an end-user shares a Video to SNS from either the video list or play screen.

######Push Notification
This is where you will enter your APNS, and GCM certificates and keys.  
For Android devices, you need to provide your GCM API Key.

  * If you haven’t got a GCM Key, we would suggest to go [here] (https://support.google.com/googleplay/android-developer/answer/2663268?hl=en) and follow the directions to get your GCM API Key.
  
  * For iOS devices, you will need to enter a key for production, and if you want to use the Sandbox test environment, you will also need a key for Development as well.  You can learn about getting these keys from [here] (https://fresvii.zendesk.com/hc/en-us/articles/203512810-APNS-Certifiate-Tutorial)

######CSR
The CSR user is just like any other user for you game, except…. you have admin control and power to edit, and delete comments, ban users, etc…  You should make sure your community understand that this user represents your company.  You can configure the name, Icon, and some other options from this tab.

######EULA
You can setup/modify the End User License Agreement for AppSteroid.
You can prepare multiple version for iOS, Android and regions.

######Export Data
This tab allows you to download all of your User Data, as well as your Leaderboards, and Key Value stores (Cloud Storage Data), for your ap.  At this time there is no way to export your forums, or other user content.

######Advanced
If you are the owner of this app, this is where you can delete this app.  If you are not the owner, the Advanced tab will not show up.


----------


##What are Teams, and how do they work?
Teams are how you associate different developers with different product groups.  The person who creates the team, is the “owner” of this team.  The owner is the only person who can access the billing section of their team. 

######Important Note
  * You cannot move an application from one team to another.
  
  * The owner cannot be changed without contacting Fresvii.  However the owner can add additional team members, and give them either Admin, or Normal roles.

  * A normal developer can view and change app configuration settings.  An admin can do that, plus add and delete members.

######Account Profile
After logging in, and selecting your use name, followed by Account/Team settings, you can change manage these items, by selecting the category on the left..  To go back to the Application Dashboard, click on the Fresvii Logo on the upper left part of the panel.

1. Profile
    - Enter your Name, Email address and Organization name here.
2. Password
    - Enter your Current Password, to change and confirm your new password.  Please choose a secure password that is 10 characters long.  If you select a password that is in our dictionary, you may be asked to select a different password.
3. Account
    - Time Zone: Set your local time zone.
    - Connected Accounts: Connect your Facebook Github and Twitter accounts.
4. Billing
    - Credit Card Number  (Only shows last 4 digits).
    - Expiration date.
    - Usage in this month.  Shows what your projected bill will be for the following month.
    - Shows your payment history.

######Team Settings
After this marker, all of your teams will be shown, which you can select to bring up the team management interface.

1. TEAM NAME
    - From this page you can add a new developer, in either an Admin or Normal role, by pressing the “Add New Member” button at the top right.  Or you can select from the following tabs.
2. Members
    - Allows you to view members and their roles, or resend invitations that have not been accepted at this time.
3. Profile
    - Allows you to change the name of the team.
4. Transfer Ownership
    - Only the owner can take this action. Select another team member to be the next owner.
5. Billing
    -  Note, this billing information is separate from your developer profile billing information, but the functionality is the same.