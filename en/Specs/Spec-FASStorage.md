# FASStorage Specifications

last update at 2014/10/15

----------

## Introduction

## <a name ="FASStorageClass">FASStorage Class</a>
Class to operate Key-Value Storage.

----------

## Classes

|Namespace|Class|Description|
|-------|------|-----|
|Fresvii.AppSteroid|[FASStorage](#FASStorageClass)|Class to operate Key-Value Storage |

----------

### Methods

|Name|Description|
|------|-----|
|[FASStorage.GetAllKeyValueData](#FASStorage.GetAllKeyValueData)| Get every Key-Value data from Key Value Store |
|[FASStorage.GetAllKeys](#FASStorage.GetAllKeys)| Get all Key from Key Value Store |
|[FASStorage.SetObjectForKey](#FASStorage.SetObjectForKey)| Save object to Key Value Store |
|[FASStorage.GetObjectForKey](#FASStorage.GetObjectForKey)| Get object from Key Value Store |
|[FASStorage.RemoveObjectForKey](#FASStorage.RemoveObjectForKey)|Delete specific object from Key Value Store |

### <a name ="FASStorage.GetAllKeyValueData">FASStorage.GetAllKeyValueData</a>

Get every Key-Value data from Key Value Store

  public static void GetAllKeyValueData(Action<List<KeyValue>, Error> callback)
  public static void GetAllKeyValueData(string prefix, Action<List<KeyValue>, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|callback|Action\<List\<KeyValue>, Error>|A delegate to be called when the process to get list of KeyValue model is completed.|
|prefix|string|[Optional] Prefix|

### <a name ="FASStorage.GetAllKeys">FASStorage.GetAllKeys</a>

Get all Key from Key Value Store

  public static void GetAllKeys(Action<List<string>, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|callback|Action\<List\<string>, Error>|A delegate to be called when the process to get list of Key is completed.|

### <a name ="FASStorage.SetObjectForKey">FASStorage.SetObjectForKey</a>

Save object to Key Value Store

  public static void SetObjectForKey(object value, string key, Action<List<KeyValue>, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|value|object|Object to save|
|key|string|Key|
|callback|Action\<List\<KeyValue>, Error>|A delegate to be called when the process to store/save KeyValue is completed.|

### <a name ="FASStorage.GetObjectForKey">FASStorage.GetObjectForKey</a>

Get object to Key Value Store

  public static void GetObjectForKey(string key, Action<object, Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|key|string|Key|
|callback|Action\<object, Error>|A delegate to be called when the process to get object is completed.|

### <a name ="FASStorage.RemoveObjectForKey">FASStorage.RemoveObjectForKey</a>

Delete specific object from Key Value Store

  public static void RemoveObjectForKey(string key, Action<Error> callback)

#### Parameters
|Name|Type|Description|
|------|------|-----|
|key|string|Key of an object to delete|
|callback|Action\<Error>|A delegate to be called when the process to delete object is completed.|
