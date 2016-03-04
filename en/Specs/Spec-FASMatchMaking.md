# FASMatchMaking Specifications

last update at 2015/07/07

----------

## Introduction

This is a specification for function related to matchmaking feature.
With this feature, players will be able to find other players to play within the game.
AppSteroid also provide a matchmaking GUI for implementation. please check the document, [Use MatchMaking](../Use MatchMaking.md), for detail.


---

## Sequence

#### At the Start of Matchmake (Regular Match)
![MatchMaking1](../Images/diagram_match_making_start.png)

- 1.1 An user create a new matchmake request.
- 1.2 Response the result of request creation. Match status: FASMatchStatusWating
- 2.1 A new matchmake request created by other users.
- 3.1 (If there is an existing match to join) Join a Match.
- 3.2 (If participants reach the maximum capacity of the match) Match is completed.
- 2.2 Response the result of request creation. Match status: FASMatchStatusComplete
- 4 Notify match completion event to all match participants.
- 5.1 Get the latest match invitation info.
- 5.2 Response the match detail.

#### At the Start of Matchmake (Friend Match by Invitation)
![MatchMaking2](../Images/diagram_match_making_invitation.png)

- 1.1 An user create a new matchmake request.
- 1.2 Response the result of request creation. Match status: FASMatchStatusInviting
- 2. Notify matchmake invitation event to joiner.
- 3.1 Accept invitation.
- 3.2 (If participants reach the maximum capacity of the match) Match is completed.
- 4 Notify match completion event to all match participants.
- 5.1 Get the latest match invitation info.
- 5.2 Response the match detail.

![MatchMaking3](../Images/diagram_match_making_end.png)

- 1.1 Dispose the needless match.
- 1.2 Response the result of match disposal. Match status: FASMatchStatusDisposed


## <a name ="FASMatchMakigClass">FASMatchMaking Class</a>
Class to operate Matchmaking functions.

----------

## Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASMatchMaking](#FASMatchMaking)|MatchMaking Operation Class|

----------

### Methods

