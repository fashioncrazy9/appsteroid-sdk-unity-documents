# Use Leaderboard #

----------

## leaderboard description
This document describes the process of configuring and building the Leaderboard GUI into your app. Players can browse the score and ranking on the leaderboard, which can be created and managed with ease on the Fresvii web console.

## 【Setup】　Create leaderboard on the Fresvii web console

Click "Create Leaderboard" on the leaderboard page. Enter the name and select a suitable settings for your leaderboard.

![](Images/Leaderboards-ENG-1.png)

![](Images/Leaderboards-ENG-2.png)

Check your **Leaderboard ID** after the setup.

![](Images/Leaderboards-ENG-3.png)

## Submit Score on Leaderboard

Below is a sample code for users to submit scores to the leaderboard. **Users must be logged in before submitting any scores to the leaderboard**

#### Sample

  string leaderboardId = "50d8d7095ca940c6bce7dfdf1df80d44";

  int score = 1000;

  FASLeaderboard.ReportScore(leaderboardId, score, delegate(Score score, Error error)
  {
      if (error == null)
      {
          Debug.Log("Report score success : " + score.User.Name + " : " + score.Value);
      }
      else
      {
          Debug.LogError("Report score error : " + error.ToString());
      }
  });


## Show Leaderboard with AppSteroid GUI

This is a sample code to show AppSteroid GUI by selecting leaderboard ID.
Please refer to the document, "[GetStarted](GetStarted.md)", for GUI setup.

#### Sample Code

  string leaderboardId = "50d8d7095ca940c6bce7dfdf1df80d44";

  FASGui.SetLeaderboardId(leaderboardId);

  FASGui.ShowGUI(FASGui.Mode.Leaderboards);

## Display Leaderboard with AppSteroid GUI after submitting scores

This is a sample code to display leaderboard with AppSteroid GUI after a user submit a score.

You will need to display the leaderboard after the submission is completed. Displaying the leaderboard without receiving submission callback will result to show the leaderboard to the user without the latest score.

#### Sample Code

  string leaderboardId = "50d8d7095ca940c6bce7dfdf1df80d44";

  FASLeaderboard.ReportScore(leaderboardId, score, delegate(Score score, Error error)
  {
    if (error == null)
    {
      Debug.Log("Report score success : " + score.User.Name + " : " + score.Value);

      FASGui.SetLeaderboardId(leaderboardId);

      FASGui.ShowGUI(FASGui.Mode.Leaderboards);
    }
    else
    {
      Debug.LogError("Report score error : " + error.ToString());
    }
  });


## Other functions on leaderboard

You can also use these functions listed below on leaderboard. Check out [Spec-FASLeaderboard](Specs/Spec-FASLeaderboard.md) for more detailed information,

- Aggregation setting (Hourly)
  - Daily aggregation setting
  - Weekly aggregation setting
- Get leaderboard list in app
- Get Score
- Delete Score
- Get Rank (Score list)
- Get User Ranking (List of Rank)
