# FASForum Specifications

last update at 2014/10/15

----------

## Introduction

## <a name ="FASForumClass">FASForum Class</a>
Class to operate Forum

----------

## Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASForum](#FASForumClass)|Class to operate forum |

----------

### Methods

|Name|Description|
|------|-----|
|[FASForum.GetForumThreads](#FASForum.GetForumThreads)| Get Thread list from a forum |
|[FASForum.CreateThread](#FASForum.CreateThread)| Create a new thread |
|[FASForum.DeleteThread](#FASForum.DeleteThread)| Delete a thread |
|[FASForum.GetThreadComments](#FASForum.GetThreadComments)| Get comment list from a thread |
|[FASForum.Subscribe](#FASForum.Subscribe)| Subscribe to a thread |
|[FASForum.Unsubscribe](#FASForum.Unsubscribe)| Unsubscribe from a thread |
|[FASForum.AddComment](#FASForum.AddComment)| Add new comment to a thread |
|[FASForum.EditComment](#FASForum.EditComment)| Edit a comment |
|[FASForum.DeleteComment](#FASForum.DeleteComment)| delete a comment |
|[FASForum.LikeComment](#FASForum.LikeComment)| Like a comment |
|[FASForum.UnlikeComment](#FASForum.UnlikeComment)| Unlike from a comment |

### <a name ="FASForum.GetForumThreads">FASForum.GetForumThreads</a>
Get the thread list.

    public static void GetForumThreads(Action<IList<Thread>, Error> callback)
    public static void GetForumThreads(uint page, Action<IList<Thread>, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|callback| Action\<IList\<Thread\>, Error\> |Delegate to be called after acquisition|
|page|uint|Page number to be acquired (optional)|

#### Example

    FASForum.GetForumThreads((threads, error)=>
    {
        if (error != null)
        {
            Debug.LogError(error.ToString());
        }
    });

-----------------
### <a name ="FASForum.CreateThread">FASForum.CreateThread</a>
Create a new thread.

    public static void CreateThread(string text, Action<Thread, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|text|string|Comment on the new thread to be created|
|callback| Action\<IList\<Thread\>, Error\> |Delegate to be called after process|

#### Example

    FASForum.CreateThread("thread created " + System.DateTime.Now.ToString(), (thread, error)=>
    {
        if (error != null)
        {
            Debug.LogError(error.ToString());
        }
    });

-----------------
### <a name ="FASForum.DeleteThread">FASForum.DeleteThread</a>
Delete a thread. Only the user who created the thread can delete it.

  public static void DeleteThread(string id, Action<Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|callback| Action\<IList\<Thread\>, Error\> |Delegate to be called after process|

#### Example

    FASForum.CreateThread("thread created " + System.DateTime.Now.ToString(), (thread, error)=>
    {
        if (error != null)
        {            
            Debug.LogError(error.ToString());
        }
    });

-----------------
### <a name ="FASForum.GetThreadComments">FASForum.GetThreadComments</a>
Get comment list on thread.

    public static void GetThreadComments(string threadId, Action<IList<Comment>, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|threadId|string|ID of the thread whose list is to be acquired|
|callback| Action\<IList\<Comment\>, Error\> |Delegate to be called after acquisition|

#### Example

    FASForum.GetThreadComments(selectedThread.Id, (comments, error)=>
    {
     if (error != null)
     {
         Debug.LogError(error.ToString());
     }
     });

-----------------
### <a name ="FASForum.Subscribe">FASForum.Subscribe</a>
Subscribe to a thread.

    public static void Subscribe(string threadId, Action<Thread, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|threadId|string|ID of the thread to which to subscribe|
|callback| Action\<Thread, Error\> |Delegate to be called after process|

#### Example

    FASForum.Subscribe(selectedThread.Id, (thread, error)=>
    {
        if (error != null)
        {
            Debug.LogError(error.ToString());
        }
    });

-----------------
### <a name ="FASForum.Unsubscribe">FASForum.Unsubscribe</a>
Unsubscribe from a thread.

    public static void Unsubscribe(string threadId, Action<Error> callback)


#### Parameters
|Name|Type|Description|
|------|------|-----|
|threadId|string|ID of the thread from which to unsubscribe|
|callback| Action\<Error\> |Delegate to be called after process|

#### Example

    FASForum.Unsubscribe(selectedThread.Id, (error)=>
    {
        if (error != null)
        {
            Debug.LogError(error.ToString());
        }
    });

-----------------
### <a name ="FASForum.AddComment">FASForum.AddComment</a>
Add a comment to a thread.

    public static void AddComment(string threadId, string text, Action<Comment, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|threadId|string|ID of the thread to which to add a comment|
|text|string|Comment text to be added|
|callback| Action\<Comment, Error\>  |Delegate to be called after process|

#### Example

    FASForum.AddComment(selectedThread.Id, "Add comment : " + System.DateTime.Now.ToString(), (comment, error)=>
    {
        if (error != null)
        {
            Debug.LogError(error.ToString());
        }
    });

-----------------
### <a name ="FASForum.EditComment">FASForum.EditComment</a>
Edit a comment.

  public static void EditComment(string commentId, string text, Action<Comment, Error> callback)


#### Parameters
|Name|Type|Description|
|------|------|-----|
|commentId|string|ID of the comment to be edited|
|text|string|Comment text to be edited|
|callback| Action\<Comment, Error\>  |Delegate to be called after process|

#### Example

    FASForum.EditComment(comment.Id, "Edit comment : " + System.DateTime.Now.ToString(), (comment, error) =>
    {
        if (error != null)
        {
            Debug.LogError(error.ToString());
        }
    });

-----------------
### <a name ="FASForum.DeleteComment">FASForum.DeleteComment</a>
Delete a comment.

    public static void DeleteComment(string commentId, Action<Error> callback)


#### Parameters
|Name|Type|Description|
|------|------|-----|
|commentId|string|ID of the comment to be deleted|
|callback| Action\<Error\>  |Delegate to be called after process|

#### Example

    FASForum.DeleteComment(comment.Id, (error)=>
    {
        if (error != null)
        {
            Debug.LogError(error.ToString());
        }
    });

-----------------
### <a name ="FASForum.LikeComment">FASForum.LikeComment</a>
Like a comment.

    public static void LikeComment(string commentId, Action<Comment, Error> callback)


#### Parameters
|Name|Type|Description|
|------|------|-----|
|commentId|string|ID of the comment to be liked|
|callback| Action\<Comment, Error\>  |Delegate to be called after process|

#### Example

    FASForum.LikeComment(comment.Id, (comment, error) =>
    {    
        if(error != null)
        {
            Debug.LogError(error.ToString());
        }    
    });

-----------------
### <a name ="FASForum.UnlikeComment">FASForum.UnlikeComment</a>
Remove like on a comment.

  public static void UnlikeComment(string commentId, Action<Error> callback)


#### Parameters
|Name|Type|Description|
|------|------|-----|
|commentId|string|ID of the comment to be unliked|
|callback| Action\<Error\>  |Delegate to be called after process|

#### Example

    FASForum.UnlikeComment(comment.Id, (error)=>
    {
        if(error != null)
        {
            Debug.LogError(error.ToString());
        }
    });
