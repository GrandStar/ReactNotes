---
description: >-
  Node.js includes fs module to access physical file system. The fs module is
  responsible for all the asynchronous or synchronous file I/O operations.
---

# File System



### Reading File

Use fs.readFile\(\) method to read the physical file asynchronously.Signature:

```text
fs.readFile(fileName [,options], callback)

```

* filename: Full path and name of the file as a string.
* options: The options parameter can be an object or string which can include encoding and flag. The default encoding is utf8 and default flag is "r".
* callback: A function with two parameters err and fd. This will get called when readFile operation completes.
* options: "utf8"

Reading existing TestFile.txt asynchronously.Example: Reading File Copy

```text
var fs = require('fs');

fs.readFile('TestFile.txt', function (err, data) {
                    if (err) throw err;

    console.log(data);
});

$.getJSON('http://example.com/ajax', function (data) {
    console.log('IO...');
});
console.log('No wait for IO...');
```

Asychronize reading

```text
'use strict';

var fs = require('fs');

fs.readFile('sample.png', function (err, data) {
    if (err) {
        console.log(err);
    } else {
        console.log(data);
        console.log(data.length + ' bytes');
    }
});
```

If option is null, Buffer object return.  we can use 

```text
var text = data.toString('utf-8');
```

Sync read file:

```text
'use strict';

var fs = require('fs');

var data = fs.readFileSync('sample.txt', 'utf-8');
console.log(data);
```

readfile

```text
'use strict';

var fs = require('fs');

var data = 'Hello, Node.js';
fs.writeFile('output.txt', data, function (err) {
    if (err) {
        console.log(err);
    } else {
        console.log('ok.');
    }
});
```

stat

fs.stat\(\), 

```text
'use strict';

var fs = require('fs');

// 打开一个流:
var rs = fs.createReadStream('sample.txt', 'utf-8');

rs.on('data', function (chunk) {
    console.log('DATA:')
    console.log(chunk);
});

rs.on('end', function () {
    console.log('END');
});

rs.on('error', function (err) {
    console.log('ERROR: ' + err);
});
```









