<p align="center"><img alt="Citation.js" src="https://citation.js.org/static/img/square_logo_medium.png" /></p>

Citation.js converts formats like BibTeX, Wikidata JSON and ContentMine JSON to CSL-JSON to convert to other formats like APA, Vancouver and back to BibTeX.

---

<p align="center"><a href="https://citation.js.org">Site</a> • <a href="https://github.com/larsgw/citation.js">Repo</a> • <a href="https://citation.js.org/api/tutorial-getting_started.html">Getting Started</a> • <a href="https://citation.js.org/api">Documentation</a> • <a href="https://citation.js.org/demo">Demo</a></p>

---

[![NPM version](https://img.shields.io/npm/v/citation-js.svg)](https://www.npmjs.org/citation-js)
[![NPM total downloads](https://img.shields.io/npm/dt/citation-js.svg)](https://npmjs.org/citation-js)
[![Build Status](https://travis-ci.org/larsgw/citation.js.svg?branch=master)](https://travis-ci.org/larsgw/citation.js)
[![Dependency Status](https://david-dm.org/larsgw/citation.js/status.svg)](https://david-dm.org/larsgw/citation.js)
[![codecov](https://codecov.io/gh/larsgw/citation.js/branch/master/graph/badge.svg)](https://codecov.io/gh/larsgw/citation.js)
[![license](https://img.shields.io/github/license/larsgw/citation.js.svg)](https://github.com/larsgw/citation.js/blob/master/LICENSE.md)
[![DOI](https://zenodo.org/badge/doi/10.5281/zenodo.1005176.svg)](https://doi.org/10.5281/zenodo.1005176)

[![JavaScript Style Guide](https://cdn.rawgit.com/standard/standard/master/badge.svg)](https://github.com/standard/standard)

---

<!-- toc -->

- [Install](#install)
- [Getting Started](#getting-started)
- [CLI](#cli)
- [`Cite`](#cite)
  * [Async](#async)
- [Acknowledgements](#acknowledgements)

<!-- tocstop -->

# Install

On Node.js, install the package ([citation-js](https://npmjs.org/package/citation-js)) like this:

    npm install citation-js

To install the CLI as a global command, do this:

    npm install --global citation-js

Browser releases are available [here](https://github.com/larsgw/citation.js/tree/archive). These define `require` and add `citation-js` as a module.

```html
<script src="path/to/citation.js" type="text/javascript"></script>
<script>
  const Cite = require('citation-js')
</script>
```

# Getting Started

You can read a guide on how to get started, together with some tutorials and examples, [here](https://citation.js.org/api/tutorial-getting_started.html).

# CLI

> [More info](https://citation.js.org/api/tutorial-cli.html)

Run the CLI like this:

    citation-js  [options]

    Options:

      -h, --help                      output usage information
      -V, --version                   output the version number
      
      -i, --input <path>              Input file
      -u, --url <url>                 Input url
      -t, --text <string>             Input text
      
      -o, --output <path>             Output file (omit file extension)
      
      -R, --output-non-real           Do not output the file in its mime type, but as a string
      -f, --output-type <option>      Output structure type: string, html, json
      -s, --output-style <option>     Output scheme. A combination of --output-format json and --output-style citation-* is considered invalid. Options: csl (Citation Style Lanugage JSON), bibtex, citation-* (where * is any formatting style)
      -l, --output-language <option>  Output language. [RFC 5646](https://tools.ietf.org/html/rfc5646) codes

# `Cite`

> [More info](https://citation.js.org/api/tutorial-cite_.html)

To use the [`Cite`](#cite) constructor, `require()` the module like this:

```js
const Cite = require('citation-js')
```

For example, to get the bibliographical data of the Wikidata item [`wd:Q21972834`](https://wikidata.org/wiki/Q21972834), and then format it in HTML, English and APA:

```js 
const data = new Cite('Q21972834')

const output = data.get({
  format: 'string',
  type: 'html',
  style: 'citation-apa',
  lang: 'en-US'
})

console.log(output)
```

To test this code, go to [RunKit](https://runkit.com/larsgw/591b5651bd9b40001113931c).

## Async

Use the async API (recommended for Wikidata, URL, and DOI input) like this:

```js
const data = await Cite.async('Q21972834')

const output = data.get({
  format: 'string',
  type: 'html',
  style: 'citation-apa',
  lang: 'en-US'
})

console.log(output)
```

> `Cite.async()` also supports a callback function as the second or third argument

# Acknowledgements

[![JS.ORG](https://logo.js.org/dark_tiny.png)](https://js.org)

* Thanks to the JS.ORG [DNS service](https://dns.js.org) for the site url!

[<img width="250" alt="BrowserStack" src="https://citation.js.org/static/img/browserstack-logo-600x315.png" />](https://browserstack.com)

* Thanks to [BrowserStack](https://browserstack.com) for the free Open Source plan, allowing me to automate testing browser support, and avoid issues like [this one](https://github.com/larsgw/citation.js/issues/87)!
