# Add-on Developer Tools - DRAFT

As a content type hosted on AMO, extensions have never been more popular. We host thousands of extensions and downloads metrics consistently clock in at 30 million per month or so.

At the same time, Mozilla has yet to produce a set of developer tools that addresses the requirements of developers. printf-style debugging is basic at best thanks to the ancient Error Console, no actual step & breakpoint debugging experience, and a difficult-to-debug technology stack.

Add-on Builder was an interesting experiment in trying to webify add-on development but it lacked a key list of functionality:
1. no debugger
2. extremely basic logging
3. no way to run tests
4. no mobile support

It is not overstating things to say that some of the largest innovations of the web browser to date have all come from a diverse group of a few thousand Mozilla  / extension developers. All labs projects that integrate with the browser start off as extensions. Firebug is an extension that has spawned its own extension ecosystem.

### Goals
1. build on the infrastructure provided by the devtools team
2. provide a ‘happy path’ for add-on prototyping; simple things should be easy.

### Non-Goals
1. build an IDE
2. build a web app
Competitive Landscape


Chrome DevTools support for extensions is minimal:
1. inspection of pop-up html
2. debugging of content scripts ( in the regular tools ) and pop-ups ( in a special, ephemeral window )
3. no real story for background scripts?


### Prior Art
1. scratch-kit
1. https://github.com/Gozala/scratch-kit/
2. simple prototyping
3. does not re-load on run, easy to get to eg widget id conflicts
1. jetpack-console
1. Alex’s: https://github.com/ochameau/jetpack-console
2. Irakli’s: https://github.com/Gozala/jetpack-console
1. extension-developer-extension
  1. Crazy, does bootstrapping of extensions
1. venkman
  1. bad UX, no longer supported
1. DOM Inspector
  1. bad UX, no longer supported
1. Add-on Builder
  1. imperfect IDE / Editor
  2. extension dependency for running  / testing addons
  3. no mobile support

### Epic: Hacking Reddit

Joe is a recently unemployed web developer and part-time Reddit admin. He has a lot of spare time on his hands and has a long list of personal gripes around Reddit's usability and...

### Console logging

The browser console is our friend here, with some limitations: https://bugzilla.mozilla.org/show_bug.cgi?id=879019

|ID | Name   | Story    | User  | Priority    | 
|--- | --- | :--- | --- | ---|
addon-tools-01||I should see messages sent from console.* in the Browser Console ( or equivalent )|All|P1
addon-tools-02||If I call console.log(Object), I should see a nice browse-able representation of that Object in the variable pane.|All|P1
addon-tools-03||I should be able to filter console output to only show errors, warnings and messages from my add-on code.|All|P1

###Debugging

Debugging main.js and similar scripts works in the browser console, with some caveats. General add-on debugging is broken last time I checked for eg bootstrap.js based add-ons.

|ID | Name   | Story    | User  | Priority    | 
|--- | --- | :--- | --- | ---|
|xpi-tools-01|Focus|I want to be able to focus on my add-on specifically without being distracted by other Firefox source code.|All|P1
|xpi-tools-02|Initialization|I need to be able to debug my extension’s initialization code.|All|P1
|xpi-tools-03|Standards|The debugger should honor the pseudo standard ‘debugger;’ statement and treat it as a breakpoint.|All|P2
  
###Project Management

Projects  should be as simple as possible, but no simpler!

|ID | Name   | Story    | User  | Priority    | 
|--- | --- | :--- | --- | ---|
|xpi-tools-|Get Started|I should be able to start a new project via the UI or gcli.|All|P1
|xpi-tools-|Find a place.|I should be able to pick or create a new project folder.|All|P1
|xpi-tools-|Tweak the Meta|I should be able to initially define or later adjust all of my project meta-data ( add-on author, version, etc ) via the UI|All|P1
|xpi-tools-|Publish|I want to be able to upload an extension version directly to AMO from the UI.|All|P2
|xpi-tools-|Dev Cycles|I want to be able to reload, test or package an extension directly from the UI via the mouse or key commands.|All|P1
|xpi-tools-|Boilerplate|As a developer I want to be able to generate an initial skeletal add-on project.|All|P1
|xpi-tools-|Useful Boilerplate|The code produced by default in this process should be both as minimal as possible an|well documented.|All|P2
|xpi-tools-|My Boilerplate|It should be possible to provide a directory, archive or url as an alternative base template for starting new projects.|All|P3
|xpi-tools-|Hand-code the Meta.|I need to directly edit package.json properties from the UI.|All|P2
|xpi-tools-|Save me from myself.|When editing package.json, the project manager should check the JSON syntax and report errors and warnings.|All|P2|

###Authoring

Currently, we have no story for actually writing code.

|ID | Name   | Story    | User  | Priority    | 
|--- | --- | :--- | --- | ---|
|xpi-tools-|Code now!|I want to be able to quickly hack on and prototype an extension.|All|P1
|xpi-tools-|Back me up.|My prototype code should be saved to the filesystem as an extension even if we don’t yet have a proper extension project.|All|P1||xpi-tools-|Core SDK Completion.|The built-in editor should know about and offer completion for the SDK’s built-in APIs|All|P2||xpi-tools-|3rd party completion.|The built-in editor should know about and offer completion for any third party modules being used in the project.|All|P3|

###Packaging

Over the history of Firefox extensions, Mozilla developers have always been really happy to point out that an .xpi file is ‘just a fancy zip file’. This is both true and unhelpful to developers getting started with the platform who need to learn all sorts of additional info about the xpi file format in order to even get to hello world. Chrome’s approach is both much better, and a bit too simplistic. The simply ask you to point chrome at a filesystem directory, and assume you’ve read the docs enough to produce a workable JSON manifest.

|ID | Name   | Story    | User  | Priority    | 
|--- | --- | :--- | --- | ---|
|xpi-tools-|Fast Hacking|I need to be able to load, unload or reload my in-progress extension without re-starting the browser.|All|P1
|xpi-tools-|Fast Packing|I need to be able to package the extension via a mouse action or key command.|All|P1
|xpi-tools-|Protection|The packager should validate the extension project to ensure that there are no syntax errors or other fatal errors prior to loading, packaging or testing an extension project.|All|P2|

### Testing

The SDK’s testing framework is a very necessary part of its development and we should enable easier use of the test framework for developers who do write tests for their own extensions.

|ID | Name   | Story    | User  | Priority    | 
|--- | --- | :--- | --- | ---|
|xpi-tools-|Testing support|If tests exist for an extension project, it should be possible to run them via a mouse action or key-command.|All|P2
|xpi-tools-|Auto-tests!|I’d like to have tests run every time the js/html/css files in my extension project change.|All|P3
|xpi-tools-|Visual Feedback|Current test status should be displayed in the UI.|All|P3|