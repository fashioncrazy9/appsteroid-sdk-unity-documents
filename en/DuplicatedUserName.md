
# Behavior on User Name Duplication

You can change the behavior of when an user name is duplicated.   
1. Automatically add a serial number at the end of the duplicated name. 
2. Return an error when an user enter an existing name.  

![duplication_settings](./Images/console_name_duplication.png "On Name Duplication")

Following is the API  
- [FASUser.SignUp](./Specs/Spec-FASUser.md#FASUser.SignUp)
- [FASUser.PatchAccount](./Specs/Spec-FASUser.md#FASUser.PatchAccount)  

### Behavior on 1
API would not return an error, but automatically add a serial number at the end of the name.  
For example, if an user name `Chicken` already exist on the data base, the next user who entered `Chicken` will be registered as `Chicken_1`.

### Behavior on 2
On name duplication, an Error object with the following error code will be returned by API.

#### Errors
|Fresvii.AppSteroid.Models.Error.ErrorCode|Description|
|------|------|-----|
|NameHasAlreadyBeenTaken|Error code of when user name is duplicated on sign up|

Developers can notify the user about name duplication by handling this error. 
Sample Code:

```C#
FASUser.SignUp(”username”, "description",  profileImage,  (user, error)=>
    {
        if (error != null)
        {
            if (error.Code == Fresvii.AppSteroid.Models.Error.ErrorCode.NameHasAlreadyBeenTaken)
            {
                // name duplication error process
            }
            else{
                // Error process such as network error
            }

        }
        else
        {       
            // Signup success
            Debug.Log(user.name + ", " + user.friend_code + ", " + user.id + ", " + user.created_at + ", " + user.updated_at);
        }
    });
```