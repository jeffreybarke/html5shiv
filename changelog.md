# html5shiv changelog

## v3.3

### v 3.3
complete refactoring by jdalton

* huge performance improvement on createElement (more than 10 times faster compared to 3.2)
* improved inline documentation

### v 3.1/3.2

* fixed issue with vml elements
* small performance improvement for createElement (1.6 times faster compared to 3.0)

### v 3.0
Complete rewrite by jonathantneal

* print iframe fix
* includes normalized styles for unknown elements
* fixes createElement/createDocumentFragement for unknown elements

#### **As of April 18th, 2011**, [html5shim](http://code.google.com/p/html5shim/), [html5shiv](http://code.google.com/p/html5shiv/), [modernizr](https://github.com/Modernizr/Modernizr) all have been updated to use iepp v2.

## v2 changelog

here is the list of fixed issues and made changes. I have also added a list of known issues (The first one is really critical, but needs a lot work...).

### Fixes:

* print error on second print/print preview
* allow styling through body id (i.e.: `body#some-id article`)
* wrong selector parsing in IE8 (subbug: `@media print { }` blocks in `media=all` stylesheets are ignored, but fixed a lot more than just that)
* alternate/disabled stylesheets aren't parsed (can solve problems with mediaqueries polyfills/styleswitchers)
* styles with multiple media declaration or mediaqueries (i.e.:` media="screen, projection"`, `media="only screen..."`) are not used as print styles (unless, they have print or all medium) (this also fixes a lot of slowness and crashes)
* reset default media type to `"all"`, with every new stylesheet (fixes errors, if a stylesheet had no media attribute, but the previous  had a non-print media-attribute)

### Features:

#### Configuration:

* iepp.html5elements:  override shimed html5elements (developer can add additional html5elements or reduce the elements)
* iepp.disablePP: disables print protection without disabling standard shiv (in case, print protection causes too much trouble, it's still a big hack)

#### Extras:
* simple testsuite 
* [unofficial] API (created for testing, but can be used for monkey patching)


### Known issues:

* `@media screen {}` blocks in media all are treated as print-styles (This would need a big rewrite)
* selector order (Currently, this seems "by design", but should be changed. Also needs a big rewrite)
* change of selector specificity (`.iepp_article <-> article`) (Currently this seems "by design", but for IE7 and IE8, it can be changed to` [data-iepp-elem="article"] `<-> `article`)

Before someone is looking into the first two known issues, we should create good performance tests. Fixing last issue only makes sense, if we also fix the selector order...

cheers
alex