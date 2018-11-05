
# rtview-utils - Simplified HTTP client


## Table of contents

- [What does this utiltiy do?](#what-does-this-utiltiy-do?)
- [API](#api)
- [Examples](#examples)


Request also offers [convenience methods](#convenience-methods) like
`request.defaults` and `request.post`, and there are
lots of [usage examples](#examples) and several
[debugging techniques](#debugging).


---


## What does this utiltiy do?

You can stream any response to a file stream.


## API

```js
set_targeturl (targetURL) 
```

where targetURL is a string which is constituted of: 

the address of the computer, where the RTView DataServer is running plus the RTView DataServer’s http port
the default value for targetURL is 'http://localhost:3275'
in this case, for non-localhost IPs, the port 3275 must be accessible.

or

the address of the application server where the rtvpost servlet is running
the default value for targetURL is ’http://localhost/rtvpost’
in this case, for non-localhost IPs, the application server’s connection port must be accessible.


## Examples

```js
var qaInstance1URL = “http://12.243.27.123:3275”;
// function call
rtview_utils.set_targeturl (qaInstance1URL);

```


[back to top](#table-of-contents)
