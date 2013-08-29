# Browser Resource Tool

*Firefox Developer Tools Team*

## User stories

### General

* As a user I should be able to access the 5 common supported types of storage are supported and easily accessible ( IndexedDB, Localstorage, Session, Cookies, Appcache ) for the current site.| 
* I should be able to view the sites data via an appropriate ‘viewer’ for that type of data.| All | P1
* If there is more than one source uri of data on a page, data sources must be clearly labeled with which uri they came from.
* I should be able to easily clear the currently stored data.

### Search

* I should be able to search for a value in either keys or data and reduce the number of results visible to only those matching my search terms.
* While I search, I should see a visible indication of matches on the current search term in the visible data.

### Cookies

* Cookies should be parsed into an array of key-value pairs and browse-able.
* I should be able to delete individual keys - this deletes both the key and the value.
* I should be able to edit either the key or the value.| All | P1


### Localstorage

* I should be able to browse all key-value pairs
* If I store JSON as a value, I should be able to view the value as a browse-able object instead of just JSON text.

### IndexedDB

* If I’ve stored media files in the database such as images or audio, I should be able to either preview the media or at least see a visual indication of the media type.
* I should be able to run a JS snippet against the IndexedDB database and see results.

### Appcache

* I should be able to view the contents of the appcache
* I should be able to easily clear the appcache
* I should be able to easily re-generate the appcache
