# api documentation for  [node-dev (v3.1.3)](https://github.com/fgnass/node-dev#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-node-dev.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-node-dev) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-node-dev.svg)](https://travis-ci.org/npmdoc/node-npmdoc-node-dev)
#### Restarts your app when files are modified

[![NPM](https://nodei.co/npm/node-dev.png?downloads=true)](https://www.npmjs.com/package/node-dev)

[![apidoc](https://npmdoc.github.io/node-npmdoc-node-dev/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-node-dev_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-node-dev/build..beta..travis-ci.org/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-node-dev/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-node-dev/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Felix Gnass"
    },
    "bin": {
        "node-dev": "./bin/node-dev"
    },
    "bugs": {
        "url": "https://github.com/fgnass/node-dev/issues"
    },
    "contributors": [
        {
            "name": "Daniel Gasienica",
            "email": "daniel@gasienica.ch",
            "url": "https://github.com/gasi/"
        }
    ],
    "dependencies": {
        "dateformat": "~1.0.4-1.2.3",
        "dynamic-dedupe": "^0.2.0",
        "filewatcher": "~3.0.0",
        "minimist": "^1.1.3",
        "node-notifier": "^4.0.2",
        "resolve": "^1.0.0"
    },
    "description": "Restarts your app when files are modified",
    "devDependencies": {
        "coffee-script": "^1.8.0",
        "eslint": "^2.0.0",
        "eslint-config-airbnb-base": "^3.0.1",
        "eslint-plugin-import": "^1.8.1",
        "tap": "^5.2.0",
        "touch": "^1.0.0"
    },
    "directories": {},
    "dist": {
        "shasum": "582719223ebdef5d63059e6a7fbcd2399fc0f84d",
        "tarball": "https://registry.npmjs.org/node-dev/-/node-dev-3.1.3.tgz"
    },
    "engines": {
        "node": ">=0.8.0"
    },
    "gitHead": "55d67b0406947bf8c5e1f206d7469d55378a8655",
    "homepage": "https://github.com/fgnass/node-dev#readme",
    "keywords": [
        "restart",
        "reload",
        "supervisor",
        "monitor",
        "watch"
    ],
    "license": "MIT",
    "main": "./lib",
    "maintainers": [
        {
            "name": "fgnass",
            "email": "fgnass@gmail.com"
        },
        {
            "name": "gasi",
            "email": "daniel@gasienica.ch"
        },
        {
            "name": "tomekwi",
            "email": "t.wiszniewski@gmail.com"
        }
    ],
    "name": "node-dev",
    "optionalDependencies": {},
    "preferGlobal": true,
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+ssh://git@github.com/fgnass/node-dev.git"
    },
    "scripts": {
        "test": "tap test/*.js"
    },
    "version": "3.1.3"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module node-dev](#apidoc.module.node-dev)
1.  object <span class="apidocSignatureSpan">node-dev.</span>ipc

#### [module node-dev.ipc](#apidoc.module.node-dev.ipc)
1.  [function <span class="apidocSignatureSpan">node-dev.ipc.</span>on (proc, type, cb)](#apidoc.element.node-dev.ipc.on)
1.  [function <span class="apidocSignatureSpan">node-dev.ipc.</span>relay (src, dest)](#apidoc.element.node-dev.ipc.relay)
1.  [function <span class="apidocSignatureSpan">node-dev.ipc.</span>send (m, dest)](#apidoc.element.node-dev.ipc.send)



# <a name="apidoc.module.node-dev"></a>[module node-dev](#apidoc.module.node-dev)



# <a name="apidoc.module.node-dev.ipc"></a>[module node-dev.ipc](#apidoc.module.node-dev.ipc)

#### <a name="apidoc.element.node-dev.ipc.on"></a>[function <span class="apidocSignatureSpan">node-dev.ipc.</span>on (proc, type, cb)](#apidoc.element.node-dev.ipc.on)
- description and source-code
```javascript
on = function (proc, type, cb) {
  function handleMessage(m) {
    if (isNodeDevMessage(m) && type in m) cb(m);
  }
  proc.on('internalMessage', handleMessage);
  proc.on('message', handleMessage);
}
```
- example usage
```shell
...
if (dest.send) dest.send(m);
};

exports.on = function (proc, type, cb) {
function handleMessage(m) {
  if (isNodeDevMessage(m) && type in m) cb(m);
}
proc.on('internalMessage', handleMessage);
proc.on('message', handleMessage);
};

exports.relay = function (src, dest) {
if (!dest) dest = process;
function relayMessage(m) {
  if (isNodeDevMessage(m)) dest.send(m);
...
```

#### <a name="apidoc.element.node-dev.ipc.relay"></a>[function <span class="apidocSignatureSpan">node-dev.ipc.</span>relay (src, dest)](#apidoc.element.node-dev.ipc.relay)
- description and source-code
```javascript
relay = function (src, dest) {
  if (!dest) dest = process;
  function relayMessage(m) {
    if (isNodeDevMessage(m)) dest.send(m);
  }
  src.on('internalMessage', relayMessage);
  src.on('message', relayMessage);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.node-dev.ipc.send"></a>[function <span class="apidocSignatureSpan">node-dev.ipc.</span>send (m, dest)](#apidoc.element.node-dev.ipc.send)
- description and source-code
```javascript
send = function (m, dest) {
  m.cmd = 'NODE_DEV';
  if (!dest) dest = process;
  if (dest.send) dest.send(m);
}
```
- example usage
```shell
...

/**
 * Sends a message to the given process.
 */
exports.send = function (m, dest) {
m.cmd = 'NODE_DEV';
if (!dest) dest = process;
if (dest.send) dest.send(m);
};

exports.on = function (proc, type, cb) {
function handleMessage(m) {
  if (isNodeDevMessage(m) && type in m) cb(m);
}
proc.on('internalMessage', handleMessage);
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
