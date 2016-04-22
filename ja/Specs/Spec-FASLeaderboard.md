# FASLeaderboard Specifications

last update at 2016/04/22

----------

## Introduction

## <a name ="FASLeaderboard">FASLeaderboard Class</a>
リーダーボードに関連する操作をするクラスです。

----------

## Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASLeaderboard](#FASLeaderboard)|リーダーボードに関連する操作をするクラス|

----------

### Methods

#### Leaderborad
|Name|内容|
|------|-----|
|[FASLeaderboard.SetTotalizationClockUtcOffset](#FASLeaderboard.SetTotalizationClockUtcOffset)| リーダーボードの集計時間時刻のUTCオフセットを設定します。（デフォルト＝０） |
|[FASLeaderboard.SetDailyTotalizationStartTime](#FASLeaderboard.SetDailyTotalizationStartTime)| リーダーボードの Daily 集計開始時刻を設定します。（デフォルト＝00:00） |
|[FASLeaderboard.SetWeeklyTotalizationStartTime](#FASLeaderboard.SetWeeklyTotalizationStartTime)| リーダーボードの Weekly 集計開始時刻を設定します。（デフォルト＝ Sunday, 00:00） |
|[FASLeaderboard.GetLeaderboardList](#FASLeaderboard.GetLeaderboardList)| アプリのリーダーボードのリストを取得します。リーダーボードの作成はWebコンソールから行います。 |
|[FASLeaderboard.GetLeaderboard](#FASLeaderboard.GetLeaderboard)| リーダーボードを取得します。|
|[FASLeaderboard.ReportScore](#FASLeaderboard.ReportScore)| スコアを送信します。|
|[FASLeaderboard.GetScore](#FASLeaderboard.GetScore)| スコアを取得します。|
|[FASLeaderboard.DeleteScore](#FASLeaderboard.DeleteScore)| スコアを削除します。|
|[FASLeaderboard.GetNumberOfPlayers](#FASLeaderboard.GetNumberOfPlayers)| リーダーボードにスコアのあるのプレイヤー数を取得します。|
|[FASLeaderboard.GetUserScores](#FASLeaderboard.GetUserScores)| 指定したリーダーボードの指定したユーザーのスコア一覧を取得します。|
|[FASLeaderboard.GetRanking](#FASLeaderboard.GetRanking)|スコア一覧を取得します。|
|[FASLeaderboard.GetUserRank](#FASLeaderboard.GetUserRank)|ユーザーのランクを取得します。|

#### Eventboard
|Name|内容|
|------|-----|
|[FASLeaderboard.GetEventList](#FASLeaderboard.GetEventList)|イベントの一覧を取得します。|
|[FASLeaderboard.GetEvent](#FASLeaderboard.GetEvent)|指定したイベントの詳細を取得します。|
|[FASLeaderboard.GetEventboardList](#FASLeaderboard.GetEventboardList)|指定したイベントのイベントボード一覧を取得します。|
|[FASLeaderboard.GetAllEventboardList](#FASLeaderboard.GetAllEventboardList)|すべてのイベントのイベントボード一覧を取得します。|
|[FASLeaderboard.GetEventboard](#FASLeaderboard.GetEventboard)|指定したイベントボードの詳細を取得します。|
|[FASLeaderboard.GetEventboardRanking](#FASLeaderboard.GetEventboardRanking)|イベントボードのスコア一覧を取得します。|
|[FASLeaderboard.GetEventboardUserRank](#FASLeaderboard.GetEventboardRanking)|指定したイベントボードの指定したユーザーのランクを取得します。|

### <a name ="FASLeaderboard.SetTotalizationClockUtcOffset">FASLeaderboard.SetTotalizationClockUtcOffset</a>

リーダーボードの集計時間時刻のUTCオフセットを設定します。（デフォルト＝０）

    public static void FASLeaderboard.SetTotalizationClockUtcOffset(int utcOffset)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|utcOffset|int|オフセット時間|

### <a name ="FASLeaderboard.SetDailyTotalizationStartTime">FASLeaderboard.SetDailyTotalizationStartTime</a>

リーダーボードの Daily 集計開始時刻を設定します。（デフォルト＝00:00）

    public static void FASLeaderboard.SetDailyTotalizationStartTime(int hour, int minute)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|hour|int|時間 (デフォルト = 0)|
|minute|int|分 (デフォルト = 0)|

### <a name ="FASLeaderboard.SetWeeklyTotalizationStartTime">FASLeaderboard.SetWeeklyTotalizationStartTime</a>

リーダーボードの Weekly 集計開始時刻を設定します。（デフォルト＝ Sunday, 00:00）

    public static void FASLeaderboard.SetWeeklyTotalizationStartTime(System.DayOfWeek dayOfWeek, int hour, int minute)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|dayOfWeek|System.DayOfWeek|曜日（デフォルト = Sunday）|
|hour|int|時間 (デフォルト = 0)|
|minute|int|分 (デフォルト = 0)|

### <a name ="FASLeaderboard.GetLeaderboardList">FASLeaderboard.GetLeaderboardList</a>

リーダーボードの一覧を取得します。

    public static void GetLeaderboardList(uint page, Action < IList < Leaderboard > , Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|page|uint|（オプション）取得するページ番号|
|callback|Action < IList < Leaderboard >, Error>|リーダーボードのリスト取得処理完了時に、Leaderboard モデルのリスト、エラー情報を引数に呼び出されるデリゲート|

#### Example

    FASLeaderboard.GetLeaderboardList((leaderboards, error)=>
    {
        if(error == null)
        {
            //	リーダーボードのリストの処理を行う
        }
    });

### <a name ="FASLeaderboard.GetLeaderboard">FASLeaderboard.GetLeaderboard</a>

リーダーボードを取得します。

    public static void GetLeaderboard(string leaderboardId, Action < Leaderboard, Error > callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|leaderboardId|string|取得するリーダーボードのID|
|callback|Action < Leaderboard, Error > |リーダーボード取得処理完了時に、Leaderboard モデル、エラー情報を引数に呼び出されるデリゲート|

#### Example

    FASLeaderboard.GetLeaderboard(leaderboardId, (leaderboard, error)=>
    {
        if(error == null)
        {
            //	リーダーボードの処理を行う
        }
    });


### <a name ="FASLeaderboard.ReportScore">FASLeaderboard.ReportScore</a>

スコアを送信します。

    public static void ReportScore(string leaderboardId, int value, Action < Score, Error > callback)
    public static void ReportScore(string leaderboardId, int value, System.DateTime createdAt, Action < Score, Error > callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|leaderboardId|string|取得するリーダーボードのID|
|value|int|送信するスコア|
|createdAt|System.DateTime|（オプション）作成日時|
|callback|Action < Score, Error >|スコア送信処理完了時に、Score モデル、エラー情報を引数に呼び出されるデリゲート|

### <a name ="FASLeaderboard.GetScore">FASLeaderboard.GetScore</a>

スコアを取得します。

    public static void GetScore(string leaderboardId, string scoreId, Action < Score, Error > callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|leaderboardId|string|取得するリーダーボードのID|
|scoreId|string|取得するスコアのID|
|callback|Action < Score, Error >|スコア取得処理完了時に、Score モデル、エラー情報を引数に呼び出されるデリゲート|

#### Example

    FASLeaderboard.GetScore(leaderboardId, scoreId, (score, error)=>
    {
        if(error == null)
        {
            //	スコアの処理を行う
        }
    });


### <a name ="FASLeaderboard.DeleteScore">FASLeaderboard.DeleteScore</a>

スコアを削除します。

    public static void DeleteScore(string leaderboardId, string scoreId, Action<Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|leaderboardId|string|削除するリーダーボードのID|
|scoreId|string|削除するスコアのID|
|callback|Action < Error >|スコア削除処理完了時に、エラー情報を引数に呼び出されるデリゲート|

#### Example

    FASLeaderboard.DeleteScore(leaderboardId, scoreId, (error)=>
    {
        if(error != null)
        {
            //	エラー処理を行う
        }
    });

### <a name ="FASLeaderboard.GetNumberOfPlayers">FASLeaderboard.GetNumberOfPlayers</a>

  リーダーボードにスコアのあるのプレイヤー数を取得します。

        public static void GetNumberOfPlayers(string leaderboardId, FASLeaderboard.Period period, bool onlyFriends, Action<int> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|leaderboardId|string|リーダーボードのID|
|period|FASLeaderboard.Period|集計期間|
|onlyFriends|bool|フレンドのみの場合　true, 全プレイヤーの場合 false|
|callback|Action < int >|該当リーダーボードのプレイヤー数を返すコールバック。エラー発生時には -1 を返す。|

#### Example

    FASLeaderboard.GetNumberOfPlayers(leaderboardId, Period.Whole, false, (numberOfPlayers)=>
    {
        if(numberOfPlayers < 0)
        {
            Debug.LogError("Error");
        }
        else
        {
            Debug.Log("Number of players = " + numberOfPlayers);
        }
    });




### <a name ="FASLeaderboard.GetUserScores">FASLeaderboard.GetUserScores</a>

ユーザーのスコアの一覧を取得します。

    public static void GetUserScores(string leaderboardId, string userId, System.DateTime startTime, Leaderboard.SubmissionType sortBy, uint page, Action<IList<Score>, ListMeta, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|leaderboardId|string|ユーザースコアを取得するリーダーボードのID|
|userId|string|リストを取得するユーザーのID|
|span|FASLeaderboard.TotalizeSpan|（オプション）リストを取得する間隔 { Daily, Weekly, Total }|
|startTime|System.DateTime|（オプション）リストを取得する開始基準時刻|
|sortBy|Leaderboard.SubmissionType|（オプション）BestScore もしくは RecentScore のどちらかで設定する。デフォルトは BestScore。最も良いスコア順か最後にサブミットされた順によって並べる。最も良いスコアが最も高いものか低いものかは Leaderboard の設定に依存する。|
|page|uint|リストを取得するユーザーのID|
|userId|string|（オプション）取得するページ番号|
|callback| Action < IList < Score >, ListMeta, Error >|スコアリスト取得処理完了時に、Score モデルリスト、メタ情報、エラー情報を引数に呼び出されるデリゲート|

#### Example

    FASLeaderboard.GetUserScores(leaderboardId, userId, (scores, meta, error)=>
    {
        if(error == null)
        {
            // 処理を行う
        }
    });


### <a name ="FASLeaderboard.GetRanking">FASLeaderboard.GetRanking</a>

ランキング（スコアリスト）を取得します。

    public static void GetRanking(string leaderboardId, Action < IList < Fresvii.AppSteroid.Models.Score >, Fresvii.AppSteroid.Models.ListMeta, Fresvii.AppSteroid.Models.Error > callback)


#### Parameters
|Name|Type|内容|
|------|------|-----|
|leaderboardId|string|ランキングを取得するリーダーボードのID|
|span|FASLeaderboard.TotalizeSpan|（オプション）リストを取得する間隔 { Daily, Weekly, Total }|
|startTime|System.DateTime|（オプション）リストを取得する開始基準時刻|
|onlyFriends|bool|（オプション）友達のみの結果を表示する（デフォルトは false ）|
|callback| Action < IList < Fresvii.AppSteroid.Models.Score >, Fresvii.AppSteroid.Models.ListMeta, Fresvii.AppSteroid.Models.Error > |スコアリスト取得処理完了時に、Score モデルリスト、エラー情報を引数に呼び出されるデリゲート|

#### Example

    FASLeaderboard.GetRanking(leaderboardId, startTime, (ranking, meta, error)=>
    {
        if(error == null)
        {
            // 処理を行う
        }
    });

### <a name ="FASLeaderboard.GetUserRank">FASLeaderboard.GetUserRank</a>

ユーザーのランクを取得します。

    public static void GetUserRank(string leaderboardId, string userId, System.DateTime startTime, bool onlyFriends, Action<Rank, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|leaderboardId|string|ランキングを取得するリーダーボードのID|
|userId|string|リストを取得するユーザーのID|
|span|FASLeaderboard.TotalizeSpan|（オプション）リストを取得する間隔 { Daily, Weekly, Total }|
|startTime|System.DateTime|（オプション）リストを取得する開始基準時刻|
|onlyFriends|bool|（オプション）友達のみの結果を表示する（デフォルトは false ）|
|callback| Action < Rank, Error >|スコア取得処理完了時に、Score モデル、エラー情報を引数に呼び出されるデリゲート|

#### Example

    FASLeaderboard.GetUserRank(leaderboardId, userId, startTime, (rank, error) =>
    {
        if(error == null)
        {
            // 処理を行う
        }
    });

### <a name ="FASLeaderboard.GetEventList">FASLeaderboard.GetEventList</a>

イベントの一覧を取得します。

    public static void GetEventList(Fresvii.AppSteroid.Models.GameEvent.Status status, Action<IList<Fresvii.AppSteroid.Models.GameEvent>, Fresvii.AppSteroid.Models.ListMeta, Fresvii.AppSteroid.Models.Error> callback)
    public static void GetEventList(uint page, Fresvii.AppSteroid.Models.GameEvent.Status status, Action < IList < Fresvii.AppSteroid.Models.GameEvent >, Fresvii.AppSteroid.Models.ListMeta, Fresvii.AppSteroid.Models.Error > callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|page|uint|（オプション）取得するページ番号|
|status|Fresvii.AppSteroid.Models.GameEvent.Status|ゲームイベントの状態（Upcoming, Ongoing, Past）|
|callback|Action  < IList  < Leaderboard >,  Fresvii.AppSteroid.Models.ListMeta, Error >|ゲームイベントのリスト取得処理完了時に、GameEvent モデルのリスト、リストのメタ情報、エラー情報を引数に呼び出されるデリゲート|

#### Example

    FASLeaderboard.GetEventList((gameEvents, listMeta, error) =>
    {
        if(error == null)
        {
            // ゲームイベントリストの処理を行う
        }
    });

### <a name ="FASLeaderboard.GetEvent">FASLeaderboard.GetEvent</a>

ゲームイベントの詳細を取得します。

    public static void GetEvent(string eventId, Action < Fresvii.AppSteroid.Models.GameEvent, Fresvii.AppSteroid.Models.Error > callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|eventId|string|詳細を取得するGameEventのID|
|callback|Action < GameEvent, Error > |ゲームイベント詳細取得処理完了時に、GameEvent モデル、エラー情報を引数に呼び出されるデリゲート|

#### Example

    FASLeaderboard.GetEvent((gameEvent, error) =>
    {
        if(error == null)
        {
            // ゲームイベントの処理を行う
        }
    });


### <a name ="FASLeaderboard.GetEventboardList">FASLeaderboard.GetEventboardList</a>

イベントボード一覧を取得します。

    public static void GetEventboardList(string gameEventId, Action<IList<Fresvii.AppSteroid.Models.Eventboard>, Fresvii.AppSteroid.Models.ListMeta, Fresvii.AppSteroid.Models.Error> callback)
    public static void GetEventboardList(uint page, string gameEventId, Action<IList<Fresvii.AppSteroid.Models.Eventboard>, Fresvii.AppSteroid.Models.ListMeta, Fresvii.AppSteroid.Models.Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|page|uint|（オプション）取得するページ番号|
|gameEventId|string|ゲームイベントのID|
|callback|Action < IList < Eventboard >,  ListMeta, Error > |イベントボードリスト取得処理完了時に、Eventboard モデルのリスト、リストのメタ情報、エラー情報を引数に呼び出されるデリゲート|

#### Example

    FASLeaderboard.GetEventboardList(gameEvent.Id, (eventboards, meta, error) =>
    {
        if(error == null)
        {
            // イベントボードリストの処理を行う
        }
    });

### <a name ="FASLeaderboard.GetAllEventboardList">FASLeaderboard.GetAllEventboardList</a>

ゲームイベントの指定をせずに、すべてのイベントボード一覧を取得します。

    public static void GetAllEventboardList(Action < IList < Fresvii.AppSteroid.Models.Eventboard >, Fresvii.AppSteroid.Models.ListMeta, Fresvii.AppSteroid.Models.Error > callback)

    public static void GetAllEventboardList(uint page, Action < IList < Fresvii.AppSteroid.Models.Eventboard > , Fresvii.AppSteroid.Models.ListMeta, Fresvii.AppSteroid.Models.Error > callback)    

#### Parameters
|Name|Type|内容|
|------|------|-----|
|page|uint|（オプション）取得するページ番号|
|callback|Action  < IList < Eventboard >,  ListMeta, Error >|イベントボードリスト取得処理完了時に、Eventboard モデルのリスト、リストのメタ情報、エラー情報を引数に呼び出されるデリゲート|

#### Example

    FASLeaderboard.GetEventboardList(gameEvent.Id, (eventboards, meta, error) =>
    {
        if(error == null)
        {
            // イベントボードリストの処理を行う
        }
    });


### <a name ="FASLeaderboard.GetEventboard">FASLeaderboard.GetEventboard</a>

イベントボードを取得します。

    public static void GetEventboard(string eventboardId, Action<Fresvii.AppSteroid.Models.Eventboard, Fresvii.AppSteroid.Models.Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|leaderboardId|string|取得するイベントボードのID|
|callback|Action < Eventboard, Error > |イベントボード取得処理完了時に、Eventboard モデル、エラー情報を引数に呼び出されるデリゲート|

#### Example

    FASLeaderboard.GetEventboard(eventboardId, (eventboard, error) =>
    {
        if(error == null)
        {
            //  イベントボードの処理を行う
        }
    });


### <a name ="FASLeaderboard.GetEventboardRanking">FASLeaderboard.GetEventboardRanking</a>

イベントボードのランキング（スコアリスト）を取得します。

    public static void GetEventboardRanking(string eventboardId, Action < IList < Fresvii.AppSteroid.Models.Score >, Fresvii.AppSteroid.Models.ListMeta, Fresvii.AppSteroid.Models.Error > callback)
    public static void GetEventboardRanking(string eventboardId, uint page, Action < IList < Fresvii.AppSteroid.Models.Score >, Fresvii.AppSteroid.Models.ListMeta, Fresvii.AppSteroid.Models.Error > callback)
    public static void GetEventboardRanking(string eventboardId, bool onlyFriends, Action < IList < Fresvii.AppSteroid.Models.Score >, Fresvii.AppSteroid.Models.ListMeta, Fresvii.AppSteroid.Models.Error > callback)
    public static void GetEventboardRanking(string eventboardId, bool onlyFriends, uint page, Action < IList < Fresvii.AppSteroid.Models.Score >, Fresvii.AppSteroid.Models.ListMeta, Fresvii.AppSteroid.Models.Error > callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|eventboardId|string|ランキングを取得するイベントボードのID|
|page|uint|（オプション）取得するページ番号|
|onlyFriends|bool|（オプション）友達のみの結果を表示する（デフォルトは false ）|
|callback| Action < IList < Score >, Error > |スコアリスト取得処理完了時に、Score モデルリスト、エラー情報を引数に呼び出されるデリゲート|

#### Example

    FASLeaderboard.GetEventboardRanking(eventboardId, 1, true, (scores, error) =>
    {
        if(error == null)
        {
            // ランキングの処理を行う
        }
    });

### <a name ="FASLeaderboard.GetEventboardUserRank">FASLeaderboard.GetEventboardUserRank</a>

イベントボードでの指定ユーザーのランクを取得します。

    public static void GetEventboardUserRank(string eventboardId, string userId, Action < Fresvii.AppSteroid.Models.Rank, Fresvii.AppSteroid.Models.Error > callback)
    public static void GetEventboardUserRank(string eventboardId, string userId, bool onlyFriends, Action < Fresvii.AppSteroid.Models.Rank, Fresvii.AppSteroid.Models.Error > callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|leaderboardId|string|ランクを取得するイベントのID|
|userId|string|ランクを取得するユーザーのID|
|callback| Action < Rank, Error > |スコア取得処理完了時に、Score モデル、エラー情報を引数に呼び出されるデリゲート|

#### Example

    FASLeaderboard.GetEventboardUserRank(leaderboardId, userId, (rank, error) =>
    {
        if(error == null)
        {
            // 処理を行う
        }
    });
