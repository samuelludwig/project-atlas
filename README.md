# project-atlas
An attempt at producing a modular, extensible API for evaluating software
projects.

We can break down a given project into a number of components:
 - Files/Modules
 - Functions
 - Tests
 - Data/Variables
 - Types/Datastructures
 - Classes/Methods(?)

The system is composed of 4 distinct, decoupled parts:
 - The API: A JSON-based(?) representation of elements in the project, including
   call-graphs, and other metadata, accompanied by a full-text copy of the
   project itself.
 - The Client: Our frontend--a (most likely graphical) representation of the
   project, with the potential ability to provide different "views" of the
   project data. Consumes project data via the API's format. The most basic
   example of a client would simply echo out what it's sent from the server
   verbatim.
 - The Server: Collects/conforms project data (including emitter data if
   applicable) into a format that's consumable by the API, and will then send
   the data to the client via the API.
 - The Emitter: Embedded in a given editor (most likely a plugin), which will
   provide data to the server, which will enable "live-action" features. The
   emitter should 'emit' the cursors current location, along with the contents of
   unsaved buffers. Absence of an emitter should only result in the loss of the
   emitter-specific features (graceful degradation).

There will need be a different server implementation for each language.
