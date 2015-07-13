# FASLeaderboard Specifications

last update at 2014/10/15

----------

## Introduction

## <a name ="FASLeaderboardClass">FASLeaderboard Class</a>
Class to operate Leaderboard

----------

## Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASLeaderboard](#FASLeaderboardClass)|Class to operate leaderboard |

----------

### Methods

|Name|Description|
|------|-----|
|[FASLeaderboard.SetTotalizationClockUtcOffset](#FASLeaderboard.SetTotalizationClockUtcOffset)| Setup UTC offset for time to tally Leaderboard. (Default = 0) |
|[FASLeaderboard.SetDailyTotalizationStartTime](#FASLeaderboard.SetDailyTotalizationStartTime)| Setup Daily Starting time to tally Leaderboard. (Default = 00:00) |
|[FASLeaderboard.SetWeeklyTotalizationStartTime](#FASLeaderboard.SetWeeklyTotalizationStartTime)| Setup Weekly starting time to tally Leaderboard. (Default = Sunday, 00:00) |
|[FASLeaderboard.GetLeaderboards](#FASLeaderboard.GetLeaderboards)| Get list of leaderboards from app. You can creat leaderboards from the web console. |
|[FASLeaderboard.GetLeaderboard](#FASLeaderboard.GetLeaderboard)| Get Leaderboard|
|[FASLeaderboard.ReportScore](#FASLeaderboard.ReportScore)| Report Score|
|[FASLeaderboard.GetScore](#FASLeaderboard.GetScore)| Get Score|
|[FASLeaderboard.DeleteScore](#FASLeaderboard.DeleteScore)| Delete Score|
|[FASLeaderboard.GetUserScores](#FASLeaderboard.GetUserScores)| Get list of Score|
|[FASLeaderboard.GetRanking](#FASLeaderboard.GetRanking)|Get Ranking (list of ranks)|
|[FASLeaderboard.GetUserRanking](#FASLeaderboard.GetUserRanking)|Get User Ranking (list of ranks)|

### <a name ="FASLeaderboard.SetTotalizationClockUtcOffset">FASLeaderboard.SetTotalizationClockUtcOffset</a>

Setup UTC offset for time to tally Leaderboard. (Default = 0)

  public static void FASLeaderboard.SetTotalizationClockUtcOffset(int utcOffset)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|utcOffset|int|Offset time|

### <a name ="FASLeaderboard.SetDailyTotalizationStartTime">FASLeaderboard.SetDailyTotalizationStartTime</a>

Setup Daily Starting time to tally Leaderboard. (Default = 00:00)

  public static void FASLeaderboard.SetDailyTotalizationStartTime(int hour, int minute)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|hour|int|hour (Default = 0)|
|minute|int|minute (Default = 0)|

### <a name ="FASLeaderboard.SetWeeklyTotalizationStartTime">FASLeaderboard.SetWeeklyTotalizationStartTime</a>

Setup Weekly starting time to tally Leaderboard. (Default = Sunday, 00:00)

  public static void FASLeaderboard.SetWeeklyTotalizationStartTime(System.DayOfWeek dayOfWeek, int hour, int minute)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|dayOfWeek|System.DayOfWeek|Day of the Week(Default = Sunday)|
|hour|int|hour (Default = 0)|
|minute|int|minute (Default = 0)|

### <a name ="FASLeaderboard.GetLeaderboards">FASLeaderboard.GetLeaderboards</a>

Get Leaderboard List

   public static void GetLeaderboards(Action<IList<Leaderboard>, Error> callback)
   public static void GetLeaderboards(uint page, Action<IList<Leaderboard>, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|page|uint|The Page number you will get (optional)|
|callback|Action\<IList\<Leaderboard>, Error>|This is a Delegate with an argument of Leaderboard model list and error info that will be called when the rocess to get list of leaderboard is completed.|

#### Example

   FASLeaderboard.GetLeaderboards(delegate(IList<Leaderboard> leaderboards, Error error)
   {
     if(error == null)
     {
       // To go through process for Leaderboard List
     }
   });

### <a name ="FASLeaderboard.GetLeaderboard">FASLeaderboard.GetLeaderboard</a>

Get Leaderboard

 public static void GetLeaderboard(string leaderboardId, Action<Leaderboard, Error> callback)
 public static void GetLeaderboard(string leaderboardId, uint page, Action<Leaderboard, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|leaderboardId|string|The Leaderboard ID you will get|
|page|uint|The Page number you will get (optional)|
|callback|Action\<Leaderboard, Error>|This is a Delegate with an argument of Leaderboard model and error info that will be called when the process to get leaderboard is completed.|
#### Example

   FASLeaderboard.GetLeaderboard(　leaderboardId, delegate(Leaderboard leaderboard, Error error)
   {
     if(error == null)
     {
       // To go through process for Leaderboard
     }
   });


### <a name ="FASLeaderboard.ReportScore">FASLeaderboard.ReportScore</a>

Transmit Score

 public static void ReportScore(string leaderboardId, int value, Action<Score, Error> callback)
 public static void ReportScore(string leaderboardId, int value, System.DateTime createdAt, Action<Score, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|leaderboardId|string|The leaderboard ID you will get|
|value|int|The score you will transmit|
|createdAt|System.DateTime|Creation date (optional)|
|callback|Action\<Score, Error>|This is a Delegate with an argument of Score model and error info that will be called when the process to transmit score is completed.|


### <a name ="FASLeaderboard.GetScore">FASLeaderboard.GetScore</a>

Get Score

 public static void GetScore(string leaderboardId, string scoreId, Action<Score, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|leaderboardId|string|The leaderboard ID you will get|
|scoreId|string|The score ID you will get|
|callback|Action\<Score, Error>|This is a Delegate with an argument of Score model and error info that will be called when the process to get leaderboard is completed.|

#### Example

   FASLeaderboard.GetScore(　leaderboardId, scoreId,　delegate(Score score, Error error)
   {
     if(error == null)
     {
       // To go through process for Score
     }
   });


### <a name ="FASLeaderboard.DeleteScore">FASLeaderboard.DeleteScore</a>

Delete Score

 public static void DeleteScore(string leaderboardId, string scoreId, Action<Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|leaderboardId|string|The Leaderboard ID you will delete|
|scoreId|string|The score ID you will delete|
|callback|Action\<Error>|This is a Delegate with an argument of error info that will be called when the process to delete score is completed.|

#### Example

   FASLeaderboard.DeleteScore(　leaderboardId, scoreId,　delegate(Error error)
   {
     if(error != null)
     {
      // To go through process for Error
     }
   });


### <a name ="FASLeaderboard.GetUserScores">FASLeaderboard.GetUserScores</a>

Get user score list

 public static void GetUserScores(string leaderboardId, string userId, System.DateTime startTime, Leaderboard.SubmissionType sortBy, uint page, Action<IList<Score>, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|leaderboardId|string|Leaderboard ID to get the User's score from|
|userId|string|User ID to get the list from|
|span|FASLeaderboard.TotalizeSpan|(optional) Interval to get list { Daily, Weekly, Total }|
|startTime|System.DateTime|Starting time to get the list (optional)|
|sortBy|Leaderboard.SubmissionType|Set with BestScore or RecentScore, the default setting is BestScore. Whether to sort the score from high to low or from low to high will depend on the setting of Leaderboard (optional)|
|page|uint|Page number to get (optional)|
|userId|string|User ID to get the list from|
|callback| Action\<IList\<Score>, Error>|This is a Delegate with an argument of Score model list and error info that will be called when the process to get score list is completed.|

#### Example

   FASLeaderboard.GetUserScores(　leaderboardId, userId,　delegate(IList<Score> scores, Error error)
      {
         if(error == null)
        {
           //　To go through process
        }
     });


### <a name ="FASLeaderboard.GetRanking">FASLeaderboard.GetRanking</a>

Get Ranking

 public static void GetRanking(string leaderboardId, System.DateTime startTime, bool onlyFriends, Action<IList<Rank>, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|leaderboardId|string|Leaderboard ID to get the Ranking from|
|span|FASLeaderboard.TotalizeSpan|(optional) Interval to get list { Daily, Weekly, Total }|
|startTime|System.DateTime|Starting time to get the list (optional)|
|onlyFriends|bool|(optional)Only show friend's result (The default is false)|
|callback| Action\<IList\<Rank>, Error>|This is a Delegate with an argument of Score model list and error info that will be called when the process to get core list is completed.|

#### Example

   FASLeaderboard.GetRanking(leaderboardId, startTime, delegate(IList<Rank> ranking, Error error)
   {
      if(error == null)
      {
        //　To go through process
     }
   });


### <a name ="FASLeaderboard.GetUserRanking">FASLeaderboard.GetUserRanking</a>

Get User Ranking

 public static void GetUserRanking(string leaderboardId, string userId, System.DateTime startTime, bool onlyFriends, Action<Rank, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|leaderboardId|string|Leaderboard ID to get the Ranking from|
|userId|string|User ID to get the list from|
|span|FASLeaderboard.TotalizeSpan|(optional) Interval to get list { Daily, Weekly, Total }|
|startTime|System.DateTime|Starting time to get the list (optional)|
|onlyFriends|bool|（(optional)Only show friend's result (The default is false)|
|callback| Action\<Rank, Error>|This is a Delegate with an argument of Score model list and error info that will be called when the process to get score list is completed.|

#### Example

   FASLeaderboard.GetUserRanking(leaderboardId, userId, startTime, delegate(Rank rank, Error error)
   {
      if(error == null)
     {
      //　To go through process
   }
   });
