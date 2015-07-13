#　ログインして AppSteroid GUI を表示する

### 手順
- **Step 1.** [GettingStarted](GettingStarted.md) を参考にして、AppSteroidUIのシーンをビルドセッティングに追加する１~４の手順までを行ってください。
- **Step 2.** サインアップ済みユーザーでログインする
  - **Case 1.** サインアップ済みのユーザーがいない場合　→　新たにサインアップしてログインする
  - **Case 2.** サインアップ済みユーザーがいる場合　→　サインアップ済みのユーザーからユーザーを選択してログインする
- **Step 3.** GUI を表示する

### サンプルコード
```
using Fresvii.AppSteroid;
using Fresvii.AppSteroid.Models;
```

    //  Get signed up users list
    List<User> users = FASUser.LoadSignedUpUsers();

    //  If signed up user already exists
    if (users.Count > 0) // Step 2 - Case 2
    {
        User user = users[users.Count - 1]; //  In this case, we use latest signed up user account.

        FASUser.LogIn(user.Id, user.Token, delegate(Error error)
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
        FASUser.SignUp(delegate(User user, Error error)
        {
            if (error == null)
            {
                FASUser.LogIn(user.Id, user.Token, delegate(Error error2)
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
