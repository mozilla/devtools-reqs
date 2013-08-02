# Transpilers

*Transpiler: a script that takes one syntax (typically a non-standard scripting, document or style syntax) and transforms it  into the web-standard languages of HTML, Javascript and CSS*

There is an increasing proliferation of alternate syntaxes being used by web developers that rely on command-line scripts to transform the alternate syntax

## More popular examples

* Coffeescript ( => JS )
* Livescript ( => JS )
* ClojureScript ( => JS )
* Dart ( native *or* JS )
* SASS ( => CSS )
* LESS ( => CSS )
* Stylus ( => CSS )
* Jade ( => HTML )
* HAML ( => HAML )

## Rising Prevalence

If you use node's express framework to write apps, by default you get a stubbed app that uses Javascript, Stylus and Jade, and express handles the transpilation to CSS and JS dynamically when you run `node app`.

Likewise, conferences like TXJS feature several talks on SASS or Stylus, espousing the various advantages of using the alternative syntax particularly for managing styles on large and complex web applications.

## Standards are SLLLOOOOOOOOOWWWWWW, dude

Underlying these technologies is an undercurrent of dissatisfaction with progress in web standards or the scalability of the underlying web standards. Web developers are taking matters into their own hands and creating new syntax

## Trends

### Scripting

* generally the itch being scratched is bolting some other programing paradigm onto JS:
** LiveScript - type inference and C#-esque classes
** coffeescript - odd combination of some ruby and python features, syntax is particularly popular with rails developers.
** functional languages like Clojure, Haskell, Lisp
** Dart - a deliberate wedge technology to drag the web platform towards multiple languages for scripting ( failed at this point? )

These new syntaxes are in some cases quite divisive, use of them could be seen as either a matter of taste or pedantic rejection of JS as a language, or a very real solution to the dangers of JS' inconsistency.

### Styling

CSS Pre-processors could be seen as a much more pragmatic solution to the problems of scaling css styles out to very large websites. Unlike the scripting syntaxes, the styling syntaxes bring major features to web developers that are simply absent from CSS.

### Layout

There are fewer complete alternatives to HTML, in particular HAML and Jade which are linked to the Rails and Express MVC-ish frameworks. Jade in particular is popular in the node.js community and this community is growing expansively.

### Concatenation

Require.js, Browserify, these systems provide an asynchronous module loading system in the browser and as well they make it possible to concatenate / compile all dependencies down to a single file.

### Compression

The grandaddy of the transpiler scene, minifiers were cool before you ever heard of them. Early in the web 2.0 days JS minification became a hot new way to reduce downloads and improve performance of websites that were just starting to become more dynamic. These days for high-traffic

### Sprites or Base64?

Images have less interesting tech generally built in, but we have seen two basic techniques gaining favour in high-traffic sites:

* Base64 encoding of smaller images as data uris into the hmtl itself, or css
* providing single images as sprites that contain anywhere from a few to dozens of smaller images or icons.

### It's the source, stupid

The challenges to tooling presented by the stack of tools developers might be using is enormous - fortunately we have a powerful weapon available to us to untangle all of this, namely SourceMaps. Given this scenario:

* a developer is writing all of their code in alternative syntaxes: coffeescript, stylus and jade.
* they are using the require.js module system to load script dependencies, and when the site is deployed to production it is concatenated into 2 files and then minified.
* similarly html files are generated from jade and css stylesheets are generated from stylus
* a node.js-based file watcher built into the local development 

### Deployment techniques

Two key related blog posts:

1) "No Buids": http://www.futurealoof.com/posts/no-builds.html

"The routes we write for resources that would normally be the output of a build process we generate the first time they are requested and cache them in memory indefinitely..."

This is essentially an old PHP / Perl idea called 'funky caching', a resource is requested, generated the first time and then cached until it is no longer valid.

2) "Deploying JavaScript Applications": http://alexsexton.com/blog/2013/03/deploying-javascript-applications/

"Locally, you might run a static server with some AMD modules, or a “precompile server” in front of some sass and coffeescript, or browserify with commonjs modules. Whatever you’re doing in development is your choice and not the topic du jour.

The hope is that you have a way of taking your dev environment files and wrapping them up into concisely built and minified JavaScript and CSS files."

There seems like a fairly stark difference in opinion here, but the difference in approaches really amounts to deciding when you run the transpilation code for a given resource, and how you cache the result. The latter approach favours pre-deploy scripts that cache on the filesystem as the source of truth, whereas the former instead just processes the source on first request and then uses things like memcache or varnish to serve the results.