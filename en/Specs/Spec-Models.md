# Models Specifications

last update at 2015/09/04

----------

## Introduction
Model Class for each Data

----------

## Classes

|Namespace|Class|Description|
|-----|-----|-----|
|Fresvii.AppSteroid.Models|[Comment](#Comment)|Comment model class |
|Fresvii.AppSteroid.Models|[CustomMessage](#CustomMessage)|CustomMessage model class |
|Fresvii.AppSteroid.Models|[DirectMessage](#DirectMessage)|DirectMessage model class |
|Fresvii.AppSteroid.Models|[Error](#Error)|Error model class|
|Fresvii.AppSteroid.Models|[GameContext](#GameContext)|GameContext model class|
|Fresvii.AppSteroid.Models|[Group](#GameContext)|Group model class |
|Fresvii.AppSteroid.Models|[GroupConference](#GroupConference)|GroupConference model class|
|Fresvii.AppSteroid.Models|[GroupConferenceParticipant](#GroupConferenceParticipant)|GroupConferenceParticipant model class |
|Fresvii.AppSteroid.Models|[GroupMessage](#GroupMessage)|GroupMessage model class |
|Fresvii.AppSteroid.Models|[Leaderboard](#Leaderboard)|Leaderboard model class |
|Fresvii.AppSteroid.Models|[Match](#Match)|Match model class |
|Fresvii.AppSteroid.Models|[MatchMakingInvitation](#MatchMakingInvitation)|MatchMakingInvitation model class |
|Fresvii.AppSteroid.Models|[MatchMakingRequest](#MatchMakingRequest)|MatchMakingRequest model class |
|Fresvii.AppSteroid.Models|[ListMeta](#ListMeta)|ListMeta model class |
|Fresvii.AppSteroid.Models|[Player](#Player)|Player model class |
|Fresvii.AppSteroid.Models|[Rank](#Rank)|Rank model class |
|Fresvii.AppSteroid.Models|[Score](#Score)|Score model class |
|Fresvii.AppSteroid.Models|[SnsAccount](#SnsAccount)|SnsAccount model class |
|Fresvii.AppSteroid.Models|[Thread](#Thread)|Thread model class |
|Fresvii.AppSteroid.Models|[User](#UserClass)|User model class |
|Fresvii.AppSteroid.Models|[GameEvent](#GameEventClass)| Game event model class|
|Fresvii.AppSteroid.Models|[Eventboard](#EventboardClass)| Eventboard model class|


----------
----------

## <a name ="Comment">Comment Class</a>

Comment data class

### Properties
|Type|Name|Description|
|---|---|---|
|string|Id|Comment ID|
|DateTime|CreatedAt|Creation date and time|
|DateTime|UpdateAt|Update date and time|
|uint|LikeCount|Number of likes|
|string|ThreadId|Thread ID|
|User|User|User|


--------------------------

## <a name ="CustomMessage">CustomMessage Class</a>

CustomMessage Class

### Properties
|Type|Name|Description|
|---|---|---|
|string|Id|ID|
|string|Action|Action name|
|IDictionary|Params|Parameter dictional|
|DateTime|CreatedAt|Data and time of when it was created.|

--------------------------

## <a name ="Error">Error Class</a>

If an error occurs in an FAS method, the error class of the Fresvii.AppSteroid.Models namespace will be returned in the relevant delegate.
The error codes are defined below, followed by the descriptions of the properties.

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
|int|Code|ErrorCode (int value of ErrorCode)|
|string|Detail|Error description|
|Method|ToString()|Error string|

--------------------------
## <a name ="GameContext">GameContext Class</a>

GameContext Class

### Properties
|Type|Name|Description|
|---|---|---|
|object|Value|object|
|User|UpdatedBy|User who updated|
|User|NextPlayer|Next Player|
|System.DateTime|UpdatedAt|Date and time of when it was updated.|
|uint|UpdatedCount|Number of time it was updated.|


--------------------------
## <a name ="Group">Group Class</a>

Group Class

### Properties
|Type|Name|Description|
|---|---|---|
|string |Id |ID|
|System.DateTime | CreatedAt |Date and time of when it was created.|
|System.DateTime | UpdatedAt |Date and time of when it was updated.|
|bool|Subscribed|Whether it is subscribed or unsubscribed.|
|string |Name |Group name|
|uint|MembersCount|Number of member in the group|
|IList<Member>|Members|Lis of member in the group|
|bool|Pair|Whether it is an pair group or not|
|GroupMessage|LatestMessage|Latest Group message|

--------------------------
## <a name ="GroupMessage">GroupMessage Class</a>

GroupMessage data Class

### Properties
|Type|Name|Description|
|---|---|---|
|int|Ranking|Ranking|
|DateTime|CreatedAt|Created date|
|DateTime|UpdateAt|Updated date|
|string|GroupId|Group ID|
|string|Text|Text|
|string|ImageUrl|Image URL|
|string|ImageThumbnailUrl|Image Thumbnail URL|
|User|User|User|

--------------------------
## <a name ="GroupConference">GroupConference Class</a>

Group Conference Class.

### Properties
|Type|Name|Description|
|---|---|---|
|string|GroupId|Group ID|
|string|UserId|User ID|
|System.DateTime|CreatedAt|Date and time of when it was created.|

--------------------------
## <a name ="GroupConferenceParticipant">GroupConferenceParticipant Class</a>

Group Conference Participant Class

### Properties
|Type|Name|Description|
|---|---|---|
|string|Id|ID|
|string|Name|User ID|
|string|GroupId|Group ID|
|System.DateTime|CreatedAt|Date and time of when it was created.|

-----------------

## <a name ="ListMeta">ListMeta Class</a>

Class for Meta information of list

### Properties
|Type|Name|Description|
|---|---|---|
|uint|TotalCount|Total count|
|uint|TotalPages|Total count of pages|
|uint|CurrentPage|Current page|
|uint|PerPage|Unite per page|
|uint?|NextPage|Next page (null when there isn't any page).|

-----------------

## <a name ="Thread">Thread Class</a>

Thread data class

### Properties
|Type|Name|Description|
|---|---|---|
|string|Id|Thread ID|
|DateTime|CreatedAt|Creation date and time|
|DateTime|UpdateAt|Update date and time|
|uint|CommentCount|Number of comments|
|uint|LikeCount|Number of likes|
|string|UserId|User ID|
|Comment|Comment|


--------------------------
## <a name ="Leaderboard">Leaderboard Class</a>

Class for leaderboard data

### Defines

 public enum SubmissionType {BestScore, RecentScore};

### Properties
|Type|Name|Description|
|---|---|---|
|string|Id|Leaderboard ID|
|DateTime|CreatedAt|Created date|
|DateTime|UpdateAt|Updated date|
|string|Name|Leaderboard Name|
|SubmissionType|Submission|To use highest score for the Ranking or to use the latest score for the Ranking(Set up on Web Console)|
|bool|Ascend|ascending order or not|

--------------------------
## <a name ="Match">Match Class</a>

Match Class

### Defines

   public enum Statuses { None = 0, Waiting, Inviting, Complete, Disposed }

### Properties
|Type|Name|Description|
|---|---|---|
|string|Id|Id|
|Statuses|Status|Match status|
|string|Segment|Segment|
|System.DateTime|CreatedAt|Date and time of when it was create.|
|System.DateTime|UpdatedAt|Date and time of when ti was update.|
|List\<Player>|Players|list of players|
|List\<Group>|Groups|list of groups|

--------------------------
## <a name ="MatchMakingInvitation">MatchMakingInvitation Class</a>

Matchmaking invitation Class.

### Defines

   public enum Statuses { None, Invited, Accepted, Matched, Declined, Expired };

### Properties
|Type|Name|Description|
|---|---|---|
|string|Id|Id|
|Statuses|Status|Matchmaking invitation status.|
|string|InvitationMessage|invitation message|
|User|User|User|


--------------------------
## <a name ="MatchMakingRequest">MatchMakingRequest Class</a>

Matchmaking request Class

### Defines

    public enum Statuses {None, Matching, Matched};

### Properties
|Type|Name|Description|
|---|---|---|
|string|Id|Id|
|Statuses|Status|Matchmaking request status|
|string|InvitationMessage|Invitation message|
|User|User|User|
|System.DateTime|CreatedAt|Date and time of when it was created.|
|System.DateTime|UpdatedAt|Date and time of when it was updated.|
|string|Segment|Segment|
|User|User|User|
|Match|Match|Match|
|List\<MatchMakingInvitation>|Invitations|List of invitation|

--------------------------
## <a name ="Rank">Rank Class</a>

Class for Rank data

### Properties
|Type|Name|Description|
|---|---|---|
|int|Ranking|Ranking|
|Score|Score|Score|

--------------------------
## <a name ="Score">Score Class</a>

Class for score data

### Properties
|Type|Name|Description|
|---|---|---|
|string|Id|ID|
|int|Value|Score Value|
|DateTime|CreatedAt|Created date|
|Leaderboard|Leaderboard|Leaderboard|
|User|User|User|

--------------------------

## <a name ="SnsAccount">SnsAccount Class</a>

SNS account class

### Properties
|Type|Name|Description|
|---|---|---|
|string|Id|ID|
|string|Provider|Provider string such as "Facebook" or "Twitter"|
|string|Uid|User ID|
|DateTime|CreatedAt|Creation date and time|
|DateTime|UpdatedAt|Update date and time|

--------------------------
## <a name ="Player">Player Class</a>

Matchmaking player Class


### Defines

   public enum Statuses { None, Matching, Matched };

### Properties
|Type|Name|Description|
|---|---|---|
|Statuses|Status|Player Status|
|User|User|User|



--------------------------
## <a name ="UserClass">User Class</a>

User data class

### Properties
|Type|Name|Description|
|---|---|---|
|string|Name|User name|
|string|FriendCode|Friend code|
|string|Id|User ID|
|DateTime|CreatedAt|Creation date and time|
|DateTime|UpdatedAt|Update date and time|


--------------------------
## <a name ="GameEventClass">GameEvent Class</a>

Game event data class

### Defines

#### enum Status
|Value|Description|
|-|-|
|Upcoming|Upcoming Event|
|Ongoing|Ongoing Event|
|Past|Past Event|

### Properties
|Type|Name|Description|
|---|---|---|
|string|Id|Game Event ID|
|string|Name|Event Name|
|DateTime|StartAt|Start date of the event|
|DateTime|EndAt|End date of the event|
|string|Description|Description text|
|DateTime|CreatedAt|Created date|
|string|ImageUrl|URL of event image|
|string|ImageLargeUrl|URL of event image (big)|
|string|WebSiteUrl|URL of event web site|
|Fresvii.AppSteroid.Models.App|App|App information of the event|

## <a name ="Eventboard">Eventboard Class</a>

Eventboard data class

### Properties
|Type|Name|Description|
|---|---|---|
|string|Id|Eventboard ID|
|Fresvii.AppSteroid.Models.Leaderboard|Leaderboard|Leaderboard|
|Fresvii.AppSteroid.Models.GameEvent|GameEvent|Game Event|
