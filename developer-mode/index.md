# Firefox Developer and Tester modes

Most users will not have multiple installations of Firefox on their system. Those that do fall into two categories:

1. testers who might want to test a given build with their default profile.
2. web and add-on developers who might want to have multiple profiles - one for browsing, the other for development.

The current user experience related to this is terrible and hasn't been reviewed for years:

* upon starting a second Firefox build, we only show an alert that tells us there is another Firefox process using the same profile.
* the ability to create and manage Firefox profiles is hidden behind the command-line flag -ProfileManager
* and the only way to automate starting a given binary with a specific profile is via the command-line flag -P

I hate this workflow so much I spent some time and even wrote a tiny amount of AppleScript code (!) to [make this nicer for me](http://canuckistani.ca/blog/2011/12/24/launching-multiple-firefox-profiles-on-os-x-using-applescript/). My experience creating new profiles is still bad, but at least the experience of launching different build / profile combinations is as simple as clicking on an OS X .app bundle.

### Developer user stories:

* as a web developer, if I start Firefox Aurora or Nightly builds and already have a copy of Firefox running, I would like to be offered to use a different profile, or create a new one.
* when I create an alternate profile I should be able to select it as the default profile for this build of Firefox
* as a web developer I would like to create a development-specific profile from the Tools / Web Developer menu
* when creating a new developer profile, I would like to have common developer-centric preferences and options enabled for me.
* when I first start my developer profile, I would find it helpful to be shown documentation talking about the developer-specific features available to me.
* when I first start my developer profile, I would appreciate pointers to additional docs, resources, extensions and tool integrations that work with Firefox.

### Tester user stories

I don't have a clear idea what qa-specific tweaks we would want aside from providing easy access to resources like about:memory or about:crashes, and possibly various diagnostic add-ons. The point is, the tester use case is different from the developer use case, and there should be a first-run experience that handles that. It could be as simple as setting the homepage to a site with relevant QA information.


