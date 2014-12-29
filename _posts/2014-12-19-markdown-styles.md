---
Katie: post
title: Markdown Styles
categories: [Web Development]
tags: [markdown, css]
share: true
comments: true
---
## Features

- Ready-made CSS stylesheets for Markdown, just copy the assets folder you want
- Bundled with `generate-md`, a small tool that converts a folder of Markdown documents into a output folder of HTML documents, preserving the directory structure
- Use your own custom markup and CSS via `--layout`.
- Support for relative paths to the assets folder via `{{assetsRelative}}` and document table of content generation via `{{toc}}`.
- Support for generic metadata via a meta.json file

-----
## Quickstart

Install `generate-md` via npm:

    sudo npm install -g markdown-styles

Create a markdown file and then convert it to html:

    mkdir input/
    echo "# Hello world\n YOLO" > input/index.md
    generate-md --layout mixu-gray --input ./input --output ./output
    google-chrome ./output/index.html

Try out different layouts by changing the `--layout` parameter; screenshots at the bottom of this page.

![montage](https://github.com/mixu/markdown-styles/raw/master/screenshots/montage.png)

If you want to make use of the bundled layouts stylesheets as a basis for your own site, copy the ./assets folder and point `--layout` to your own layout.

For example:

    git clone https://github.com/mixu/markdown-styles.git ./markdown-styles
    cp -Rv ./markdown-styles/layouts/mixu-gray ./my-layout
    nano ./my-layout/page.html

Now edit the files `./my-layout/page.html` and run:

    generate-md --layout ./my-layout/page.html --input ./input --output ./output

## What's new in v1.2.x

`v1.2.0`: Code syntax highlighting has been reworked so that syntax highlighters have become pluggable. See the relevant section below on how to use the new system.

`v1.2.1`: added the `bootstrap3` style, thanks @MrJuliuss!

`v1.2.2`: added the `github` style, based on [sindresorhus/github-markdown-css](https://github.com/sindresorhus/github-markdown-css).

## Just using the stylesheets

Alternatively, if you just want the stylesheets for your own project, you can just copy the `./assets` folder from the layout you want.

To preview the styles in the browser, clone this repo locally and then open `./output/index.html` or run `make preview` which opens that page in your default browser.

## Using generate-md

This project also includes a small tool for generating HTML files from Markdown files.

The console tool is `generate-md`, e.g.

    generate-md --layout jasonm23-foghorn --output ./test/

[Here is an example](https://github.com/zendesk/radar/blob/gh-pages/Makefile) of how I generated the project docs for [Radar](https://github.com/zendesk/radar) using generate-md, a Makefile and a few custom assets.

`--input` specifies the input directory (default: `./input/`).

`--output` specifies the output directory (default: `./output/`).

`--layout` specifies the layout to use. This can be either one of built in layouts, or a path to a custom template file with a set of custom assets.

`--partials` specifies the [partials](#partials) directory. 

`--helpers` specifies the [helpers](#helpers) directory. 

To override the layout, simply create a directory, such as `./my-theme/`, with the following structure:

````bash
├── my-theme
│   ├── assets
│   │   ├── css
│   │   ├── img
│   │   └── js
│   └── page.html

````

Then, running a command like:

      generate-md --input ./input/ --layout ./my-theme/page.html --output ./test/

will:

1. convert all Markdown files in `./input` to HTML files under `./test`, preserving paths in `./input`.
2. use the template `./my-theme/page.html`, replacing values such as `{{> content}}`, `{{{toc}}}` and `{{assetsRelative}}` (see the layouts for examples on this)
3. (recursively) copy over the assets from `./my-theme/assets` to `./test/assets`.

This means that you could, for example, point a HTTP server at the root of `./test/` and be done with it.

You can also use the current directory as the output (e.g. for Github pages).

## Syntax highlighting support (changed in v1.2.x)

`generate-md` supports syntax highlighting during the Markdown-to-HTML conversion process.

Supported:

- highlight.js via [mds-hljs](https://github.com/mixu/mds-hljs)
- csv (using highlight.js css classes) via [mds-csv](https://github.com/mixu/mds-csv)

To enable the syntax highlighting support, install the module (e.g. `mds-hljs`) and then use `--highlight` (e.g. `--highlight mds-hljs`) to activate the highlighter.

For example, to use `highlight.js` to highlight all code blocks:

    npm install -g markdown-styles mds-hljs
    generate-md --highlight mds-hljs ...

You will also need to include [one of the highlight.js CSS style sheets](http://softwaremaniacs.org/media/soft/highlight/test.html) in your assets folder/layout file CSS (e.g. by using a custom `--layout` file).


### Template Evaluation

The [handlebars.js](https://github.com/wycats/handlebars.js) template language is used to evaluate both the template and the markdown. Together with the `meta.json`, partials and helpers both template and markdown can be enhanced.

#### `meta.json`
You can add a file named `meta.json` to the folder from which you run `generate-md`.

The metadata in that directory will be read and replacements will be made for corresponding `{{names}}` in the template.

The metadata is scoped by the top-level directory in `./input`.

For example:

````json
{
  "foo": {
    "repoUrl": "https://github.com/mixu/markdown-styles"
  }
}
````

would make the metadata value `{{repoUrl}}` available in the template, for all files that are in the directory `./input/foo`.

Using [handlebars.js](https://github.com/wycats/handlebars.js) we can go event farther. For example, you may add a tags array to the meta.json:

```json
{
  "foo": {
    "tags": ["handlebars", "template"]
  }
}
```

While in the html you may:

```html
<ul>
{{#each tags}}
    <li>{{ this }}</li>
{{/each}}
</ul>
```

Which will result in 

```html
<ul>
    <li>handlebars</li>
    <li>template</li>
</ul>
```

#### Partials

Partials are html files that can be included via handlebars `{{> partialName}}` style. Usually they are .html files. For example, if `footer.html` resides in the partials directory, `{{> footer}}` will be replaced with `footer.html`'s content. For more advanced topics, see [handlebars partials documentation](https://github.com/wycats/handlebars.js#partials). Don't use `content.html`, it is reserved to the html generated from the markdown.

#### Helpers

Helpers are functions that you can use throughout the template. See [handlebars helpers ](https://github.com/wycats/handlebars.js#registering-helpers).
For example, add `linkTo.js` to the specified helpers directory:

```js
var Handlebars = require('handlebars');
module.exports = function(){
  return new Handlebars.SafeString("<a href='" + Handlebars.Utils.escapeExpression(this.url) + "'>" + Handlebars.Utils.escapeExpression(this.body) + "</a>");
};
```

In your `meta.json`
```json
{
  "foo": {
    "links": [
      {"url": "/hello", "body": "Hello"},
      {"url": "/world", "body": "World!"}
    ]
  }
}
```
Somewhere in your template:
```html
<ul>{{#links}}<li>{{linkTo}}</li>{{/links}}</ul>
```

The result:
```html
<ul>
  <li>
    <a href='/hello'>Hello</a>
  </li>
  <li>
    <a href='/world'>World!</a>
  </li>
</ul>
```

### Language-specific syntax highlighting and custom highlighters

You can use `--highlight-<language> <module>` to override the syntax highlighter for a specific language. `<module>` can also be a path to a file.

For example, you might use the `mds-csv` highlighter for csv code blocks. Input code block with language:

    ```csv
    "EmployeeID","EmployeeName","PhoneNumber","ZipCode"
    "1048","Jimmy Adams",5559876543,12345
    ```

Command:

    generate-md --highlight-csv mds-csv ...

You can write your own syntax highlighter wrappers. Have a look at [mds-hljs](https://github.com/mixu/mds-hljs) and [mds-csv](https://github.com/mixu/mds-csv) for examples. These come in two flavors:

Asynchronous (three parameters):

    module.exports = function(code, lang, onDone) {
        return onDone(null, result);
    };

Synchronous (two parameters):

    module.exports = function(code, lang) {
        return require('highlight.js').highlightAuto(code).value;
    };

## --command

`--command <cmd>`: Pipe each Markdown file through a shell command and capture the output before converting. Useful for filtering the file, for example.

## --asset-dir

`--asset-dir <path>`: Normally, the asset directory is assumed to be `./assets/` in the same folder the `--layout` file is. You can override it to a different asset directory explicitly with `--asset-dir`, which is useful for builds where several directories use the same layout but different asset directories.

## Acknowledgments

I'd like to thank the authors the following CSS stylesheets:

- jasonm23-dark, jasonm23-foghorn, jasonm23-markdown and jasonm23-swiss are based on https://github.com/jasonm23/markdown-css-themes by [jasonm23](https://github.com/jasonm23)
- thomasf-solarizedcssdark and thomasf-solarizedcsslight are based on https://github.com/thomasf/solarized-css by [thomasf](https://github.com/thomasf)
- markedapp-byword is based on the user-contributed stylesheet at http://bywordapp.com/extras/
- roryg-ghostwriter is based on https://github.com/roryg/ghostwriter
- github is based on [sindresorhus/github-markdown-css](https://github.com/sindresorhus/github-markdown-css) (sorry, sindresorhus-github is too long to type as a layout name!)

## Screenshots of the layouts

Note: these screenshots are generate via cutycapt, so they look worse than they do in a real browser.

### roryg-ghostwriter

![roryg-ghostwriter](https://github.com/mixu/markdown-styles/raw/master/screenshots/roryg-ghostwriter.png)

### mixu-bootstrap

![mixu-bootstrap](https://github.com/mixu/markdown-styles/raw/master/screenshots/mixu-bootstrap.png)

### mixu-bootstrap-2col

![mixu-bootstrap-2col](https://github.com/mixu/markdown-styles/raw/master/screenshots/mixu-bootstrap-2col.png)

### mixu-gray

![mixu-gray](https://github.com/mixu/markdown-styles/raw/master/screenshots/mixu-gray.png)

### jasonm23-dark

![jasonm23-dark](https://github.com/mixu/markdown-styles/raw/master/screenshots/jasonm23-dark.png)

### jasonm23-foghorn

![jasonm23-foghorn](https://github.com/mixu/markdown-styles/raw/master/screenshots/jasonm23-foghorn.png)

### jasonm23-markdown

![jasonm23-markdown](https://github.com/mixu/markdown-styles/raw/master/screenshots/jasonm23-markdown.png)

### jasonm23-swiss

![jasonm23-swiss](https://github.com/mixu/markdown-styles/raw/master/screenshots/jasonm23-swiss.png)

### markedapp-byword

![markedapp-byword](https://github.com/mixu/markdown-styles/raw/master/screenshots/markedapp-byword.png)

### mixu-book

![mixu-book](https://github.com/mixu/markdown-styles/raw/master/screenshots/mixu-book.png)

### mixu-page

![mixu-page](https://github.com/mixu/markdown-styles/raw/master/screenshots/mixu-page.png)

### mixu-radar

![mixu-radar](https://github.com/mixu/markdown-styles/raw/master/screenshots/mixu-radar.png)

### thomasf-solarizedcssdark

![thomasf-solarizedcssdark](https://github.com/mixu/markdown-styles/raw/master/screenshots/thomasf-solarizedcssdark.png)

### thomasf-solarizedcsslight

![thomasf-solarizedcsslight](https://github.com/mixu/markdown-styles/raw/master/screenshots/thomasf-solarizedcsslight.png)

### bootstrap3

![bootstrap3](https://github.com/mixu/markdown-styles/raw/master/screenshots/bootstrap3.png)

## Adding new styles

Create a new directory under `./output/themename`.

If a file called `./layouts/themename/page.html` exists, it is used, otherwise the default footer and header in `./layouts/plain/` are used.

The switcher is an old school frameset, you need to add a link in `./output/menu.html`.

To regenerate the pages, you need node:

    git clone git://github.com/mixu/markdown-styles.git
    npm install
    make build

To regenerate the screenshots, you need cutycapt (or some other Webkit to image tool) and imagemagic. On Ubuntu / Debian, that's:

    sudo aptitude install cutycapt imagemagick

You also need to install the web fonts locally so that cutycapt will find them, run `node font-download.js` to get the commands you need to run (basically a series of wget and fc-cache -fv commands).

Finally, run:

    make screenshots

