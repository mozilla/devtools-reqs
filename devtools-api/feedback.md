###Fitzgen

I am a JS framework developer and I want to customize the output of my framework's objects in the webconsole/variables view/*anywhere* they are displayed.

Maybe my model instances have foo and bar properties. You access them through .get("foo") and set through .set("foo", "value") so that listeners can fire (with backwards compat), but I should be able to display the item as though foo and bar were normal properties. I should also be able to hide any framework private properties from being displayed. I should be able to display anything I want for the object regardless of whether the actual object has properties or not.

Maybe I have an RGB color class that makes objects of the form { red: Number, green: Number, blue: Number }. I should be able to have my object outputted as a box filled in with the corresponding color. 

###Honza

Misc points:
- The framework should support tool pane integration, e.g. if the user clicks on an element anywhere the HTML pane is displayed (selecting the clicked element). if the user clicks a function -> the Debugger pane is displayed (highlighting the function), etc.
Extensions should be able to introduce new panes/object types for this.

I think there are following basic areas dev folks want to extend
almost in every extension:
- UI (e.g. new UI widgets + handling user action such as button click )
- Data model (e.g. collecting or computing new meta data about the page + using existing data)
- Back-end services (e.g. new profiler based on jsd2 + a new actor in case of remoting)

Domplate allows extension folks to do the following:
- Modify existing templates
- Inherit from existing templates (in Domplate a template is JS object)
- Create new templates and register them for an object type
  (e.g. string, number, table element, dom attribute list, storage, etc.) in a registry.
- Associate user actions with a template (clicks, etc.) to impl interaction.
One thing that Firebug extensions (or Firebug itself) have done
is creating new UI templates for specific object types.

Btw. I don’t see story for: “I want to create a new command line command”, but perhaps it belong to some other section.

I don’t see story for:
- I want to export collected data from the Network panel (using HAR)
- I want to add a new tab for a request (displayed alongside Headers, Cookies, etc.)

Extensions devs often want to visualize response bodies and posted bodies (e.g. using an expandable tree for JSON/XML, or visualize fonts, SVG, or proprietary formats/mime-types)