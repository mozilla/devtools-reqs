# The Developer Tools API - PRD DRAFT

*Firefox Developer Tools Team*

## Background

Firefox became wildly popular amongst web developers shortly after its initial release in 2006 and revolutionized web development. It is fair to say that the tools created by Google, Apple,, Microsoft since then are largely in reaction to the potent Firebug + Firefox combo, and for a few years most sane web developers lived and breathed Firebug as a tool.

As well, Firebug’s strengths and weaknesses have been hugely influential on the design goals for Firefox’s new integrated tools. We have largely kept the expected UI design metaphors, and we have put enormous amounts of effort into making the tools much more performant than Firebug has become.

An additional aspect of Firebug that we take inspiration from is its baked-in extensibility and ecosystem of extensions. Extensibility in tools was a key differentiator for Firebug but also an additional source of friction with users due to increasingly poor performance.

## Prior Art

### Firebug

Firebug has a diverse and somewhat inactive extension scene:

* http://www.softwareishard.com/blog/extending-firebug/


Interesting examples include FirePHP, FireDrupal, Firequery, Illuminations.

### Chrome

Chrome devtools feature limited support:
* http://developer.chrome.com/extensions/devtools.html

Interesting examples include Batarang, the Coffee Repl, Tincr in particular as it provides the ability to save edited changes back to disk.

## Existing Work

Paul Rouget has created some apis here:
https://developer.mozilla.org/en-US/docs/Tools/DevToolsAPI

