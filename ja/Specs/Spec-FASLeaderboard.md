# FASLeaderboard Specifications

last update at 2014/10/15

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

|Name|内容|
|------|-----|
|[FASLeaderboard.SetTotalizationClockUtcOffset](#FASLeaderboard.SetTotalizationClockUtcOffset)| リーダーボードの集計時間時刻のUTCオフセットを設定します。（デフォルト＝０） |
|[FASLeaderboard.SetDailyTotalizationStartTime](#FASLeaderboard.SetDailyTotalizationStartTime)| リーダーボードの Daily 集計開始時刻を設定します。（デフォルト＝00:00） |
|[FASLeaderboard.SetWeeklyTotalizationStartTime](#FASLeaderboard.SetWeeklyTotalizationStartTime)| リーダーボードの Weekly 集計開始時刻を設定します。（デフォルト＝ Sunday, 00:00） |
|[FASLeaderboard.GetLeaderboards](#FASLeaderboard.GetLeaderboards)| アプリのリーダーボードのリストを取得します。リーダーボードの作成はWebコンソールから行います。 |
|[FASLeaderboard.GetLeaderboard](#FASLeaderboard.GetLeaderboard)| リーダーボードを取得します。|
|[FASLeaderboard.ReportScore](#FASLeaderboard.ReportScore)| スコアを送信します。|
|[FASLeaderboard.GetScore](#FASLeaderboard.GetScore)| スコアを取得します。|
|[FASLeaderboard.DeleteScore](#FASLeaderboard.DeleteScore)| スコアを削除します。|
|[FASLeaderboard.GetUserScores](#FASLeaderboard.GetUserScores)| スコアのリストを取得します。|
|[FASLeaderboard.GetRanking](#FASLeaderboard.GetRanking)|ランキング（スコアのリスト）を取得します。|
|[FASLeaderboard.GetUserRanking](#FASLeaderboard.GetUserRanking)|ユーザーのランキング（ランクのリスト）を取得します。|

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

### <a name ="FASLeaderboard.GetLeaderboards">FASLeaderboard.GetLeaderboards</a>

リーダーボードの一覧を取得します。

    public static void GetLeaderboards(Action<IList<Leaderboard>, Error> callback)
    public static void GetLeaderboards(uint page, Action<IList<Leaderboard>, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|page|uint|（オプション）取得するページ番号|
|callback|Action\<IList\<Leaderboard>, Error>|リーダーボードのリスト取得処理完了時に、Leaderboard モデルのリスト、エラー情報を引数に呼び出されるデリゲート|

#### Example

    FASLeaderboard.GetLeaderboards(delegate(IList<Leaderboard> leaderboards, Error error)
    {
        if(error == null)
        {
            //	リーダーボードのリストの処理を行う
        }
    });

### <a name ="FASLeaderboard.GetLeaderboard">FASLeaderboard.GetLeaderboard</a>

リーダーボードを取得します。

    public static void GetLeaderboard(string leaderboardId, Action<Leaderboard, Error> callback)
    public static void GetLeaderboard(string leaderboardId, uint page, Action<Leaderboard, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|leaderboardId|string|取得するリーダーボードのID|
|page|uint|（オプション）取得するページ番号|
|callback|Action\<Leaderboard, Error>|リーダーボード取得処理完了時に、Leaderboard モデル、エラー情報を引数に呼び出されるデリゲート|
#### Example

    FASLeaderboard.GetLeaderboard(　leaderboardId, delegate(Leaderboard leaderboard, Error error)
    {
        if(error == null)
        {
            //	リーダーボードの処理を行う
        }
    });


### <a name ="FASLeaderboard.ReportScore">FASLeaderboard.ReportScore</a>

スコアを送信します。

    public static void ReportScore(string leaderboardId, int value, Action<Score, Error> callback)
    public static void ReportScore(string leaderboardId, int value, System.DateTime createdAt, Action<Score, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|leaderboardId|string|取得するリーダーボードのID|
|value|int|送信するスコア|
|createdAt|System.DateTime|（オプション）作成日時|
|callback|Action\<Score, Error>|スコア送信処理完了時に、Score モデル、エラー情報を引数に呼び出されるデリゲート|

### <a name ="FASLeaderboard.GetScore">FASLeaderboard.GetScore</a>

スコアを取得します。

    public static void GetScore(string leaderboardId, string scoreId, Action<Score, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|leaderboardId|string|取得するリーダーボードのID|
|scoreId|string|取得するスコアのID|
|callback|Action\<Score, Error>|スコア取得処理完了時に、Score モデル、エラー情報を引数に呼び出されるデリゲート|

#### Example

    FASLeaderboard.GetScore(　leaderboardId, scoreId,　delegate(Score score, Error error)
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
|callback|Action\<Error>|スコア削除処理完了時に、エラー情報を引数に呼び出されるデリゲート|

#### Example

    FASLeaderboard.DeleteScore(　leaderboardId, scoreId,　(error)=>
    {
        if(error != null)
        {
            //	エラー処理を行う
        }
    });


### <a name ="FASLeaderboard.GetUserScores">FASLeaderboard.GetUserScores</a>

ユーザーのスコアの一覧を取得します。

    public static void GetUserScores(string leaderboardId, string userId, System.DateTime startTime, Leaderboard.SubmissionType sortBy, uint page, Action<IList<Score>, Error> callback)

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
|callback| Action\<IList\<Score>, Error>|スコアリスト取得処理完了時に、Score モデルリスト、エラー情報を引数に呼び出されるデリゲート|

#### Example

    FASLeaderboard.GetUserScores(　leaderboardId, userId,　(scores, error)=>
    {
        if(error == null)
        {
            //　処理を行う
        }
    });


### <a name ="FASLeaderboard.GetRanking">FASLeaderboard.GetRanking</a>

ランキング（スコアリスト）を取得します。

    public static void GetRanking(string leaderboardId, System.DateTime startTime, bool onlyFriends, Action<IList<Score>, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|leaderboardId|string|ランキングを取得するリーダーボードのID|
|span|FASLeaderboard.TotalizeSpan|（オプション）リストを取得する間隔 { Daily, Weekly, Total }|
|startTime|System.DateTime|（オプション）リストを取得する開始基準時刻|
|onlyFriends|bool|（オプション）友達のみの結果を表示する（デフォルトは false ）|
|callback| Action\<IList\<Score>, Error>|スコアリスト取得処理完了時に、Score モデルリスト、エラー情報を引数に呼び出されるデリゲート|

#### Example

    FASLeaderboard.GetRanking(leaderboardId, startTime, delegate(IList<Score> ranking, Error error)
    {
        if(error == null)
        {
            //　処理を行う
        }
    });

### <a name ="FASLeaderboard.GetUserRanking">FASLeaderboard.GetUserRanking</a>

ユーザーのランキングを取得します。

    public static void GetUserRanking(string leaderboardId, string userId, System.DateTime startTime, bool onlyFriends, Action<Rank, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|leaderboardId|string|ランキングを取得するリーダーボードのID|
|userId|string|リストを取得するユーザーのID|
|span|FASLeaderboard.TotalizeSpan|（オプション）リストを取得する間隔 { Daily, Weekly, Total }|
|startTime|System.DateTime|（オプション）リストを取得する開始基準時刻|
|onlyFriends|bool|（オプション）友達のみの結果を表示する（デフォルトは false ）|
|callback| Action\<Rank, Error>|スコア取得処理完了時に、Score モデル、エラー情報を引数に呼び出されるデリゲート|

#### Example

    FASLeaderboard.GetUserRanking(leaderboardId, userId, startTime, delegate(Rank rank, Error error)
    {
        if(error == null)
        {
            //　処理を行う
        }
    });
