
# rtview-utils - An API for communicating with an RTView DataServer


## Table of contents

- [What does this utiltiy do?](#what-does-this-utiltiy-do?)
- [API](#api)
- [Examples](#examples)


The rtview-utils npm package contains a set of utility functions for handling the Data which is intended to be sent to and stored in an RTView DataServer.

An RTView DataServer is a Java process that allows the user to create in-memory caches and store information in those caches, in order to feed that information into displays, dashboards, reports and alerts.

A user application will utilize the functions in the rtview-utils package to store its data into those caches. 

The rtview-utils package provides the following features:

- define RTView cache structure(s), which includes index and history columns with their types
- send data to RTView with proper metadata 
- batching of data for performance optimization
- retry on lost connection



---


## What does this utiltiy do?

You can stream any response to a file stream.


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
In the case access through the rtvpost servlet, the application server’s connection port must be accessible.


```js
set_batchsize (batchSize) 
```

Where `batchSize` is an integer.
Its default value is 50.
This function allows the user application to send data to the RTView DataServer in bigger blocks and therefore, less frequently.



```js
set_interval (timerInterval)  
```

Where `timerInterval` is an integer.
Its default value is 2000 and urepresents milliseconds.


```js
create_datacache (cacheName, properties, metadata) 
```

Where `cacheName` is a string, `properties` is a set of Key:Value pairs of property names and their values, and `metadata` is an
array of Key:Value pairs of column names and their values. Multiple caches can be defined per RTView DataServer. 


```js
send_datatable (cacheName, data) 
```

Where `cacheName` is a string and `data` is a set of Key:Value pairs of columns names and their current values.




## Examples

```js
var qaInstance1URL = “http://12.243.27.123:3275”;
// function call
rtview_utils.`set_targeturl` (qaInstance1URL);

```


[back to top](#table-of-contents)
