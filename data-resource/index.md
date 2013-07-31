# Browser Resource Tool

*Firefox Developer Tools Team*

The purpose of these requirements is to solve our lack of any tooling to examine the various data sources web applications use, including: Cookies, Localstorage, IndexedDB, Session and Appcache. This grouping (as well as the non-standard WebSQL) are shown here as implemented in Chrome’s ‘resources’ tool:

As the web gets increasingly mobile and offline-oriented and we explore the technologies available to help enable mobile-first and offline-aware apps, our ability to cache data in the browser and sync it opportunistically with servers becomes critical. Worse, existing standard APIs such as localstorage and appcache frustrate users who find them either difficult to use, slow, or both.
It’s about the data, stupid

Of course, the standards process is long and fraught with danger; what we can do in the meantime is provide great tools so that at least developers can see the data.


## Prior Art

### Firebug

Firebug only really captures one aspect of this story with built-in cookie parsing and inspection. The “FireStorage Plus!“ extension adds rudimentary localstorage and session capabilities, but IndexedDB and Appcache are not supported AFAICT.

### Chrome
Chrome has wide support for all of these standards as well as the on-standard WebSQL storage spec as shown above:

1. Frames ( all frames and more importantly all iframes in a page )
1. WebSQL ( non-standard, not supported in Gecko )
1. IndexedDB
1. Local Storage
1. Session Storage
1. Cookies
1. AppCache

For the most part these are very basic tools used to view data state.

## Web Standards / Polyfill status

1. CanIuse:
  1. http://caniuse.com/offline-apps
  1. http://caniuse.com/indexeddb
  1. http://caniuse.com/sql-storage
1. Polyfills
  1. TBD

## User / Application Types

Defining user types is a little daunting for this, as there is a very magnetic central type called an ‘app developer’, but just speaking about app developers oversimplifies the various use cases developers would use these technologies for. I think it is a bit more interesting to think about different styles of apps and the use cases that spring forth from them:

###Offline / Packaged Apps

Apps that need to store all state data on device and are fully functional without a network connection. S sub-set includes apps ( such as a calendar or possibly a chess game ) that are meant to sync data to a back-end server when  a network connection is available.

###Single Page Apps

Single page apps may make extensive use of locally cached data to improve interactivity and performance.

###Heavy Media Use

The Gecko platform currently lacks any general-purpose file system access ( such as the privileged, non-standard ‘Device Storage API’ ) so there are techniques being used currently by developers to mimic file-like behaviour using IndexedDB. Use cases include local storage of images, audio sprites and similar, particularly for games.

###Server-side Apps

This is “Web Classic”, the classic pattern is that data is all stored in databases on the server, and sessions are kept via cookies or some similar form of light-weight tag association ( HTTP headers, session ids embedded in requests, etc )

## Requirements

### General

ID | Name   | Story    | User  | Priority
--- | --- | :--- | --- | ---
drt-01| something | As a user I should be able to access the 5 common supported types of storage are supported and easily accessible ( IndexedDB, Localstorage, Session, Cookies, Appcache ) for the current site.| All | P1
drt-02| something | I should be able to view the sites data via an appropriate ‘viewer’ for that type of data.| All | P1
drt-03| something | If there is more than one source uri of data on a page, data sources must be clearly labelled with which uri they came from.| All | P1
drt-04| something | I should be able to easily clear the currently stored data.| All | P1

### Search

|ID | Name   | Story    | User  | Priority    | 
--- | --- | :--- | --- | ---
drt-04| something | I should be able to search for a value in either keys or data and reduce the number of results visible to only those matching my search terms.| All | P1
drt-04| something | While I search, I should see a visible indication of matches on the current search term in the visible data.| All | P1


### Cookies

|ID | Name   | Story    | User  | Priority    | 
--- | --- | :--- | --- | ---
drt-04| something | Cookies should be parsed into an array of key-value pairs and browse-able.| All | P1
drt-04| something | I should be able to delete individual keys - this deletes both the key and the value.| All | P1
drt-04| something | I should be able to edit either the key or the value.| All | P1


### Localstorage

|ID | Name   | Story    | User  | Priority    | 
--- | --- | :--- | --- | ---
drt-04| something | I should be able to browse all key-value pairs| All | P1
drt-04| something | If I store JSON as a value, I should be able to view the value as a browse-able object instead of just JSON text.| All | P1


### IndexedDB

|ID | Name   | Story    | User  | Priority    | 
--- | --- | :--- | --- | ---
drt-04| something | If I’ve stored media files in the database such as images or audio, I should be able to either preview the media or at least see a visual indication of the media type.| All | P1
drt-04| something | I should be able to run a JS snippet against the IndexedDB database and see results.| All | P1


### Appcache

|ID | Name   | Story    | User  | Priority    | 
--- | --- | :--- | --- | ---
drt-04| something | I should be able to view the contents of the appcache| All | P1
drt-04| something | I should be able to easily clear the appcache| All | P1
drt-04| something | I should be able to easily re-generate the appcache| All | P1
