# Use Fresvii GUI

### Steps

- **Step 1.** Refer to GetStarted and go through step 1 up to step 4 to add scene of AppSteroidGUI into build setting.
- **Step 2.** Login with an account that have already singed up.
  - **Case 1.** You do not have an account　→　Create a new account and login.
  - **Case 2.** You do have an account　→　Login with your account.
- **Step 3.** Show GUI

### Sample code

```
using Fresvii.AppSteroid;
using Fresvii.AppSteroid.Models;
```

    //  Get signed up users list
    List<User> users = FAS.LoadSignedUpUsers();

    //  If signed up user already exists
    if (users.Count > 0) // Step 2 - Case 2
    {
        User user = users[users.Count - 1]; //  In this case, we use latest signed up user account.

        FAS.LogIn(user.Id, user.Token, delegate(Error error)
        {
            if (error == null)
            {
                FASGui.ShowGUI(FASGui.Mode.Forum | FASGui.Mode.MyProfile); // Step 3
            }
            else
            {
                Debug.LogError(error.ToString());
            }
        });

        return;
    }
    //  If signed up user does not exist
    else // Step 2 - Case 1
    {
        FAS.SignUp(delegate(User user, Error error)
        {
            if (error == null)
            {
                FAS.LogIn(user.Id, user.Token, delegate(Error error2)
                {
                    if (error2 == null)
                    {
                            FASGui.ShowGUI(FASGui.Mode.Forum | FASGui.Mode.MyProfile); // Step 3
                    }
                    else
                    {
                            Debug.LogError(error2.ToString()); // Log in error
                    }
                });
            }
            else
            {
                Debug.LogError(error.ToString()); // Sign up error
            }
        });
    }
