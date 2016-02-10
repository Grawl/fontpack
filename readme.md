# FontPack

### Sass mixin to create `@font-face` for custom fonts.

[![No Maintenance Intended](http://unmaintained.tech/badge.svg)](http://unmaintained.tech/)

use [`postcss-font-magician`](https://github.com/jonathantneal/postcss-font-magician) instead

---

Bulletproof syntax from [FontSpring article](http://www.fontspring.com/blog/the-new-bulletproof-font-face-syntax)

## Quick start

File tree:

- style.css
- fonts
	- PTSans-Regular.woff
	- PTSans-Regular.eot

`style.sass`

```sass
+fontPack('PTSans-Regular')
```

`style.css`

```css
@font-face {
  font-family: "PTSans-Regular";
  src: url("fonts/PTSans-Regular.eot");
  src: url("fonts/PTSans-Regular.eot?#iefix") format("embedded-opentype"),
  	url("fonts/PTSans-Regular.woff") format("woff"); }
```

## Configuration

You can choose what formats you want to use with conditional variables:

Variable | Description | Default
---|---|---
`$fontPack-eot` | Embedded OpenType | `true`
`$fontPack-woff` | Web Open Font Format | `true`
`$fontPack-ttf` | TrueType Font | `false`
`$fontPack-otf` | OpenType Font | `false`
`$fontPack-svg` | SVG font | `false`
`$fontPack-path`| Path prefix | `fonts/`

Just add them **before** you `@import fontpack` and they will be applied.

Like this:

```sass
$fontPack-eot: false
@import /bower_components/fontpack/fontpack
```

*If you want to drop IE<9 support.*

## Formats

By default there is only EOT and TTF.

- EOT for IE6-8
- WOFF for all others

Short reference to Can I Use:

- Everybody can WOFF http://caniuse.com/#feat=woff
- Only Webkit can SVG http://caniuse.com/#feat=svg-fonts
- Everybody except IE can TTF/OTF http://caniuse.com/#feat=ttf
	- no support for IE<9
	- partial support for IE9-11

> So why no TTF/OTF? I am already have it from designer.

Because:
- probably you have to support IE<9 with EOT
	- To convert TTF/OTF to EOT you need a font converter program. Any multi-format font converter can give you WOFF. (list below in [References](#references))
- or just want to embed lightweight file.
	- TTF/OTF from your designer is not a lightweight file to embed into your website, and WOFF is here to cover this issue.

So in any case better to have WOFF or you already have it.

## Reference

- [Bulletproof @font-face Syntax](http://www.paulirish.com/2009/bulletproof-font-face-implementation-syntax/) on Paul Irish blog
- [Best Practices for Serving Webfonts to IE9](http://www.fontspring.com/blog/fixing-ie9-font-face-problems) on Fontspring – Short reference on font formats
- [Can I Use Article](http://caniuse.com/#feat=ttf) on browser support
