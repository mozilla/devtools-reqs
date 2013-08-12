# Add-on Debugger

### Epic

Mike is an underemployed web developer and full-time Reddit troll / admin who has grown dissatisfied with the limited features of the otherwise popular Reddit Enhancement Suite (RES) add-on. As a Firefox user he disocvers that the extension is built with Mozilla's Add-on SDK and the source is hosted on github, so he creates a github repo, forks the source, reads a few snippets of git, JS and extension documentation and sets about making things right.

* first step: run the cfx tool to create a local build of RES from his forked repo.
* Mike looks at Firefox's about:addons page to confirm that the installed version of RES is indeed his ( he changed the name to 'mIK3z RES, derp!' ) and notices that there is a 'Debug' button next to the extension's entry. He clicks on this button and a debugger toolbox window opens and displays main.js from RES, with execution paused at the very first line. He is able to step through all of the code in main.js that loads the various features of RES.
* Most of RES' functionality involves content scripts. Mike notices one in particular that looks interesting in the list of files on the left side of the debugger UI. He clicks on it, sets a breakpoint in an event handler, then disables and re-enables the add-on. Again the debugger starts up and pauses on the first line. He hits the Resume / 'go' ( |> ) button and the debugger then pauses at the breakpoint he set in the content script.
* After some digging around in the source Mike makes some moderate success changing the UI and behavior of RES, occasionally using the debugger to step through content script code and see how it is actually working. Between the debugger and some printf-style logging via the browser console, he makes good progress towards implementing his desired features.

### User stories

1. I should be able to launch the add-on debugger from the Add-on Manager for a specific add-on.
1. I want to be able to focus on my add-on specifically without being distracted by other Firefox source code.
1. When debugging my add-on I do not want to step through the SDK's own modules or other Firefox platform code.
1. In some cases it would be useful to opt-in to stepping through Firefox code.
1. I need to be able to debug my add-on's initialization code.
1. If I add the pseudo-standard 'debugger;' statement to my code, I expect the debugger to treat it as a breakpoint.
1. I want to be able to optionally break on uncaught exceptions, similar to how the other debuggers work.
1. I need to be able to debug add-ons running on a remote device, for example Firefox for Android.


