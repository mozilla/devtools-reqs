# Resource Maps

*Firefox Developer Tools Team*

## Initial goals for MVP

At it’s most basic, resource maps allow us to map a localhost url to a folder on the filesystem and then provide editing functionality to improve the workflow of the developer. In particular: editing or processing source files and reloading the site based on file changes.

## The Problem

Browser developer tools are great at allowing developers the ability to manipulate web pages on the fly, however it can be exceedingly difficult to then track, extract and properly save the changes or tweaks back to disk. Current trends in web development actually make this harder:
1. module systems such as RequireJS compile and minify sources.
1. alternate syntax systems like sass, coffeescript and jade make it difficult to edit the ‘real’ source of the site in their original syntax.
1. browsers don’t surface any kind of diff interface between what has been loaded and the current tweaked state.

## Chrome Workspaces: a minimal start
Chrome workspaces allow developers to minimally map a url to a directory in order to be able to save web resources back to disk. If you’re nly editing standards-based syntax with no minification, this works well.

## The ‘Build Step’, ResourceMaps and SourceMaps

Implementation of SourceMaps allows us to back from what the browser requested through the developer’s toolchain to wherever they actually wrote the code. ResourceMaps expand this out slightly farther to complete the circle, letting us open the right file from the right directory for a given web server.


## Non-goals for MVP

Although there are a number of common remote-editing workflows where developers use ssh-ish protocols, we should concentrate instead on providing a great, simple local solution. We should consider how to allow support for remote protocols like sftp via extensions.

## Developer scenarios

### All local

In the best case scenario the files are local and the server is being run on localhost. Given this power we can react to local file changes as the user edits and update the browser on the fly, magically providing the live editing experience.

### Remote, but local-ish

Developers often mount remote filesystems using afp, nfs or samba in order to edit sources on the server as if they were local files. In the best case scenario this is a low-latency, high-speed connection to a virtual machine running locally where there would be no noticeable difference in performance, however monitoring methods like file watchers won’t work efficiently and should be optional.


### All Remote

Firefox as a product should not need to ship with the kind of extra infrastructure needed to access ssh / sftp-based or webdav file servers - while it would be interesting to try to support these sorts of connections via an extension framework there are already common OS-level solutions for this, particularly on UNIX systems ( sshfs, for example ). This use case is best left to be considered so that we do not prevent extension developers from implementing support?


## User stories

### Epic: SASS tweaking

An app developer updates a local copy of her new app’s github repo and starts Firefox Nightly. She switches to Terminal, and runs ‘grunt server’, then opens ‘http://localhost:8000’ in a new tab in Nightly.

Something is not quite right with how the css looks so she switches to Nightly and inspects some of the elements in the navigation bar. She clicks on the link to the file and line number in the relevant sass file, makes some edits and hits Cmd+S to save the file. Nightly has read the projectmap.json file as well as the sourcemap captured in the generated css file so it knows exactly where to save the sass to. On save Firefox is also smart enough to run grunt again to re-generate the css, and then it reloads the css into the current page.

### User stories table

|ID | Name   | Story    | User  | Priority 
--- | --- | :--- | --- | ---
ResourceMap-001|Simple Mapping|When running a ‘localhost’ web server to create a web app, developers are able to map that host to the directory that contains the html, js and css files for the site.|All Local|1
ResourceMap-002|Inspect then Edit|A web developer can inspect a page, identify the resources loaded by the page and then edit these resources.|All Local|1
ResourceMap-003|Save to Disk|Changes to files that have been edited are saved to the mapped folder.|All Local|1
ResourceMap-004|Sourcemap allows access|If a sourcemap is present, the developer should be able to open source files directly instead of generated files.|All Local|2
ResourceMap-005|Transpilation Triggered!|If a sourcemap exists, saving changes triggers whatever transformer is configured to transpile the source file into the web-standard generated fle.|All Local|2
