# electron-markdown

electron-markdown is a Node.js module to convert Markdown to HTML. It uses [cmark-gfm](https://www.npmjs.com/package/cmark-gfm) for HTML generation, and a series of [unified](https://github.com/unifiedjs/unified) plugins to process the resulting HTML.

## Installation

Supports Node.js v8 or higher.

```bash
npm install electron-markdown
```

## Usage

electron-markdown exports a single function, which takes a Markdown string as its first argument and an options object as its second argument, and returns a Promise that resolves to the resulting HTML.

`resultPromise = electronMarkdown(markdown[, options])`

* `result: Promise<String>` - a Promise resolving to the resulting HTML if parsing and rendering succeeds
* `markdown: String` - a string of Markdown to render to HTML
* `options: Object` - options to pass to [cmark-gfm](https://github.com/BinaryMuse/node-cmark-gfm#options); will be deeply merged with the default options

Default options:

```javascript
{
  footnotes: true,
  extensions: {
    table: true,
    strikethrough: true,
    autolink: true,
    tagfilter: true
  }
}
```

To disable an option or extension that is enabled by default, provide your own options with a value of `false` (or an `extensions` object with the given extension's value set to `false`). Any options you provide will be merged into the default options, with `false` values overriding any default `true` value.

```javascript
const markdownToHtml = require('electron-markdown')

markdownToHtml(someMarkdown)
  .then(function (html) {
    console.log(html)
  }, function (err) {
    console.error(err)
  })
```
