
# rtview-utils - API for communicating with an RTView DataServer


## Table of contents

- [What does this utility do?](#what-does-this-utility-do?)
- [API](#api)
- [Examples](#examples)


---


## What does this utility do?


The `rtview-utils` npm package contains a set of utility functions for handling the Data, intended to be sent to and stored in an RTView DataServer.

An RTView DataServer is a Java process. As part of its many functionalities, it allows the users to create in-memory caches and store their information in those caches. That information, in turn, will be consumed by displays, dashboards, reports and alerts.

Users, in their own applications, will use the API in this package to:

- define RTView cache structure(s), which includes index and history columns with their types
- send data to RTView with proper metadata 
- do batching of data for performance optimization
- retry on lost connection


## API

```js
set_targeturl (targetURL) 
```

Where `targetURL` is a string which is constituted of: 

The address of the computer, where the RTView DataServer is running plus the RTView DataServer’s HTTP port,
Or
The address of the application server to which rtvpost servlet has been deployed.

The default value for `targetURL` is 'http://localhost:3275'.
In the case of the direct HTTP port access, this port must be accessible.
In the case access through the rtvpost servlet, the application server’s connection port must be accessible.\


```js
set_batchsize (batchSize) 
```

Where `batchSize` is an integer.
Its default value is 50.
This function allows the user application to send data to the RTView DataServer in bigger blocks and therefore, less frequently.\



```js
set_interval (timerInterval)  
```

Where `timerInterval` is an integer.
Its default value is 2000 and represents milliseconds.\


```js
create_datacache (cacheName, properties, metadata) 
```

Where `cacheName` is a string, `properties` is a set of Key:Value pairs of property names and their values, and `metadata` is an
array of Key:Value pairs of column names and their values. Multiple caches can be defined per RTView DataServer.\


```js
send_datatable (cacheName, data) 
```

Where `cacheName` is a string and `data` is a set of Key:Value pairs of columns names and their current values.


## Examples

### set_targeturl()\

```js
var qaInstance1URL = “http://12.243.27.123:3275”;
// function call
rtview_utils.set_targeturl (qaInstance1URL);
```

### set_batchsize()\

```js
var qaInstance1BatchSize = 25;
// function call
rtview_utils.set_batchsize (qaInstance1BatchSize);
```

### set_interval()\

```js
var qaInstance1TimerInterval = 10000;
// function call  
rtview_utils.set_interval (qaInstance1TimerInterval);
```

### create_datacache()\

```js
var sensorCacheName  = "SensorData";
var sensorProperties = {
"indexColumnNames" : "ID",
"historyColumnNames" : "temperature;humidity"
};
var sensorMetadata = [ 
{"ID" : "string" },
{"temperature" : "double"},
{"humidity" : "double"},
{"longitude" : "string"},
{"latitude" : "string"} 
];

// function call
rtview_utils.create_datacache(sensorCacheName, sensorProperties, sensorMetadata);
```

### send_datatable()\

```js
var sensorCacheName = "SensorData";
var sensorData = {
"ID" : "Sensor_01",
"temperature" : "24.57",
"humidity" : "44.11",
"longitude" : "37.9255° N",
"latitude" : "122.5275° W"
};

// function call
rtview_utils.send_datatable (sensorCacheName , sensorData);
```



[back to top](#table-of-contents)
