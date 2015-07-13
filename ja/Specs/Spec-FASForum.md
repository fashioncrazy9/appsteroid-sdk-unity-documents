# FASForum Specifications

last update at 2014/10/15

----------

## Introduction

## <a name ="FASForum">FASForum Class</a>
フォーラムの操作に関するクラスです。

----------

## Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASForum](#FASForum)|フォーラムの操作に関するクラス|

----------

### Methods

|Name|内容|
|------|-----|
|[FASForum.GetForumThreads](#FASForum.GetForumThreads)| フォーラムのスレッド一覧を取得する |
|[FASForum.CreateThread](#FASForum.CreateThread)| スレッドを新規に作成する|
|[FASForum.DeleteThread](#FASForum.DeleteThread)| スレッドを削除する|
|[FASForum.GetThreadComments](#FASForum.GetThreadComments)| スレッドのコメント一覧を取得する |
|[FASForum.Subscribe](#FASForum.Subscribe)| スレッドを購読する |
|[FASForum.Unsubscribe](#FASForum.Unsubscribe)| スレッドの購読を解除する |
|[FASForum.AddComment](#FASForum.AddComment)| スレッドにコメントを新規追加する |
|[FASForum.EditComment](#FASForum.EditComment)| コメントを編集する |
|[FASForum.DeleteComment](#FASForum.DeleteComment)| コメントを削除する |
|[FASForum.LikeComment](#FASForum.LikeComment)| コメントを Like する |
|[FASForum.UnlikeComment](#FASForum.UnlikeComment)| コメントのLikeを解除する |

### <a name ="FASForum.GetForumThreads">FASForum.GetForumThreads</a>
スレッド一覧を取得します。

    public static void GetForumThreads(Action<IList<Thread>, Error> callback)
    public static void GetForumThreads(uint page, Action<IList<Thread>, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|callback| Action\<IList\<Thread\>, Error\> |取得後に呼び出されるデリゲート|
|page|uint|（オプション）取得するページ番号|

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
新規にスレッドを作成します。

    public static void CreateThread(string text, Action<Thread, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|text|string|新規作成するスレッドのコメント|
|callback| Action\<IList\<Thread\>, Error\> |処理後に呼び出されるデリゲート|

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
スレッドを削除します。ただし、作成したユーザーのみ削除できます。

    public static void DeleteThread(string id, Action<Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|callback| Action\<IList\<Thread\>, Error\> |処理後に呼び出されるデリゲート|

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
スレッドのコメント一覧を取得します。

    public static void GetThreadComments(string threadId, Action<IList<Comment>, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|threadId|string|一覧を取得するスレッドのID|
|callback| Action\<IList\<Comment\>, Error\> |取得後に呼び出されるデリゲート|

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
スレッドを購読します。

    public static void Subscribe(string threadId, Action<Thread, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|threadId|string|購読するスレッドのID|
|callback| Action\<Thread, Error\> |処理後に呼び出されるデリゲート|

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
スレッド購読を解除します。

    public static void Unsubscribe(string threadId, Action<Error> callback)


#### Parameters
|Name|Type|内容|
|------|------|-----|
|threadId|string|購読解除するスレッドのID|
|callback| Action\<Error\> |処理後に呼び出されるデリゲート|

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
スレッドにコメントを追加します。

    public static void AddComment(string threadId, string text, Action<Comment, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|threadId|string|コメントを追加するスレッドのID|
|text|string|追加するコメントテキスト|
|callback| Action\<Comment, Error\>  |処理後に呼び出されるデリゲート|

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
コメントを編集します。

  public static void EditComment(string commentId, string text, Action<Comment, Error> callback)


#### Parameters
|Name|Type|内容|
|------|------|-----|
|commentId|string|編集するコメントのID|
|text|string|編集するコメントテキスト|
|callback| Action\<Comment, Error\>  |処理後に呼び出されるデリゲート|

#### Example

    FASForum.EditComment(comment.Id, "Edit comment : " + System.DateTime.Now.ToString(), (comment, error) =>
    {
        if (error != null)
        {
            Debug.LogError(error.ToString());
        }
    });

-----------------
### <a name ="FAS.DeleteComment">FASForum.DeleteComment</a>
コメントを削除します。

    public static void DeleteComment(string commentId, Action<Error> callback)


#### Parameters
|Name|Type|内容|
|------|------|-----|
|commentId|string|削除するコメントのID|
|callback| Action\<Error\>  |処理後に呼び出されるデリゲート|

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
コメントを Like します。

  public static void LikeComment(string commentId, Action<Comment, Error> callback)


#### Parameters
|Name|Type|内容|
|------|------|-----|
|commentId|string|Like するコメントのID|
|callback| Action\<Comment, Error\>  |処理後に呼び出されるデリゲート|

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
コメントの Like を解除します。

  public static void UnlikeComment(string commentId, Action<Error> callback)


#### Parameters
|Name|Type|内容|
|------|------|-----|
|commentId|string|Like を解除するコメントのID|
|callback| Action\<Error\>  |処理後に呼び出されるデリゲート|

#### Example

    FASForum.UnlikeComment(comment.Id, (error)=>
    {
        if(error != null)
        {
            Debug.LogError(error.ToString());
        }
    });
