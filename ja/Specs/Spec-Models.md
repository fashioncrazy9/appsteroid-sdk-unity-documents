# Models Specifications

last update at 2014/10/15

----------

## Introduction
各種データ用モデルクラスです。

----------

## Classes

|Namespace|Class|Description|
|-----|-----|-----|
|Fresvii.AppSteroid.Models|[Comment](#Comment)|Comment モデル用クラス|
|Fresvii.AppSteroid.Models|[CustomMessage](#CustomMessage)|CustomMessage モデル用クラス|
|Fresvii.AppSteroid.Models|[DirectMessage](#DirectMessage)|DirectMessage モデル用クラス|
|Fresvii.AppSteroid.Models|[Error](#Error)|Error モデル用クラス|
|Fresvii.AppSteroid.Models|[GameContext](#GameContext)|GameContext モデル用クラス|
|Fresvii.AppSteroid.Models|[Group](#GameContext)|Group モデル用クラス|
|Fresvii.AppSteroid.Models|[GroupConference](#GroupConference)|GroupConference モデル用クラス|
|Fresvii.AppSteroid.Models|[GroupConferenceParticipant](#GroupConferenceParticipant)|GroupConferenceParticipant モデル用クラス|
|Fresvii.AppSteroid.Models|[GroupMessage](#GroupMessage)|GroupMessage モデル用クラス|
|Fresvii.AppSteroid.Models|[Leaderboard](#Leaderboard)|Leaderboard モデル用クラス|
|Fresvii.AppSteroid.Models|[Match](#Match)|Match モデル用クラス|
|Fresvii.AppSteroid.Models|[MatchMakingInvitation](#MatchMakingInvitation)|MatchMakingInvitation モデル用クラス|
|Fresvii.AppSteroid.Models|[MatchMakingRequest](#MatchMakingRequest)|MatchMakingRequest モデル用クラス|
|Fresvii.AppSteroid.Models|[NotificationRegistryInformation](#NotificationRegistryInformation)| プッシュ通知デバイストークン登録情報用クラス|
|Fresvii.AppSteroid.Models|[ListListMeta](#ListListMeta)|ListListMeta モデル用クラス|
|Fresvii.AppSteroid.Models|[Player](#Player)|Player モデル用クラス|
|Fresvii.AppSteroid.Models|[Rank](#Rank)|Rank モデル用クラス|
|Fresvii.AppSteroid.Models|[Score](#Score)|Score モデル用クラス|
|Fresvii.AppSteroid.Models|[SnsAccount](#SnsAccount)|SnsAccount モデル用クラス|
|Fresvii.AppSteroid.Models|[Thread](#Thread)|Thread モデル用クラス|
|Fresvii.AppSteroid.Models|[User](#UserClass)| ユーザーモデル用クラス|



----------
----------

## <a name ="Comment">Comment Class</a>

コメントデータ用クラス。

### Properties
|Type|Name|Description|
|---|---|---|
|string|Id|コメントID|
|DateTime|CreatedAt|作成日時|
|DateTime|UpdateAt|更新日時|
|uint|LikeCount|Likeの数|
|string|ThreadId|スレッドID|
|User|User|ユーザー|


-----------------

## <a name ="CustomMessage">CustomMessage Class</a>

カスタムメッセージ用クラス。

### Properties
|Type|Name|Description|
|---|---|---|
|string|Id|ID|
|string|Action|アクション名|
|IDictionary|Params|パラメータのディクショナリ|
|DateTime|CreatedAt|作成日時|

----------

## <a name ="Error">Error Class</a>

FAS の各メソッドでエラーが発生した場合、各デリゲートで Fresvii.AppSteroid.Models ネームスペースのエラークラスが返されます。
エラーコードの定義とプロパティは以下のとおりです。

### Fields

   public enum ErrorCode
        {
            Unknown = -1,
            NotInitialized,
            InvalidJson,
            UnableToRegisterNotification,
            NetworkNotReachable,
            InvalidTypeOfKeyValueStore,
            LoacalDatabaseError
        }

### Properties
|Type|Name|Description|
|---|---|---|
|int|Code|エラーコード（ ErrorCode の int 値) |
|string|Detail|エラー詳細|
|Method|ToString()|エラー文字列|

--------------------------
## <a name ="GameContext">GameContext Class</a>

ゲームコンテクスト用クラス。

### Properties
|Type|Name|Description|
|---|---|---|
|object|Value|object|
|User|UpdatedBy|更新したユーザー|
|User|NextPlayer|次のプレイヤー|
|System.DateTime|UpdatedAt|更新日時|
|uint|UpdatedCount|更新回数|


--------------------------
## <a name ="Group">Group Class</a>

グループ用クラス。

### Properties
|Type|Name|Description|
|---|---|---|
|string |Id |ID|
|System.DateTime | CreatedAt |作成日時|
|System.DateTime | UpdatedAt |更新日時|
|bool|Subscribed|購読の有無|
|string |Name |グループ名|
|uint|MembersCount|グループメンバー数|
|IList<Member>|Members|メンバー一覧|
|bool|Pair|ペアグループか否か|
|GroupMessage|LatestMessage|最新のグループメッセージ|

--------------------------
## <a name ="GroupMessage">GroupMessage Class</a>

グループメッセージデータ用クラス。

### Properties
|Type|Name|Description|
|---|---|---|
|int|Ranking|ランキング順位|
|DateTime|CreatedAt|作成日時|
|DateTime|UpdateAt|更新日時|
|string|GroupId|グループのID|
|string|Text|テキスト|
|string|ImageUrl|画像のURL|
|string|ImageThumbnailUrl|画像のサムネイルURL|
|User|User|ユーザー|

--------------------------
## <a name ="GroupConference">GroupConference Class</a>

グループカンファレンス用クラス。

### Properties
|Type|Name|Description|
|---|---|---|
|string|GroupId|グループID|
|string|UserId|ユーザーID|
|System.DateTime|CreatedAt|作成日時|

--------------------------
## <a name ="GroupConferenceParticipant">GroupConferenceParticipant Class</a>

グループカンファレンス参加者用クラス。

### Properties
|Type|Name|Description|
|---|---|---|
|string|Id|ID|
|string|Name|ユーザーID|
|string|GroupId|グループID|
|System.DateTime|CreatedAt|作成日時|

-----------------

## <a name ="ListMeta">ListMeta Class</a>

リストのMeta情報用クラス。

### Properties
|Type|Name|Description|
|---|---|---|
|uint|TotalCount|総数|
|uint|TotalPages|総ページ数|
|uint|CurrentPage|現在のページ|
|uint|PerPage|１ページあたりの数|
|uint?|NextPage|次のページ（ページがない場合は null ）|

-----------------

## <a name ="Thread">Thread Class</a>

スレッドデータ用クラス。

### Properties
|Type|Name|Description|
|---|---|---|
|string|Id|スレッドのID|
|DateTime|CreatedAt|作成日時|
|DateTime|UpdateAt|更新日時|
|uint|CommentCount|コメント数|
|uint|LikeCount|Likeの数|
|string|UserId|ユーザーID|
|Comment|コメント|


--------------------------
## <a name ="Leaderboard">Leaderboard Class</a>

リーダーボードデータ用クラス。

### Defines

  public enum SubmissionType {BestScore, RecentScore};

### Properties
|Type|Name|Description|
|---|---|---|
|string|Id|リーダーボードID|
|DateTime|CreatedAt|作成日時|
|DateTime|UpdateAt|更新日時|
|string|Name|リーダーボード名|
|SubmissionType|Submission|ランキングの作成に最高スコアか、最も最近に追加されたスコアを使用するか（Web Console で設定する）|
|bool|Ascend|昇順か否か|

--------------------------
## <a name ="Match">Match Class</a>

マッチ用クラス。

### Defines

   public enum Statuses { None = 0, Waiting, Inviting, Complete, Disposed }

### Properties
|Type|Name|Description|
|---|---|---|
|string|Id|Id|
|Statuses|Status|マッチのステイタス|
|string|Segment|セグメント区分|
|System.DateTime|CreatedAt|作成日時|
|System.DateTime|UpdatedAt|更新日時|
|List\<Player>|Players|プレイヤーリスト|
|List\<Group>|Groups|グループリスト|

--------------------------
## <a name ="MatchMakingInvitation">MatchMakingInvitation Class</a>

マッチメイキング招待用クラス。

### Defines

   public enum Statuses { None, Invited, Accepted, Matched, Declined, Expired };

### Properties
|Type|Name|Description|
|---|---|---|
|string|Id|Id|
|Statuses|Status|マッチメイキング招待のステイタス|
|string|InvitationMessage|招待メッセージ|
|User|User|ユーザー|


--------------------------
## <a name ="MatchMakingRequest">MatchMakingRequest Class</a>

マッチメイキングリクエスト用クラス。

### Defines

    public enum Statuses {None, Matching, Matched};

### Properties
|Type|Name|Description|
|---|---|---|
|string|Id|Id|
|Statuses|Status|マッチメイキングリクエストのステイタス|
|string|InvitationMessage|招待メッセージ|
|User|User|ユーザー|
|System.DateTime|CreatedAt|作成日時|
|System.DateTime|UpdatedAt|更新日時|
|string|Segment|セグメント区分|
|User|User|ユーザー|
|Match|Match|マッチ|
|List\<MatchMakingInvitation>|Invitations|招待リスト|

--------------------------
## <a name ="NotificationRegistryInformation">NotificationRegistryInformation Class</a>

プッシュ通知デバイストークン登録情報用クラス。

### Properties
|Type|Name|Description|
|---|---|---|
|System.DateTime|CreatedAt|作成日時|
|System.DateTime|UpdatedAt|更新日時|
|CertificateTypes|CertificateType|証明書の種類 (Development or Production) ※iOSの場合のみ|

## <a name ="Rank">Rank Class</a>

ランクデータ用クラス。

### Properties
|Type|Name|Description|
|---|---|---|
|int|Ranking|ランキング順位|
|Score|Score|スコア|

--------------------------
## <a name ="Score">Score Class</a>

スコアデータ用クラス。

### Properties
|Type|Name|Description|
|---|---|---|
|string|Id|ID|
|int|Value|スコア値|
|DateTime|CreatedAt|作成日時|
|Leaderboard|Leaderboard|リーダーボード|
|User|User|ユーザー|

-----------------

## <a name ="SnsAccount">SnsAccount Class</a>

SNSアカウント用クラス。

### Properties
|Type|Name|Description|
|---|---|---|
|string|Id|ID|
|string|Provider|プロバイダ 　例) "facebook", "twitter"|
|string|Uid|ユーザーID|
|string|CreatedAt|作成日時|
|string|UpdatedAt|更新日時|

--------------------------
## <a name ="Player">Player Class</a>

マッチメイキングプレイヤー用クラス。


### Defines

   public enum Statuses { None, Matching, Matched };

### Properties
|Type|Name|Description|
|---|---|---|
|Statuses|Status|プレイヤーのステイタス|
|User|User|ユーザー|



--------------------------
## <a name ="UserClass">User Class</a>

ユーザーデータ用クラス。

### Properties
|Type|Name|Description|
|---|---|---|
|string|Name|ユーザー名|
|string|FriendCode|フレンドコード|
|string|Id|ユーザーID|
|string|CreatedAt|作成日時|
|string|UpdatedAt|更新日時|
