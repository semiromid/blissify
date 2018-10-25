blissify
========

browserify v2 plugin for bliss


## Use

### Install in local project

install blissify locally to your project

```
npm install blissify
```

### Make a bliss template

Create templates using [bliss](https://github.com/cstivers78/bliss/wiki); by default blissify transforms `.html` files

```
@!(obj)
<h1>Hello @obj.name!</h1>
```

Require and use those templates in your view (backbone), controller (spine), etc.

```
var template = require('template.html');

$('body').html(template({name: 'Nali'}));
```

### Transform with browserify

On the command line, transform module with browserify `-t` option:

```
browserify -t blissify main.js > bundle.js
```

Or, in a bundler script (e.g. `bundler.js`), use blissify as a transform:

```
var browserify = require('browserify');
var blissify = require('blissify');

var b = browserify();
b.add('view.js');
b.transform(blissify);

b.bundle().pipe(process.stdout);
```

Then, run the script to bundle it up:

```
node bundler
```

**Pro tip:** you can configure a custom extension for blissify

```
bundler.transform(blissify.configure('.bliss'));
```

### Debug

To set the transformer in debug mode, set `verbose=true` when instatiating blissify

```
var blissify = require('blissify');
blissify.verbose = true;
```

When enabled, debug mode will `console.log` when a raw template is successfully recompiled and `console.error` when a parse error occurs. This is super helpful if you're using [watchify](https://github.com/substack/watchify). an error will look like:

```
[blissify] error: <badTemplate.html>
<errorStackTrace>
```

Note that when in debug mode, the error is not passed to the `through` stream.


## Upgrading from `0.1.x` to `1.0.0`?

- If using a custom file extension, make sure to use the new configuration pattern
- If using a bundler script, make sure to change `b.transform(blissify())` to `b.transform(blissify)`


## Test

drink up me 'earties, yo ho!
