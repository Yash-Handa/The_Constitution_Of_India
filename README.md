![GitHub](https://img.shields.io/github/license/Yash-Handa/The_Constitution_Of_India?style=for-the-badge)
![GitHub file size in bytes](https://img.shields.io/github/size/Yash-Handa/The_Constitution_Of_India/COI.json?style=for-the-badge)

# The Constitution Of India (COI)
The entire Constitution of India as a single JSON file

## COI.json Structure

## To Download from Command Line

### 1. For Linux / Mac use **wget** / **curl**

  #### wget:
  
  ```shell
  $ wget https://raw.githubusercontent.com/Yash-Handa/The_Constitution_Of_India/master/COI.json -O COI.json
  ```
  
  #### curl:
  
  ```shell
  $ curl https://raw.githubusercontent.com/Yash-Handa/The_Constitution_Of_India/master/COI.json -o COI.json
  ```
  
### 2. For Windows use **Invoke-WebRequest**

  ```shell
  Invoke-WebRequest https://raw.githubusercontent.com/Yash-Handa/The_Constitution_Of_India/master/COI.json -O COI.json
  ```
  
The above commands will create a COI.json file(with all it's content) in the directory from which the command is executed.

## Node.js sample script to Download COI.json

```js
const { exec } = require('child_process'),
  { platform } = require('process'),
  url = 'https://raw.githubusercontent.com/Yash-Handa/The_Constitution_Of_India/master/COI.json';

if (platform === 'win32') {
  exec(`Invoke-WebRequest ${url} -O COI.json`, (err, stdout, stderr) => {
    if (err) throw err
  });
} else if (platform === 'darwin') {
  exec(`curl ${url} -o COI.json`, (err, stdout, stderr) => {
    if (err) throw err;
  });
} else {
  exec(`wget ${url} -O COI.json`, (err, stdout, stderr) => {
    if (err) throw err;
  });
}
```

The above script will create a COI.json file in the directory from which the script is exicuted.
If the script is saved in a file called **download_COI.js** then the following commanf will execute it:

```shell
$ node download_COI.js
```

### or can be automated by defining as a script in package.json:

#### For Linux(using **wget**):

```js
...
"scripts": {
    "download_COI": "wget https://raw.githubusercontent.com/Yash-Handa/The_Constitution_Of_India/master/COI.json -O COI.json"
    ...
  },
  ...
```

Execution:

```shell
npm run download_COI
```

For Windows use [**Invoke-WebRequest**](#2-for-windows-use-invoke-webrequest) and for Mac use [**curl**](#curl) command.

## Python sample script to Download COI.json

```python
from subprocess import run, PIPE
from sys import platform
URL = 'https://raw.githubusercontent.com/Yash-Handa/The_Constitution_Of_India/master/COI.json'

test = None
if platform == 'linux' or platform == 'linux2':
    test = run(['wget', URL, '-O COI.json'], stdout=PIPE, stderr=PIPE)
elif platform == 'darwin':
    test = run(['curl', URL, '-o COI.json'], stdout=PIPE, stderr=PIPE)
elif platform == 'win32':
    test = run(['Invoke-WebRequest', URL, '-O COI.json'], stdout=PIPE, stderr=PIPE)
test.check_returncode()
```

The above script will create a COI.json file in the directory from which the script is exicuted.
If the script is saved in a file called **download_COI.py** then the following commanf will execute it:

```shell
$ python3 download_COI.py
```
