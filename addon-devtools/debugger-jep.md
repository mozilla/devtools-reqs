This JEP describes the add-on debugger. Currently, the only way to debug
add-ons is to launch the browser debugger, which shows all
Javascript assets currently loaded in the browser. The add-on debugger will
present the same interface, but will be limited only to scripts from
a single add-on.


The steps
---------

The first step is to enable the user to open up a separate debugger session
that allows for debugging a single add-on. The chosen course of action involves
some changes to the Remote Debugging Protocol, i.e. a new actor type will be
implemented that enables debugging of globals pertaining to a particular add-on.

On the GUI side, this phase can reuse the code heavily from the existing browser
debugger implementation, the only main change being the use of a different actor
on the server side, as specified above. The debugger will work naturally as a separate process.

Additionally, the add-on debugger should provide support for debugging content
scripts loaded in browser tabs. They can be displayed in the same debugger window.

The next step is to enable debugging add-ons as they are loaded, i.e. being able
to set breakpoints on entry points of the add-on code. This can be achieved via implementing [bug #882341](https://bugzilla.mozilla.org/show_bug.cgi?id=882341) and then adding a way to explicitly reload add-ons.

Another convenient functionality is to be able to blackbox add-on SDK sources and frames
in the debugger, and enable developers to focus on their own code. The generic support for blackboxing has already landed in the debugger, see [bug #875034](https://bugzilla.mozilla.org/show_bug.cgi?id=875034).

Issues
==========

  + Script globals may be GC-ed even though objects contained in it are still hanging around.
  + Content scripts evaluate multiple times, currently the debugger doesn't recognize
    multiple instances of the same script loaded multiple times.

Dependencies & Requirements
===========================

This JEP is not dependent on any other JEPs.


API
=========

The add-on debugger does not expose any additional APIs, apart of the extensions to the
RDP.

Discussion
==========

https://etherpad.mozilla.org/addon-debugger-discussion
