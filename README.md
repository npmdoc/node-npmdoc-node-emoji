# api documentation for  [node-emoji (v1.5.1)](https://github.com/omnidan/node-emoji#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-node-emoji.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-node-emoji) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-node-emoji.svg)](https://travis-ci.org/npmdoc/node-npmdoc-node-emoji)
#### simple emoji support for node.js projects

[![NPM](https://nodei.co/npm/node-emoji.png?downloads=true)](https://www.npmjs.com/package/node-emoji)

[![apidoc](https://npmdoc.github.io/node-npmdoc-node-emoji/build/screenCapture.buildApidoc.browser.%252Fhome%252Ftravis%252Fbuild%252Fnpmdoc%252Fnode-npmdoc-node-emoji%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-node-emoji/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-node-emoji/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-node-emoji/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Daniel Bugl",
        "email": "daniel.bugl@touchlay.com"
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
            "name": "omnidan",
            "email": "daniel.bugl@touchlay.com"
        }
    ],
    "name": "node-emoji",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
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
    "version": "1.5.1"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module node-emoji](#apidoc.module.node-emoji)
1.  [function <span class="apidocSignatureSpan">node-emoji.</span>_get (emoji)](#apidoc.element.node-emoji._get)
1.  [function <span class="apidocSignatureSpan">node-emoji.</span>emojify (str, on_missing)](#apidoc.element.node-emoji.emojify)
1.  [function <span class="apidocSignatureSpan">node-emoji.</span>get (emoji)](#apidoc.element.node-emoji.get)
1.  [function <span class="apidocSignatureSpan">node-emoji.</span>random ()](#apidoc.element.node-emoji.random)
1.  [function <span class="apidocSignatureSpan">node-emoji.</span>search (str)](#apidoc.element.node-emoji.search)
1.  [function <span class="apidocSignatureSpan">node-emoji.</span>which (emoji_code)](#apidoc.element.node-emoji.which)
1.  object <span class="apidocSignatureSpan">node-emoji.</span>emoji



# <a name="apidoc.module.node-emoji"></a>[module node-emoji](#apidoc.module.node-emoji)

#### <a name="apidoc.element.node-emoji._get"></a>[function <span class="apidocSignatureSpan">node-emoji.</span>_get (emoji)](#apidoc.element.node-emoji._get)
- description and source-code
```javascript
function _get(emoji) {
  if (Emoji.emoji.hasOwnProperty(emoji)) {
    return Emoji.emoji[emoji];
  }
  return ':' + emoji + ':';
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.node-emoji.emojify"></a>[function <span class="apidocSignatureSpan">node-emoji.</span>emojify (str, on_missing)](#apidoc.element.node-emoji.emojify)
- description and source-code
```javascript
function emojify(str, on_missing) {
  if (!str) return '';

  return str.split(parser) // parse emoji via regex
            .map(function parseEmoji(s, i) {
              // every second element is an emoji, e.g. "test :fast_forward:" -> [ "test ", "fast_forward" ]
              if (i % 2 === 0) return s;
              var emoji = Emoji._get(s);
              if (emoji.indexOf(':') > -1 && typeof on_missing === 'function') {
                return on_missing(emoji.substr(1, emoji.length-2));
              }
              return emoji;
            })
            .join('') // convert back to string
  ;
}
```
- example usage
```shell
...

## Usage
'''javascript
var emoji = require('node-emoji')
emoji.get('coffee') // returns the emoji code for coffee (displays emoji on terminals that support it)
emoji.which(emoji.get('coffee')) // returns the string "coffee"
emoji.get(':fast_forward:') // '.get' also supports github flavored markdown emoji (http://www.emoji-cheat-sheet.com/)
emoji.emojify('I :heart: :coffee:!') // replaces all :emoji: with the actual emoji, in this case: returns "I ❤️ ☕️!"
emoji.random() // returns a random emoji + key, e.g. '{ emoji: '❤️', key: 'heart' }'
emoji.search('cof') // returns an array of objects with matching emoji's. '[{ emoji: '☕️', key: 'coffee' }, { emoji: ⚰', key: 'coffin
'}]'
'''

## Adding new emoji
Emoji come from js-emoji (Thanks a lot :thumbsup:). You can get a JSON file with all emoji here: https://raw.githubusercontent.com
/omnidan/node-emoji/master/lib/emoji.json
...
```

#### <a name="apidoc.element.node-emoji.get"></a>[function <span class="apidocSignatureSpan">node-emoji.</span>get (emoji)](#apidoc.element.node-emoji.get)
- description and source-code
```javascript
function get(emoji) {
  emoji = trim(emoji);

  return Emoji._get(emoji);
}
```
- example usage
```shell
...
Once you have that set-up, just run 'npm install --save node-emoji' in your project directory. :ship:

You're now ready to use emoji in your node projects! Awesome! :metal:

## Usage
'''javascript
var emoji = require('node-emoji')
emoji.get('coffee') // returns the emoji code for coffee (displays emoji on terminals that support it)
emoji.which(emoji.get('coffee')) // returns the string "coffee"
emoji.get(':fast_forward:') // '.get' also supports github flavored markdown emoji (http://www.emoji-cheat-sheet.com/)
emoji.emojify('I :heart: :coffee:!') // replaces all :emoji: with the actual emoji, in this case: returns "I ❤️ ☕️!"
emoji.random() // returns a random emoji + key, e.g. '{ emoji: '❤️', key: 'heart' }'
emoji.search('cof') // returns an array of objects with matching emoji's. '[{ emoji: '☕️', key: 'coffee' }, { emoji: ⚰', key: 'coffin
'}]'
'''
...
```

#### <a name="apidoc.element.node-emoji.random"></a>[function <span class="apidocSignatureSpan">node-emoji.</span>random ()](#apidoc.element.node-emoji.random)
- description and source-code
```javascript
function random() {
  var emojiKeys = Object.keys(Emoji.emoji);
  var randomIndex = Math.floor(Math.random() * emojiKeys.length);
  var key = emojiKeys[randomIndex];
  var emoji = Emoji._get(key);
  return {key: key, emoji: emoji};
}
```
- example usage
```shell
...
## Usage
'''javascript
var emoji = require('node-emoji')
emoji.get('coffee') // returns the emoji code for coffee (displays emoji on terminals that support it)
emoji.which(emoji.get('coffee')) // returns the string "coffee"
emoji.get(':fast_forward:') // '.get' also supports github flavored markdown emoji (http://www.emoji-cheat-sheet.com/)
emoji.emojify('I :heart: :coffee:!') // replaces all :emoji: with the actual emoji, in this case: returns "I ❤️ ☕️!"
emoji.random() // returns a random emoji + key, e.g. '{ emoji: '❤️', key: 'heart' }'
emoji.search('cof') // returns an array of objects with matching emoji's. '[{ emoji: '☕️', key: 'coffee' }, { emoji: ⚰', key: 'coffin
'}]'
'''

## Adding new emoji
Emoji come from js-emoji (Thanks a lot :thumbsup:). You can get a JSON file with all emoji here: https://raw.githubusercontent.com
/omnidan/node-emoji/master/lib/emoji.json

To update the list or add custom emoji, clone this repository and put them into 'lib/emojifile.js'.
...
```

#### <a name="apidoc.element.node-emoji.search"></a>[function <span class="apidocSignatureSpan">node-emoji.</span>search (str)](#apidoc.element.node-emoji.search)
- description and source-code
```javascript
function search(str) {
  var emojiKeys = Object.keys(Emoji.emoji);
  var matcher = trim(str)
  var matchingKeys = emojiKeys.filter(function(key) {
    return key.toString().indexOf(matcher) === 0;
  });
  return matchingKeys.map(function(key) {
    return {
      key: key,
      emoji: Emoji._get(key),
    };
  });
}
```
- example usage
```shell
...
'''javascript
var emoji = require('node-emoji')
emoji.get('coffee') // returns the emoji code for coffee (displays emoji on terminals that support it)
emoji.which(emoji.get('coffee')) // returns the string "coffee"
emoji.get(':fast_forward:') // '.get' also supports github flavored markdown emoji (http://www.emoji-cheat-sheet.com/)
emoji.emojify('I :heart: :coffee:!') // replaces all :emoji: with the actual emoji, in this case: returns "I ❤️ ☕️!"
emoji.random() // returns a random emoji + key, e.g. '{ emoji: '❤️', key: 'heart' }'
emoji.search('cof') // returns an array of objects with matching emoji's. '[{ emoji: '☕️', key: 'coffee' }, { emoji: ⚰', key: 'coffin
'}]'
'''

## Adding new emoji
Emoji come from js-emoji (Thanks a lot :thumbsup:). You can get a JSON file with all emoji here: https://raw.githubusercontent.com
/omnidan/node-emoji/master/lib/emoji.json

To update the list or add custom emoji, clone this repository and put them into 'lib/emojifile.js'.
Then run 'npm run-script emojiparse' in the project directory or 'node emojiparse' in the lib directory.
...
```

#### <a name="apidoc.element.node-emoji.which"></a>[function <span class="apidocSignatureSpan">node-emoji.</span>which (emoji_code)](#apidoc.element.node-emoji.which)
- description and source-code
```javascript
function which(emoji_code) {
  for (var prop in Emoji.emoji) {
    if (Emoji.emoji.hasOwnProperty(prop)) {
      if (Emoji.emoji[prop].codePointAt() === emoji_code.codePointAt()) {
        return prop;
      }
    }
  }
}
```
- example usage
```shell
...

You're now ready to use emoji in your node projects! Awesome! :metal:

## Usage
'''javascript
var emoji = require('node-emoji')
emoji.get('coffee') // returns the emoji code for coffee (displays emoji on terminals that support it)
emoji.which(emoji.get('coffee')) // returns the string "coffee"
emoji.get(':fast_forward:') // '.get' also supports github flavored markdown emoji (http://www.emoji-cheat-sheet.com/)
emoji.emojify('I :heart: :coffee:!') // replaces all :emoji: with the actual emoji, in this case: returns "I ❤️ ☕️!"
emoji.random() // returns a random emoji + key, e.g. '{ emoji: '❤️', key: 'heart' }'
emoji.search('cof') // returns an array of objects with matching emoji's. '[{ emoji: '☕️', key: 'coffee' }, { emoji: ⚰', key: 'coffin
'}]'
'''

## Adding new emoji
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
