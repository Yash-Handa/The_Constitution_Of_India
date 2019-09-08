![GitHub](https://img.shields.io/github/license/Yash-Handa/The_Constitution_Of_India?style=for-the-badge)

# The Constitution Of India (COI)
The entire Constitution of India as a single JSON file

## COI.json Structure

The entire COI.json file is an array with 3 elements:

- **Element 1** *(0th index)*: This is an array of all the Articles of the Constitution. Each Article is an object with key value pairs described [below](#articles).
- **Element 2** *(1st index)*: This is an array of all the Parts of the Constitution. Each Part is an object with key value pairs described [below](#parts).
- **Element 3** *(2nd index)*: This is an array of all the Schedules of the Constitution. Each Schedule is an object with key value pairs described [below](#schedules).

### Articles

Each Article object has the following keys:

```js
{
  "ArtNo": String,
  "Name": String,
  "SubHeading": String,
  "Status": String,
  "Explanations": Array,
  "ArtDesc": String,
  "Clauses": Array
}
```

#### ArtNo: String

Each article has a unique `ArtNo` which is a combination of number and uppercase alphabets. It can be used as the ID of each Article. Eg: `5`, `31A`, etc. It is **always present**.

#### Name: String

Each article has a `Name` key which acts like a short description of the Article. Eg: `Parliament to regulate the right of citizenship by law.`, `Equality before law.`, etc. It is **always present**.

#### SubHeading: String

Some Articles have a special `SubHeading` key which represent the SubHeading under which the Article is present in the Constitution. Eg: `Right to Equality`, `Right against Exploitation`, etc. It is **NOT always present**.

#### Status: String

The COI.json file also have some articles which have been omitted from the constitution. Such articles have a special key: `Status` which have the value of `Omitted` i.e., `"Status": "Omitted"`

#### Explanations: Array

Some Articles in the Indian Constitution have explanations in them. In COI.json these explanations are present in the `Explanations` key which is an array of objects. Each object of the array represents an explanation of the article. It is **NOT always present**.

Each explanation object in the `Explanations` array has the following keys:

```js
{
  "ExplanationNo": String,
  "Explanation": String
}
```

#### ExplanationNo: String

Each explanation object in the `Explanations` array has the `ExplanationNo` key which is used to identify an explanation in an article. It consist of numbers.

#### Explanation: String

Each explanation object in the `Explanations` array has the `Explanation` key which contains the actual explanation of the article.

Example of the `Explanations` array:

```js
...
"Explanations": [
  {
    "ExplanationNo": "1",
    "Explanation": "..."
  },
  {
    "ExplanationNo": "2",
    "Explanation": "..."
  }
]
...
```

#### ArtDesc: String

Most of the articles have a `ArtDesc` key which contains the information / details of the Article.  
`Name` + `ArtDesc` + `Explanations` is the complete Article as present in the Constitution of India. It is **NOT always present**. If `ArtDesc` is not present the `Clauses` will be present.

#### Clauses: Array

Most of the articles have a `Clauses` key which is an array of objects. Each object of the array represents a clause of the article. `Name` + `Clauses` + `Explanations` is the complete Article as present in the Constitution of India. It is **NOT always present**. If `Clauses` is not present the `ArtDesc` will be present.

Each clause object in the `Clauses` array has the following keys:

```js
{
  "ClauseNo": String,
  "ClauseDesc": String,
  "SubClauses": Array,
  "Status": String,
  "FollowUp": String
}
```

### Parts

### Schedules

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

The above script will create a COI.json file in the directory from which the script is executed.
If the script is saved in a file called **download_COI.js** then the following command will execute it:

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

The above script will create a COI.json file in the directory from which the script is executed.
If the script is saved in a file called **download_COI.py** then the following command will execute it:

```shell
$ python3 download_COI.py
```
