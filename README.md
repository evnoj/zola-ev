# changes from upstream
This branch adds math support, by simply applying [Apanatshka](https://github.com/Apanatshka)'s [branch with the implementation](https://github.com/Apanatshka/zola/tree/latex2mathml) to the current Zola `master`. All credit goes to Jeff Smits (Apanatshka) for the idea and implementation.

> this branch will be rebased on top of mainline `master` and force-pushed semi-regularly

To use it, add `math = true` to the `[markdown]` section of your site's `config.toml`. Then, you can use LaTeX syntax within dollar signs in your markdown files. Single dollar signs is inline, and double dollar signs is a block.

```md
An inline expression: $ x \cdot y $

A block expression: $$ x \cdot y $$
```

It is rendered as [MathML](https://developer.mozilla.org/en-US/docs/Web/MathML) and placed inside a [`<math>`](https://developer.mozilla.org/en-US/docs/Web/MathML/Reference/Element/math) element. This should be well-supported by modern browsers.

The supported LaTeX expressions are documented [here](https://docs.rs/latex2mathml/latest/latex2mathml/#supported-latex-commands), by the [latex2mathml crate](https://docs.rs/latex2mathml/latest/latex2mathml/) which peforms the rendering of LaTeX to MathML.

To use a regular dollar sign, escape it with a backslash: `\$1.00`. Using a dollar sign in a paragraph with no other dollar signs should also work fine to render it as the `$` character.

Building is just like any standard Rust project. `cargo build` will make the build to `target/debug/zola`, `cargo build -r` will make an optimized "release" build to `target/release/zola`.

## notes
- Should likely switch to the [math-core](https://github.com/tmke8/math-core) crate for the LaTeX to MathML conversion, as it seems better maintained and focuses on "MathML Core", a simplified modern version of MathML that seems to be the future.
- I'd also like to look into enabling AsciiMath support via [mathemascii](https://github.com/nfejzic/mathemascii)

# zola (né Gutenberg) <img src="docs/static/logos/Zola-logo-main-coffee.svg" align="right" alt="zola logo" width="30%"/>

[![Build Status](https://dev.azure.com/getzola/zola/_apis/build/status/getzola.zola?branchName=master)](https://dev.azure.com/getzola/zola/_build/latest?definitionId=1&branchName=master)
![GitHub all releases](https://img.shields.io/github/downloads/getzola/zola/total)

A fast static site generator in a single binary with everything built-in.

To find out more see the [Zola Documentation](https://www.getzola.org/documentation/getting-started/overview/), look
in the [docs/content](docs/content) folder of this repository or visit the [Zola community forum](https://zola.discourse.group).

This tool and its template engine [tera](https://keats.github.io/tera/) were born from an intense dislike of the (insane) Golang template engine and therefore of
Hugo that I was using before for 6+ sites.

# List of features

- [Single binary](https://www.getzola.org/documentation/getting-started/cli-usage/)
- [Syntax highlighting](https://www.getzola.org/documentation/content/syntax-highlighting/)
- [Sass compilation](https://www.getzola.org/documentation/content/sass/)
- Assets co-location
- [Multilingual site support](https://www.getzola.org/documentation/content/multilingual/) (Basic currently)
- [Image processing](https://www.getzola.org/documentation/content/image-processing/)
- [Themes](https://www.getzola.org/documentation/themes/overview/)
- [Shortcodes](https://www.getzola.org/documentation/content/shortcodes/)
- [Internal links](https://www.getzola.org/documentation/content/linking/)
- [External link checker](https://www.getzola.org/documentation/getting-started/cli-usage/#check)
- [Table of contents automatic generation](https://www.getzola.org/documentation/content/table-of-contents/)
- Automatic header anchors
- [Aliases](https://www.getzola.org/documentation/content/page/#front-matter)
- [Pagination](https://www.getzola.org/documentation/templates/pagination/)
- [Custom taxonomies](https://www.getzola.org/documentation/templates/taxonomies/)
- [Search with no servers or any third parties involved](https://www.getzola.org/documentation/content/search/)
- [Live reload](https://www.getzola.org/documentation/getting-started/cli-usage/#serve)
- Deploy on many platforms easily: [Netlify](https://www.getzola.org/documentation/deployment/netlify/), [Vercel](https://www.getzola.org/documentation/deployment/vercel/), [Cloudflare Pages](https://www.getzola.org/documentation/deployment/cloudflare-pages/), etc
