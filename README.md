# npmdoc-node-emoji

#### api documentation for  [node-emoji (v1.5.1)](https://github.com/omnidan/node-emoji#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-node-emoji.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-node-emoji) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-node-emoji.svg)](https://travis-ci.org/npmdoc/node-npmdoc-node-emoji)

#### simple emoji support for node.js projects

[![NPM](https://nodei.co/npm/node-emoji.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/node-emoji)

- [https://npmdoc.github.io/node-npmdoc-node-emoji/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-node-emoji/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-node-emoji/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-node-emoji/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-node-emoji/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-node-emoji/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Daniel Bugl"
    },
    "bugs": {
        "url": "https://github.com/omnidan/node-emoji/issues"
    },
    "dependencies": {
        "string.prototype.codepointat": "^0.2.0"
    },
    "description": "simple emoji support for node.js projects",
    "devDependencies": {
        "istanbul": "^0.4.5",
        "mocha": "^3.0.2",
        "should": "^11.1.0"
    },
    "directories": {},
    "dist": {
        "shasum": "fd918e412769bf8c448051238233840b2aff16a1",
        "tarball": "https://registry.npmjs.org/node-emoji/-/node-emoji-1.5.1.tgz"
    },
    "gitHead": "b0a43f72e84ce612d9d6b72cd564b8c1bbde173b",
    "homepage": "https://github.com/omnidan/node-emoji#readme",
    "keywords": [
        "emoji",
        "simple",
        "emoticons",
        "emoticon",
        "emojis",
        "smiley",
        "smileys",
        "smilies",
        "ideogram",
        "ideograms"
    ],
    "license": "MIT",
    "main": "index.js",
    "maintainers": [
        {
            "name": "omnidan"
        }
    ],
    "name": "node-emoji",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git+https://github.com/omnidan/node-emoji.git"
    },
    "scripts": {
        "coverage": "istanbul cover _mocha test",
        "emojiparse": "node lib/emojiparse.js",
        "prepublish": "npm run test",
        "test": "mocha --require should --bail --reporter spec test/*"
    },
    "version": "1.5.1",
    "bin": {}
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
