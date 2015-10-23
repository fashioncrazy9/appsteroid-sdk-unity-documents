# Features

----------

- [AppSteroid Feature Introduction](#Features)
	- [Social Feature Service](#SocialFeatures)
		- [Game Forum](#GameForum)
		- [User Profile](#UserProfile)
		- [Friend Management](#FriendManagement)
		- [Group Message](#GroupMessage)
		- [In Game Chat](#InGameChat)
		- [Voice Chat/In Game Voice Chat](#VoiceChat)
		- [Play Video](#PlayVideo)
		- [Push Notification](#PushNotificationForSetting)
	- [App Promotion Service](#PromotionService)
    	- [App Info](#AppsInfo)
      	- [Official Forum](#OfficialForum)
    	- [Social Share](#SocialShare)
    	- [Event Promotion](#EventManagement)
      	- [Push Notification](#PushNotificationForPromotion)
    	- [App Gallery](#AppGallery)
	- [Game Management Support Service](#SupportService)
		- [Leaderboard](#Leaderboard)
		- [Matchmake](#Matchmaking)
		- [Customer Support](#CSR)
		- [Turn Based Game Support](#Turn-BasedGame)
		- [3D Avatar Service](#3DAvator)
	- [Basic Backend as a Service](#BackendService)
		- [User Authentication](#UserCertification)
		- [Social Integration](#SocialIntegration)
		- [Cloud Storage](#CloudStrage)
		- [Game Data Migration](#DataTransfer)
	- [WEB Console Service](#WebConsole)
- [How to Implement AppSteroid SDK](#Install)

---

## <a name="Features">AppSteroid Feature Introduction</a>
To use these features in your application, you need to implement AppSteroid SDK in your App. Check [How to Implement AppSteroid SDK](#Install).

### <a name="SocialFeatures">Social Feature Service</a>
Features to boost user retention and engagement. We have a result of big raise in user retention with our clients App. Making mobile game social is our main field.

#### <a name="GameForum">- Game Forum</a>
A space for app user to freely share information with the community. User can post text, images and share their play-videos on the thread.  

- [Use Forum GUI](./Use Fresvii GUI.md)
- What can be done on the web console
	- Create, edit and modify the forum as a official user, or modify an inappropriate comment on the forum. These operation can be done on the `forum` tab on the web console.
- Related API
	- [FASForum](./Specs/Spec-FASForum.md)

#### <a name="UserProfile">- User Profile</a>
Manage users profile  

- [Use profile GUI](./Use Fresvii GUI.md)
- What can be done on the web console
	- Developer can permanently suspend a bad user's account or for a certain period of time. Please check the `Users` tab on the web console.
- RelatedAPI
	- [FASUser](./Specs/Spec-FASUser.md)

#### <a name="FriendManagement">- Friend Management</a>
Allow users to create their own community by inviting friends, and form their own groups to communicate/play together inside the app. Users will have ability to invite others to start a online match.

- RelatedAPI
	- [FASFriendship](./Specs/Spec-FASFriendship.md)

#### <a name="GroupMessage">- Group Message</a>
A chat space for app users to talk/chat with other users. App users can post text, images, play-video and stickers.

- [Use group message GUI](./Use Fresvii GUI.md)
- Related API
	- [FASGroup](./Specs/Spec-FASGroup.md)

#### <a name="InGameChat">- In Game Chat</a>
Chat system which works inside the game.  

- [How to use in-game text chat](./Use In-Game Text Chat.md)
- Related API
	- [FASEvent](./Specs/Spec-FASEvent.md)
	- [FASGroup](./Specs/Spec-FASGroup.md)

#### <a name="VoiceChat">- Voice Chat/In Game Voice Chat</a>
Fresvii voice chat will support up to 4 players to have a conversation at the same time. Players can talk with friends within the game, during their game play. (Useful for FPS games, Board games, MMO games, and more.)
Players can also start a voice session from the user profile inside AppSteroid GUI.

- [How to use Group Conference (Voice Chat)](./Use Group Conference(VoiceChat).md)
- [How to use in-game voice chat](./Use In-Game Voice Chat.md)
- Related API 
	- [FASConference](./Specs/Spec-FASConference.md)
	- [FASEvent](./Specs/Spec-FASEvent.md)
	- [FASGroup](./Specs/Spec-FASGroup.md)

#### <a name="PlayVideo">- Play Video</a>
Users can record their game play and share it with the AppSteroid community or other major social media (Facebook, Twitter, email). Users who watched the video can also share it with the community or other major social medias. Keep track of playback count and like count. 
 
Please check the related API for method to use video recording GUI or video share GUI.

- Related API
	- [FASPlayVideo](./Specs/Spec-FASPlayVideo.md)

#### <a name="PushNotificationForSetting">- Push Notification</a>
- Direct Message: This can be used to announce event and important game information to the entire user community from the Web Console.

- Automated Messages: It works similarly to Direct Messages, only it will keep sending these messages as the users move into the new User Group.

- Channels: Channels are way to get code to respond to a SNS push notification, and act accordingly. Read more about Channels and push notifications here.


Push message will also be distributed at the following conditions.

* Notify users when there is an update on a subscribed thread.
* Notify users when there is a new Group Message.
* Notify users with a new friend request/accept.
* Notify users when their friend is requesting a match.

Related information: [About Push Event](https://github.com/fresvii/appsteroid-documents/blob/master/en/EventList.md)


To use push notification, you must set it up specifically for iOS and Android.

- Settings
	-  iOS
		1. [Register APNSCertificate](https://fresvii.zendesk.com/hc/en-us/articles/203512810-APNS-Certifiate-Tutorial)
		2. [Push Notification Settings (iOS)](./[Unity-iOS]Setting Up PushNotification.md)
	- Android
		1. [Push Notification Settings (Android)](./[Unity-Android]Setting Up PushNotification.md) 
- Send out push notification from the web console
	- Available from the `message` tab.
- Send message to a specific segment of users.
	- [How to use channel](https://fresvii.zendesk.com/hc/en-us/articles/203866590-What-is-Channel-and-How-to-Use-It-)
- Push Message Specification
	- [About Push Event](https://github.com/fresvii/appsteroid-documents/blob/master/ja/EventList.md)


### <a name="PromotionService">- App Promotion Service</a>
Features to promote applications. It helps increase user retention and user traffic between multiple apps.

#### <a name="AppsInfo">- App Info</a>
Developers can introduce other applications to their existing community.  End-users can check new apps, share the app with friends on social media or download the app you have introduced.

If the introduced application has implemented AppSteroid, Forum information and video's of the game will also be shared in the info page.  Even if the application did not implemented AppSteroid, developers will be able to introduce the App by registering it on the Web Console. (In this case, Forum info and videos will not be shared.)

#### <a name="OfficialForum">- Official Forum</a>
Open a new thread operated by the developer, and distribute app information to the user community. When the developer creates a new thread, all users will receive a push message once.  Afterward, only users who have followed the thread will receive update notifications.

- What can be done on the web console
	- You can create the official forum from the `Forum` tab.

#### <a name="SocialShare">- Social Share</a>
End-users can share the following contents to major social medias. URL to the store will automatically be attached when an user shares a content. Default sharing message can be modified on the Web Console by the developer.

- Contents that can be shared<br>- App Info<br>- Event<br>- Videos

- What can be done on the Web Console<br>- Localization setting can be done in `Localization` tab.

#### <a name="EventManagement">- Event Promotion</a>
Developers can promote an ongoing Event or upcoming Events to the community.
Event can be promoted in both AppSteroid community and App Gallery. Developers can direct end-users to a specific URL, and End-users will be able to share exiting events to friends via social media.

Collaborate this feature with Push Notification to boost user traffic, and introduce existing users to the next App.

- What can be don on the Web Console
  - Create and manage Events on the event tan.

#### <a name="PushNotificationForPromotion">- Push Notification</a>
Developers can either target a specific player, segment players or address to the entire game community with their announcement.

- What can be done on the web Console
	- Shoot messages from the `Message` tab.


#### <a name="AppGallery">- AppGallery</a>
App Gallery is a space to either promote your apps in an enclosed (Private) community, or share with others in an open (Public) community to earn advertising revenue. App Gallery is an opportunity for everyone to earn additional revenue and user.
 		 
- Public: Earn additional revenue by placing other developers application info.
- Private: Do not place any ads, instead use it for cross promoting own applications.

AppSteroid features user generated contents to draw more user intrest towards the App. Promotion will be done seamlessly within the user community, with user generated contents. Thus, we highly recommend developers placing Ad in AppGallery to implement AppSteroid to maximize their profit.


Currently, We provide space for advertisers to place the following Ads on public AppGallery.
 		 
- Video Ads (User generated game video or interstitial ad can be placed)
- Banner Ads (It will be placed in the community and App Gallery)
- Event Ads (Announce your game event on App Gallery)
- Community Ads (Show Forum information)

AppGallery has a potential to double the promotion profit by "running it privately on the house App, and placeing Ads on a public AppGallery".



### <a name="SupportService">Game Management Support Service</a>
Features mainly used to manage/monetize the game. As same as the Backend features, it will significantly reduce the cost of development to manage the app.

#### <a name="Leaderboard">Leaderboard</a>
Score management feature. Developers can show scores for Today, Weekly and Total, or also have multiple leaderboards for a single game. (e.g. score, level, time, item count, etc. within a single game).

- [Showing leaderboard GUI](./Use Fresvii GUI.md)
- [How to use leaderboard](./Use Leaderboard.md)
- What can be done on the web console
	- Creating, modifying and deleting the leaderboard can be done. Check the `Leaderboard` tab on the web console.
- Related API
	- [FASLeaderboard](./Specs/Spec-FASLeaderboard.md)

#### <a name="Matchmaking">Matchmake</a>
Matchmaker will automatically find the perfect opponents online with up to 16 players. “Play with friends” or “Play with the world” are provided as a default. A flexible filter settings can also be set up by the developer. “Play with same level”, “Play in the same region”, “Players with score under XX” and so on.

- [How to use Matchmake](./Use MatchMaking.md)
- Related API
	- [FASMatchMaking](./Specs/Spec-FASMatchMaking.md)
	- [FASStorage](./Specs/Spec-FASStorage.md)

#### <a name="CSR">Customer Support</a>
Feature to communicate/support app users through text. You can send messages to any users from the Web Console. All message logs between users and CSR can be checked on the Web Console as well.  
Once this feature is implemented into your app, Live Help button will appear on the top right corner of AppSteroid GUI in the message page. Users will be able to send message to the CSR through this Live Help button.

- [Use Customer Support](./GettingStarted.md)
	- See `CSR` on `FAS Settings`.

#### <a name="Turn-BasedGame">Turn Based Game Support</a>
Support turn-based game such as chess, poker, monopoly and more. Ability to integrate with event for social use. Users can automatically send push message to opponents to notify their turn is coming up.

- [How to use Matchmaking](./Use MatchMaking.md)(Refer to game context)
- Related API
	- [FASMatchMaking](./Specs/Spec-FASMatchMaking.md)
	- [GameContext](Specs/Spec-Models.md#GameContext)
	- [FASEvent](Specs/Spec-FASEvent.md)

#### <a name="3DAvator">3D Avatar Service</a>
A Unity-based system for creating and animating custom 3D characters (Avatar) which can be used in games. Over 300 avatar items and 50 animation data are available for free. You can also add unique movements with our original FBX formatted animation.

- [Use 3D Avatar with Frenbee](https://github.com/fresvii/frenbee-sdk-documents-en/wiki)


### <a name="BackendService">Basic Backend as a Service</a>
AppSteroid will greatly reduces server side development cost from game developers.

#### <a name="UserCertification">User Authentication</a>
Automatically creates and maintains accounts with an 8 to 9 digit unique ID for all players without arduous UI. App users doesn't have to setup any user ID nor Password.

- Automated User Authentication
	-  See `Auto relogin silently on resume` in [GetStarted](./GettingStarted.md).

#### <a name="SocialIntegration">Social Integration</a>
Store SNS (Facebook, Twitter) account ID and link information with app user. 
Check the related API for "how to use".

- Related API
	- [Setting SNSAccount](./Specs/Spec-FASUser.md#FASUser.SetSnsAccount)
	- [Referring SNSAccount](./Specs/Spec-FASUser.md#FASUser.GetSnsAccountList)
	- [Deleting SNSAccount](./Specs/Spec-FASUser.md#FASUser.DeleteSnsAccount)

#### <a name="CloudStrage">Cloud Storage</a>
A Key-value-storage area mainly used to store game data.  
Check the related API for "how to use".

- Related API
	- [FASStorage](./Specs/Spec-FASStorage.md)

#### <a name="DataTransfer">Game Data Migration</a>
Enable data migration between devices with the same OS.

- iOS Device -> iOS Device
	- Enable user data migration by using the same Apple account
- Android Device -> Android Device
	- Enable user data migration by using the same Google account.



### <a name="WebConsole">WEB Console Service</a>
Ability for your entire team to access and manage users, push message, app analytics, leaderboard, forum and many other data.
For more information, please see [About WebConsole](./WebConsole.md).


## <a name="Install">How to Implement AppSteroid SDK</a>
Please refer to [Get Started](./GetStarted.md) for details.

