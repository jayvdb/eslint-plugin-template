# eslint-plugin-template

Parses out template declarations found in js and html files.

For example if you have a file like below, eslint will not be able to parse it
normally due to the template markers. With this plugin, the linter is able to
work normally. Note that whatever is inside the markers is replaced with `{}`.

```js
  {# Set data in the JS variable data #}    // ignored
  {% import json %}                         // ignored
  var x = {{ json.dumps(data) }}            // becomes var x = {}
  var y = {% raw json.dumps(data) %}        // becomes var y = {}
```

It handles conditional templates within JavaScript similarly.

```js
{% if true %}
  var x = 1
{% else %}
  var x = 2
{% endif %}
```

becomes:

```js
  var x = 1
  var x = 2
```

## Installation

```
npm install --save-dev eslint eslint-plugin-template
```

## Usage

Add `template` to the plugins section of your `.eslintrc` configuration file:

```json
{
    "plugins": [
        "template"
    ]
}
```

## Tests

```
$ npm test
```

## Release

- Update the version in `package.json`
- Commit to the master branch and push
- Run `npm publish`
