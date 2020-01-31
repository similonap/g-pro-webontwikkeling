# 02. Node Package Manager \(npm\)

Samen met Node.js werd npm \(Node Package Manager\) geïnstalleerd. Dit laat ontwikkelaars toe om externe packages te installeren die nieuwe functionaliteiten aan een project kunnen toevoegen zonder dat je hiervoor dus zelf code moet schrijven. Een grote bibliotheek van opensource packages staan op [NPMJS](https://www.npmjs.com/) en deze kunnen gebruikt worden om een eigen Node.js-applicatie te maken.

![](../.gitbook/assets/npm.png)

## voorbeeld

lorem ipsum???



## npm + Node.js

```javascript
const http = require('http');
const search = require('youtube-search');

const opts = {
  maxResults: 10,
  key: 'KEYGOESHERE',
};
let output = '';
search('Antwerpen stad', opts, (err, results) => {
  if (err) return console.log(err);
  results.forEach((element) => {
    output += ` <a href='${element.link}'>${element.title}</a> <br/> `;
    console.log(output);
  });
});
const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/html');
  res.end(output);
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```



## eigen modules

### search-string

```javascript
const search = ['antwerpen', 'brussel', 'leuven', 'mechelen', 'gent'];

exports.getSearchTerm = function () {
  const id = Math.floor(Math.random() * search.length);
  return search[id];
};
```





```javascript
const http = require('http');
const search = require('youtube-search');
const searchstrings = require('./searchstrings.js');

const searchTerm = searchstrings.getSearchTerm();
const opts = {
  maxResults: 10,
  key: 'KEYGOESHERE',
};

let output = '';
search(searchTerm, opts, (err, results) => {
  if (err) return console.log(err);
  results.forEach((element) => {
    output += ` <a href='${element.link}'>${element.title}</a> <br/> `;
    // console.log(element);
    //console.log(output);
  });
});
const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/html');
  res.end(output);
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```



## package.json

### npm init



