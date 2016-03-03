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

#### Leaderboard
|Name|Description|
|------|-----|
|[FASLeaderboard.SetTotalizationClockUtcOffset](#FASLeaderboard.SetTotalizationClockUtcOffset)| Setup UTC offset for time to tally Leaderboard. (Default = 0) |
|[FASLeaderboard.SetDailyTotalizationStartTime](#FASLeaderboard.SetDailyTotalizationStartTime)| Setup Daily Starting time to tally Leaderboard. (Default = 00:00) |
|[FASLeaderboard.SetWeeklyTotalizationStartTime](#FASLeaderboard.SetWeeklyTotalizationStartTime)| Setup Weekly starting time to tally Leaderboard. (Default = Sunday, 00:00) |
|[FASLeaderboard.GetLeaderboardList](#FASLeaderboard.GetLeaderboardList)| Get list of leaderboards from app. You can creat leaderboards from the web console. |
|[FASLeaderboard.GetLeaderboard](#FASLeaderboard.GetLeaderboard)| Get Leaderboard|
|[FASLeaderboard.ReportScore](#FASLeaderboard.ReportScore)| Report Score|
|[FASLeaderboard.GetScore](#FASLeaderboard.GetScore)| Get Score|
|[FASLeaderboard.DeleteScore](#FASLeaderboard.DeleteScore)| Delete Score|
|[FASLeaderboard.GetUserScores](#FASLeaderboard.GetUserScores)| Get score list from specific user|
|[FASLeaderboard.GetRanking](#FASLeaderboard.GetRanking)| Get score list|
|[FASLeaderboard.GetUserRank](#FASLeaderboard.GetUserRank)| Get user rank|

#### Eventboard
|Name|Description|
|------|-----|
|[FASLeaderboard.GetEventList](#FASLeaderboard.GetEventList)|Get event list|
|[FASLeaderboard.GetEvent](#FASLeaderboard.GetEvent)|Get detail info from a specified event|
|[FASLeaderboard.GetEventboardList](#FASLeaderboard.GetEventboardList)|Get eventboard list from a specified event|
|[FASLeaderboard.GetAllEventboardList](#FASLeaderboard.GetAllEventboardList)|Get event board list from all event|
|[FASLeaderboard.GetEventboard](#FASLeaderboard.GetEventboard)|Get detail info from a specified eventboard|
|[FASLeaderboard.GetEventboardRanking](#FASLeaderboard.GetEventboardRanking)|Get score list from eventboard|
|[FASLeaderboard.GetEventboardUserRank](#FASLeaderboard.GetEventboardRanking)|Get rank from a specific user|

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

### <a name ="FASLeaderboard.GetLeaderboardList">FASLeaderboard.GetLeaderboardList</a>

Get Leaderboard List

     public static void GetLeaderboardList(uint page, Action < IList < Leaderboard > , Error> callback)
   
#### Parameters
|Name|Type|Description|
|------|------|-----|
|page|uint|The Page number you will get (optional)|
|callback|Action\<IList\<Leaderboard>, Error>|This is a Delegate with an argument of Leaderboard model list and error info that will be called when the rocess to get list of leaderboard is completed.|

#### Example

    FASLeaderboard.GetLeaderboardList((leaderboards, error)=>
    {
        if(error == null)
        {
            //	リーダーボードのリストの処理を行う
        }
    });

### <a name ="FASLeaderboard.GetLeaderboard">FASLeaderboard.GetLeaderboard</a>

Get Leaderboard

    public static void GetLeaderboard(string leaderboardId, Action < Leaderboard, Error > callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|leaderboardId|string|The Leaderboard ID you will get|
|callback|Action\<Leaderboard, Error>|This is a Delegate with an argument of Leaderboard model and error info that will be called when the process to get leaderboard is completed.|

#### Example

    FASLeaderboard.GetLeaderboard(leaderboardId, (leaderboard, error)=>
    {
        if(error == null)
        {
            //	リーダーボードの処理を行う
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

    FASLeaderboard.GetScore(leaderboardId, scoreId, (score, error)=>
    {
        if(error == null)
        {
            //	スコアの処理を行う
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

    FASLeaderboard.DeleteScore(leaderboardId, scoreId, (error)=>
    {
        if(error != null)
        {
            //	エラー処理を行う
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

    FASLeaderboard.GetUserScores(leaderboardId, userId, (scores, meta, error)=>
    {
        if(error == null)
        {
            // 処理を行う
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

    FASLeaderboard.GetRanking(leaderboardId, startTime, (ranking, meta, error)=>
    {
        if(error == null)
        {
            // 処理を行う
        }
    });


### <a name ="FASLeaderboard.GetUserRank">FASLeaderboard.GetUserRank</a>

Get User Rank

    public static void GetUserRank(string leaderboardId, string userId, System.DateTime startTime, bool onlyFriends, Action<Rank, Error> callback)

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

    FASLeaderboard.GetUserRank(leaderboardId, userId, startTime, (rank, error) =>
    {
        if(error == null)
        {
            // 処理を行う
        }
    });

### <a name ="FASLeaderboard.GetEventList">FASLeaderboard.GetEventList</a>

Get event list

    public static void GetEventList(Fresvii.AppSteroid.Models.GameEvent.Status status, Action<IList<Fresvii.AppSteroid.Models.GameEvent>, Fresvii.AppSteroid.Models.ListMeta, Fresvii.AppSteroid.Models.Error> callback)
    public static void GetEventList(uint page, Fresvii.AppSteroid.Models.GameEvent.Status status, Action<IList<Fresvii.AppSteroid.Models.GameEvent>, Fresvii.AppSteroid.Models.ListMeta, Fresvii.AppSteroid.Models.Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|page|uint|(optional) page number to get|
|status|Fresvii.AppSteroid.Models.GameEvent.Status|Game event status（Upcoming, Ongoing, Past）|
|callback|Action \<IList \<Leaderboard>,  Fresvii.AppSteroid.Models.ListMeta, Error>|This is a Delegate with an argument of GameEvent model list, error info and meta info that will be called when the process to get game event list is completed.|

#### Example

    FASLeaderboard.GetEventList((gameEvents, listMeta, error) =>
    {
        if(error == null)
        {
            // To go through process
        }
    });

### <a name ="FASLeaderboard.GetEvent">FASLeaderboard.GetEvent</a>

Get detail info of game event

    public static void GetEvent(string eventId, Action<Fresvii.AppSteroid.Models.GameEvent, Fresvii.AppSteroid.Models.Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|eventId|string|ID of GameEvent to get|
|callback|Action \<GameEvent, Error>|This is a Delegate with an argument of GameEvent model and error info that will be called when the process to get game event info is completed.|

#### Example

    FASLeaderboard.GetEvent((gameEvent, error) =>
    {
        if(error == null)
        {
            // To go through process
        }
    });


### <a name ="FASLeaderboard.GetEventboardList">FASLeaderboard.GetEventboardList</a>

Get eventboard list

    public static void GetEventboardList(string gameEventId, Action<IList<Fresvii.AppSteroid.Models.Eventboard>, Fresvii.AppSteroid.Models.ListMeta, Fresvii.AppSteroid.Models.Error> callback)
    public static void GetEventboardList(uint page, string gameEventId, Action<IList<Fresvii.AppSteroid.Models.Eventboard>, Fresvii.AppSteroid.Models.ListMeta, Fresvii.AppSteroid.Models.Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|page|uint|(Optional) page number to get|
|gameEventId|string|game event ID|
|callback|Action \<IList \<Eventboard>,  Fresvii.AppSteroid.Models.ListMeta, Error>|This is a Delegate with an argument of eventboard model list, error info and meta info that will be called when the process to get eventboard list is completed.|

#### Example

    FASLeaderboard.GetEventboardList(gameEvent.Id, (eventboards, listMeta, error) =>
    {
        if(error == null)
        {
            // To go through process
        }
    });

### <a name ="FASLeaderboard.GetAllEventboardList">FASLeaderboard.GetAllEventboardList</a>

Get all eventboard list without specifying a game event

    public static void GetAllEventboardList(Action<IList<Fresvii.AppSteroid.Models.Eventboard>, Fresvii.AppSteroid.Models.ListMeta, Fresvii.AppSteroid.Models.Error> callback)

    public static void GetAllEventboardList(uint page, Action<IList<Fresvii.AppSteroid.Models.Eventboard>, Fresvii.AppSteroid.Models.ListMeta, Fresvii.AppSteroid.Models.Error> callback)    

#### Parameters
|Name|Type|Description|
|------|------|-----|
|page|uint|(Optional) page number to get|
|callback|Action \<IList \<Eventboard>,  Fresvii.AppSteroid.Models.ListMeta, Error>|This is a Delegate with an argument of eventboard model list, error info and meta info which will be called when the process to get eventboard model list is completed.|

#### Example

    FASLeaderboard.GetEventboardList(gameEvent.Id, (eventboards, listMeta, error) =>
    {
        if(error == null)
        {
            // To go through process
        }
    });


### <a name ="FASLeaderboard.GetEventboard">FASLeaderboard.GetEventboard</a>

Get eventboard

    public static void GetEventboard(string eventboardId, Action<Fresvii.AppSteroid.Models.Eventboard, Fresvii.AppSteroid.Models.Error> callback)
    
#### Parameters
|Name|Type|Description|
|------|------|-----|
|leaderboardId|string|ID of eventboard to get|
|callback|Action\<Eventboard, Error>|This is a Delegate with an argument of eventboard model and error info which will be called when the process to get eventboard is completed.|

#### Example

    FASLeaderboard.GetEventboard(eventboardId, (eventboard, error) =>
    {
        if(error == null)
        {
            //  To go through process
        }
    });


### <a name ="FASLeaderboard.GetRanking">FASLeaderboard.GetEventboardRanking</a>

Get Eventboard ranking (Score list)

    public static void GetEventboardRanking(string eventboardId, Action<IList<Fresvii.AppSteroid.Models.Score>, Fresvii.AppSteroid.Models.ListMeta, Fresvii.AppSteroid.Models.Error> callback)
    public static void GetEventboardRanking(string eventboardId, uint page, Action<IList<Fresvii.AppSteroid.Models.Score>, Fresvii.AppSteroid.Models.ListMeta, Fresvii.AppSteroid.Models.Error> callback)
    public static void GetEventboardRanking(string eventboardId, bool onlyFriends, Action<IList<Fresvii.AppSteroid.Models.Score>, Fresvii.AppSteroid.Models.ListMeta, Fresvii.AppSteroid.Models.Error> callback)
    public static void GetEventboardRanking(string eventboardId, bool onlyFriends, uint page, Action<IList<Fresvii.AppSteroid.Models.Score>, Fresvii.AppSteroid.Models.ListMeta, Fresvii.AppSteroid.Models.Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|eventboardId|string|ID of eventboard to get the ranking from|
|page|uint|(Optional) page number to get|
|onlyFriends|bool|(Optional) Only display friends' result (Default is false)|
|callback| Action\<IList\<Score>, Error> |This is a Delegate with an argument of Score model list and error info which will be called when the process to get score list is completed.|

#### Example

    FASLeaderboard.GetEventboardRanking(eventboardId, 1, true, (scores, error) =>
    {
        if(error == null)
        {
            // To go through process
        }
    });

### <a name ="FASLeaderboard.GetEventboardUserRank">FASLeaderboard.GetEventboardUserRank</a>

Get rank from a specific user on eventboard

    public static void GetEventboardUserRank(string eventboardId, string userId, Action<Fresvii.AppSteroid.Models.Rank, Fresvii.AppSteroid.Models.Error> callback)
    public static void GetEventboardUserRank(string eventboardId, string userId, bool onlyFriends, Action<Fresvii.AppSteroid.Models.Rank, Fresvii.AppSteroid.Models.Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|leaderboardId|string|ID of Event to get the rank from|
|userId|string|User ID to get the rank from|
|callback| Action\<Rank, Error>|This is a Delegate with an argument of Score model and error info which will be called when the process to get score is completed.|

#### Example

    FASLeaderboard.GetEventboardUserRank(leaderboardId, userId, (rank, error) =>
    {
        if(error == null)
        {
            //　To go through process
        }
    });
  