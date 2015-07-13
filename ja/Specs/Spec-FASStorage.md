# FASStorage Specifications

last update at 2014/10/15

----------

## Introduction

## <a name ="FASStorage">FASStorage Class</a>
Key-Value Storage　を操作するためのクラスです。

----------

## Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASStorage](#FASStorage)|Key-Value Storage　を操作するためのクラス|

----------

### Methods

|Name|内容|
|------|-----|
|[FASStorage.GetAllKeyValueData](#FASStorage.GetAllKeyValueData)| Key Value Store の Key-Value データをすべて取得する |
|[FASStorage.GetAllKeys](#FASStorage.GetAllKeys)| Key Value Store のすべての Key を取得する  |
|[FASStorage.SetObjectForKey](#FASStorage.SetObjectForKey)| Key Value Store にデータを保存する |
|[FASStorage.GetObjectForKey](#FASStorage.GetObjectForKey)| Key Value Store のデータを取得する |
|[FASStorage.RemoveObjectForKey](#FASStorage.RemoveObjectForKey)| Key Value Store のデータを削除する |

### <a name ="FASStorage.GetAllKeyValueData">FASStorage.GetAllKeyValueData</a>

Key Value Store の Key-Value データをすべて取得します。

    public static void GetAllKeyValueData(Action<List<KeyValue>, Error> callback)
    public static void GetAllKeyValueData(string prefix, Action<List<KeyValue>, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|callback|Action\<List\<KeyValue>, Error>|KeyValueモデル一覧取得処理完了時に呼び出されるデリゲート|
|prefix|string|[オプション]プレフィックス|

### <a name ="FASStorage.GetAllKeys">FASStorage.GetAllKeys</a>

Key Value Store の Key をすべて取得します。

    public static void GetAllKeys(Action<List<string>, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|callback|Action\<List\<string>, Error>|Key一覧取得処理完了時に呼び出されるデリゲート|

### <a name ="FASStorage.SetObjectForKey">FASStorage.SetObjectForKey</a>

Key Value Store にオブジェクトを保存します。

    public static void SetObjectForKey(object value, string key, Action<List<KeyValue>, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|value|object|保存するオブジェクト|
|key|string|キー|
|callback|Action\<List\<KeyValue>, Error>|KeyValue保存完了時に呼び出されるデリゲート|

### <a name ="FASStorage.GetObjectForKey">FASStorage.GetObjectForKey</a>

Key Value Store のオブジェクトを取得します。

    public static void GetObjectForKey(string key, Action<object, Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|key|string|キー|
|callback|Action\<object, Error>|オブジェクト取得完了時に呼び出されるデリゲート|

### <a name ="FASStorage.RemoveObjectForKey">FASStorage.RemoveObjectForKey</a>

Key Value Store の対象データを削除します。

    public static void RemoveObjectForKey(string key, Action<Error> callback)

#### Parameters
|Name|Type|内容|
|------|------|-----|
|key|string|削除するオブジェクトのキー|
|callback|Action\<Error>|オブジェクト削除完了時に呼び出されるデリゲート|