The main existing example is [JSTerm](https://github.com/paulrouget/firefox-jsterm).

## User Types

### Firefox Extension developers

We have a fairly stable pool of several thousand extension developers who publish extensions on AMO and are therefore are already familiar with the gecko platform, XUL, Mozilla’s slightly more advanced version of JS, etc. For bonus point, those who have created extensions based on Jetpack also already know it’s own idioms including the node.js-esque CommonJS module system and standard SDK libraries.

### Firebug hackers

Firebug has a small, dedicated community of people that provide extra functionality. In particular this group seems to have a strong interest in monetizing their add-ons to Firebug using a freemium / shareware model or via donations and commercial support, for example:
1. Illuminations: http://www.illuminations-for-developers.com/
2. FirePHP: http://www.firephp.org/HQ/Contribute.htm

### Chrome devtools extension developers

There is a strong existing trend of chrome-based web development extensions that leverage the extension apis ( inspectedWindow ). [2] ( network ) [3] ( panels ). An interesting use case is that of passionate web developers attempting to smooth out the developer experience across browsers by offering a similar experience. If there is, for example, a developer or group of developers that want to provide support for a specific new framework or library, they should be able to create a similar development experience regardless of the browser being used, and without wildly disparate implementations.


### Web developers

For web developers, the challenge is to offer an environment that is not completely dissimilar from what they are used to. Chrome achieves this particular aim better than we do by mainly using html documents to implement pop-ups or background pages. The SDK adopted CommonJS ( and we benefit here via the popularity of node.js ) however we have been trending towards more web-like development for a couple of years, via experiments like the addon page module as well as newer features like the window module ( that can access DOM apis to main.js ) or the ability to communicate from local documents directly to main.js via the ‘addon’ global.

### Adding a tool pane to the toolbox

Developers will want to create their own specialized tool and have it appear within our toolbox just like any of the default tools. 

**Prior art**: The initial prototype of the devtools api already enables us to place a document into the toolbox.



* I want to add my own tool to the toolbox.
* My custom tool should behave the same as any other tool in terms of how it appears, how it is activated, how it can be hidden in settings
* When I look at the settings, it should be clear to me that this custom tool comes from an extension, and which extension it is.
* If I use unstyled content in my tool,the default appearance should match the color scheme and fonts of the developer tools in general.
* If I use unstyled content in my tool, it should react and match changes to the global devtools ‘theme’
* Scripts run in the tool pane should have access to the DOM of the current active tab.
* I should be able to add a new panel to the DOM Inspector's side panel.

### Integrating with the Web Console

Adding logs to the web console or modifying how existing logs appear is a key feature of many popular Firebug extensions such as FirePHP.

* I want to add messages to the web console
* I want to add a new category of message ‘types’ to the web console, thereby allowing users to either exclusively select or remove my custom messages.
* For a specific type of messages I want to be able to add additional metadata to the log message.
* For a specific type of messages I want to be able to add additional metadata to the variable viewer pane that is visible when the log line is clicked.
* I want to be able to alter the appearance of specific types of log messages.

### Integrating with the Network Monitor

* I want to add specific actions to a context-menu when a developer right-click on a network request.
* Let’s do something with $request|I want to implement an add-on that adds a “open XML response in a new XML View tab” contextmenu item only for xhr requests that actually return an xml imetype.|All|
* I want to be able to add custom output modes to let users visualize response bodies

### Integrating with the App Manager

As we build out our app manager and authoring stories for developers, it seems obvious that we should provide key integration points with code sources such as github. Integrating with a specific 3rd party like Github directly in Firefox seems like an uncomfortable fit. This space in particular is where we should instead provide the right integration points and allow developers to integrate with services as they see fit.


* I want to start all new projects using a repository on Github as the base. 
* I use node.js and need the local web server to be re-started or otherwise triggered to re-load my app on file changes
* I use grunt / yeoman / nodemon etc to manage my asset pipeline and want Firefox’s app manager to be able to use them. 

### Dashboard / Status widgets

This set of requirements assumes we are keeping the developer toolbar and therefore are interested in providing add-on developers access to place live widgets in this area. This assumption is somewhat dangerous as we have also discussed removing the developer toolbar completely. 

Anyway, here are some basic user stories that capture how this could work:

* I want to add ‘status indicator ui’ to the developer toolbar so that key pieces of info related to my extension are always visible
* I want to be able to update the content in the widget continuously.
* I want to have some visual indication that an update has happened, so user’s attention will be captured.

### Remotability

Any high-level apis we provide should be remote-capable, meaning that developers using high-level apis should not have to do anything special to gain remote functionality.

Conversely, developers may want to create much deeper integrations that involve custom remote server actors. It should be possible to register new actors on the server to support novel add-on client implementations.

### Adding support for $

Web technology and techniques are a fast-moving target, and what is the new hotness this year might get old-n-busted in a few months or even weeks. If we chase trends as a team and try to ship any and all trendy frameworks we are just setting ourselves up for frustration and the thrill of always chasing the new thing. Instead, we should figure out how to enable framework and tooling developers to integrate their new shiny with our solid base.


* I’m the lead developer of a hot new COBOL / BASIC syntax language project that compiles to JS, and I would love to be able to create a Firefox extension that integrates my transpiler script, syntax highlighting, debugging support.
* As a student studying programming language design, I would love to be able to be able to bootstrap a full programming environment for my new language by transpiling to JS and implementing tools support in a Firefox extension.
* All of the designers at my firm use stylus for styling content, and we need to be able to live-code style tweaks and seem them on-device.
* If I paste stylus or sass into the style editor, Firefox should try to guess what the syntax is based on some heuristics.|All|P2|
* I should be able to add stylus or sass support to the style editor and force Firefox to treat a given file or buffer as if it was that language, overriding defaults.|All|P1
* I am a JS framework developer and I want to customize the output of my framework's objects in the webconsole/variables view *anywhere* they are displayed.

### GCLI

GCLI and the developer toolbar are a powerful keyboard-driven way to interact with the developer tools, and it is already very simple to write and publish custom GCLI commands as extensions. We can make it even simpler.

* As a user I want to expose functions from my extension as GCLI commands.
* If I write a script in scratchpad that automates something in Firefox, I should be able to easily export it as an installable extension.