|Name|内容|
|------|-----|
|[FASMatchMaking.CreateMatchMakingRequest](#FASMatchMaking.CreateMatchMakingRequest)| Create a matchmake request |
|[FASMatchMaking.CancelMatchMakingRequest](#FASMatchMaking.CancelMatchMakingRequest)| Cancel a matchmake request |
|[FASMatchMaking.GetMatchMakingRequest](#FASMatchMaking.GetMatchMakingRequest)| Get matchmake request |
|[FASMatchMaking.AcceptMatchMakingInvitation](#FASMatchMaking.AcceptMatchMakingInvitation)| Accept invitation for matchmake request |
|[FASMatchMaking.GetMatch](#FASMatchMaking.GetMatch)| Get match |
|[FASMatchMaking.GetMatchList](#FASMatchMaking.GetMatchList)| Get list of match |
|[FASMatchMaking.JoinMatch](#FASMatchMaking.JoinMatch)| Join a match |
|[FASMatchMaking.GetGameContext](#FASMatchMaking.GetGameContext)| Get game context |
|[FASMatchMaking.UpdateGameContext](#FASMatchMaking.UpdateGameContext)| Update (recreate) a game context |
|[FASMatchMaking.DisposeMatch](#FASMatchMaking.DisposeMatch)| Dispose a match |
|[FASMatchMaking.SetMatchMakingTimeOutSeconds](#FASMatchMaking.SetMatchMakingTimeOutSeconds)| Set time out for matchmaking in seconds (Default is 30 sec) |

### <a name ="FASMatchMaking.CreateMatchMakingRequest">FASMatchMaking.CreateMatchMakingRequest</a>

Create a matchmake request

Matchmaking will be accepted even after the time out seconds, only if participants reaches the minimum requested number. FASEvent.OnMatchMakingMatchCompleted will be triggered when the match was accepted. If the match is denied, the request is canceled.

    public static void CreateMatchMakingRequest(Action<MatchMakingRequest, Error> callback)
    public static void CreateMatchMakingRequest(uint? minNumberOfPlaysers, Action<MatchMakingRequest, Error> callback)
    public static void CreateMatchMakingRequest(string[] inviteUsers, Action<MatchMakingRequest, Error> callback)
    public static void CreateMatchMakingRequest(string invitationMessage, Action<MatchMakingRequest, Error> callback)
    public static void CreateMatchMakingRequest(string invitationMessage, string segment, Action<MatchMakingRequest, Error> callback)
    public static void CreateMatchMakingRequest(string[] inviteUsers, string invitationMessage, Action<MatchMakingRequest, Error> callback)
    public static void CreateMatchMakingRequest(string[] inviteUsers, string invitationMessage, string segment, Action<MatchMakingRequest, Error> callback)
    public static void CreateMatchMakingRequest(uint? minNumberOfPlaysers, string[] inviteUsers, string invitationMessage, string segment, Action<MatchMakingRequest, Error> callback)
    public static void CreateMatchMakingRequest(uint? minNumberOfPlaysers, uint? maxNumberOfPlaysers, string[] inviteUsers, string invitationMessage, string segment, Action<MatchMakingRequest, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|callback|Action<MatchMakingRequest, Error>|A delegate to be called when the process of sending a matchmaking request is completed. This delegate contains MatchMakingRequest and Error information as an argument.|
|minNumberOfPlaysers|uint?|(Optional)Minimum players [2 - 16]. Default : 2|
|maxNumberOfPlaysers|uint?|(Optional)Maximum players [2 - 16]. Default : same as min_number_of_players|
|inviteUsers|string[]|(Optional)list of user ID to invite.|
|invitationMessage|string|(Optional)invitation message|
|segment|string|(Optional)match segment.|



### <a name ="FASMatchMaking.CancelMatchMakingRequest">FASMatchMaking.CancelMatchMakingRequest</a>

Cancel a matchmake request

    public static void CancelMatchMakingRequest(string requestId, Action<Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|requestId|string|Matchmaking request ID to cancel|
|callback|Action<Error>|A delegate to be called when the process to cancel matchmaking request is completed. This delegate contains Error information as an argument.|

### <a name ="FASMatchMaking.GetMatchMakingRequest">FASMatchMaking.GetMatchMakingRequest</a>

Get Matchmake request

    public static void GetMatchMakingRequest(Action<MatchMakingRequest, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|callback|Action<MatchMakingRequest, Error>|A delegate to be called when the process to get a matchmaking request is completed. This delegate contains MatchMakingRequest and Error information as an argument.|


### <a name ="FASMatchMaking.AcceptMatchMakingInvitation">FASMatchMaking.AcceptMatchMakingInvitation</a>

Accept invitation for matchmake request

    public static void AcceptMatchMakingInvitation(string requestId, Action<MatchMakingRequest, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|requestId|string|Match request ID to accept.|
|callback|Action<MatchMakingRequest, Error>|A delegate to be called when the process, accepting a match request invitation is completed. This delegate contains MatchMakingRequest and Error information as an argument.|

### <a name ="FASMatchMaking.GetMatch">FASMatchMaking.GetMatch</a>

Get a match with a specified ID.

    public static void GetMatch(string matchId, Action<Match, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|matchId|string|Match ID|
|callback|Action<Match, Error> |A delegate to be called when the process to get a match is completed. This delegate contains Match and Error information as an argument.|


### <a name ="FASMatchMaking.GetMatchList">FASMatchMaking.GetMatchList</a>

Get list of matches

    public static void GetMatchList(Action<IList<Match>, Error> callback)
    public static void GetMatchList(uint page, Action<IList<Match>, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|page|uint|(Optional) Page |
|callback|Action<Match, Error> |A delegate to be called when the process to get list of match is completed. This delegate contains IList<Match> and Error information as an argument.|


### <a name ="FASMatchMaking.JoinMatch">FASMatchMaking.JoinMatch</a>

Join a Match

    public static void JoinMatch(string matchId, Action<MatchMakingRequest, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|matchId|string|ID of a match to join|
|callback|Action<MatchMakingRequest, Error> |A delegate to be called when the process, joining a match is completed. This delegate contains MatchMakingRequest and Error information as an argument.|


### <a name ="FASMatchMaking.GetGameContext">FASMatchMaking.GetGameContext</a>

Get game context.

    public static void GetGameContext(string matchId, Action<GameContext, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|matchId|string|Match ID|
|callback|Action<GameContext, Error> |A delegate to be called when the process to get game context is completed. This delegate contains GameContext and Error information as an argument.|



### <a name ="FASMatchMaking.UpdateGameContext">FASMatchMaking.UpdateGameContext</a>

Update (recreate) a game context.

    public static void UpdateGameContext(string matchId, string json, uint updatedCount, Action<GameContext, Error> callback)
    public static void UpdateGameContext(string matchId, string json, string nextPlayerId, Action<GameContext, Error> callback)
    public static void UpdateGameContext(string matchId, string json, Action<GameContext, Error> callback)
    public static void UpdateGameContext(string matchId, string json, string nextPlayerId, uint? updatedCount, Action<GameContext, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|matchId|string|Match ID|
|json|string|JSON format of game context. Root contents are object.|
|nextPlayerId|string|(Optional) Next user ID.|
|updatedCount|uint?|(Optional) update count.|
|callback|Action<GameContext, Error>|A delegate to be called when the process, updating game context is completed. This delegate contains GameContext and Error information as an argument.|
