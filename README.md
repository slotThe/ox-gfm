# Github Flavored Markdown exporter for Org Mode

> [!NOTE]
> This is a fork of [larstvei/ox-gfm](https://github.com/larstvei/ox-gfm).

This is a small exporter based on the Markdown exporter already existing
in Org mode. It should support most features listed in
[GitHubs GFM docs](https://help.github.com/articles/github-flavored-markdown/).

## Installation

You can install `ox-gfm` using `package-vc.el`:

``` emacs-lisp
(package-vc-install "https://codeberg.org/slotThe/ox-gfm")
```

or, if you use use-package:

``` emacs-lisp
(use-package ox-gfm
  :vc (:url "https://codeberg.org/slotThe/ox-gfm"))
```

## Usage

This package adds an Org mode export backend for GitHub Flavoured
Markdown; see the [Exporting section](http://orgmode.org/manual/Exporting.html)
in the Org manual. You should find a new menu entry upon executing
`org-export-dispatch`, once this package is loaded.

## Comparison to upstream

This fork adds some features for [Hakyll](https://jaspervdj.be/hakyll/) compatibility:

+ YAML front-matter export: the Org mode properties `#+title:`,
  `#+date:`, and `#+tags:` are exported as YAML front-matter at the top
  of the document:

  ``` org
  #+title: My Post
  #+date: 2026-02-01
  #+tags: emacs, org-mode
  ```

  becomes:

  ``` yaml
  ---
  title: My Post
  date: 2026-02-01
  tags: emacs, org-mode
  ---
  ```

+ Footnotes: Instead of some gnarly inline HTML, footnotes are exported
  using the `[^n]` syntax, which is how pandoc wants to see footnotes to
  export them properly. There's also no footnotes section anymore, they
  are just tacked onto the end of the document.
