#HTML / JS / CSS Authoring

### The "triangle of death"

Using Firebug and Firefox developer tools currently, there is a 3-stage code tweaking process that is the source of frustration for many developers:

1. open page in a tab
1. open tools
1. use the tools to tweak markup and css
1. when everything is ready, extract the modified code out into a text editor and save the appropriate files
1. hit refresh on the browser

Smarter, more seasoned developers will do this at a high frequency to incrementally change the page, making the extraction aspect of steps 2 -> 4 much more reasonable. They may also have a file watcher script ( eg written in node.js using watchr ) that somehow triggers the page reload. They still have to hand-patch css changes from the browser tools into their text editor, and this is the key part we're trying to fix.

### Competitive landscape

- [Chrome Workspaces](http://odetocode.com/blogs/scott/archive/2013/07/15/chrome-workspaces-edit-source-from-the-chrome-dev-tools.aspx) see [Chrome Devtools Revolutions](http://www.html5rocks.com/en/tutorials/developertools/revolutions2013/)

#### Browsers

Chrome's workspaces feature ( currently in Canary ) includes url mappings similar

#### Reload Tools

It's fairly easy to take a [file watcher script](https://github.com/canuckistani/reload-my-tab/blob/master/reload-server/server.js) and pair it with some sort of [browser integration](https://github.com/canuckistani/reload-my-tab/tree/master/addon) to reload web pages in reaction to filesystem changes.

- watchr, compass and various other cli-based command-line filesystem watchers.
- [LiveReload](http://livereload.com/) is a commercial app that does this.

### User Types

 - Web Dev Generalists: jack of all trades, maybe a little fuzzy on the hoisting problem or the darker corners of CSS3
 - CSS Stylists: front-end / production developers who mainly create markup, images and CSS based on Photoshop layouts and some scripting.
 - JS Framework-oriented Hacker: professional web developers working for all types of companies hacking together dynamic / single-page apps using frameworks & libraries like Backbone, Angular and Ember alongside widget sets like topcoat.io.
 - Mobile App developers: developers working on Firefox OS, Mobile Web Apps, Phonegap developers, chrome web app developers, etc. Key differntations from previous user types is a focus on memory limits, performance and on-device tools support.

### Epic Scenario

*TBD*

### User Stories

- when inspecting markup, scripts or css for a particular page, I should be able to click on a button or hit a keyboard combination to switch to editing mode
- if I have set up a resourcemap for the current page I should be able to hit Ctrl|CMD+S to save the current changes to disk.
- the current tab should change dynamically as I edit, even without saving
- if a sourcemap is present, 
- if I am using a common alternative syntax such as stylus or coffeescript and a sourcemap has been used, the original alternate source should be opened for editing

Unresolved:
- how should transpilation work on file save?
