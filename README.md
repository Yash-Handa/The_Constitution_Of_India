# The_Constitution_Of_India
The entire Constitution of India as a single JSON file


## To download from Command Line

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

or can be automated by defining as a script in package.json:

For Linux(using **wget**):

```js
...
"scripts": {
    "download_COI": "wget https://raw.githubusercontent.com/Yash-Handa/The_Constitution_Of_India/master/COI.json -O COI.json",
    ...
  },
  ...
```

Execution:

```shell
npm run download_COI
```

For Windows use [**Invoke-WebRequest**]() and for Mac use [**curl**]() command.
