# Introduction #

OMDL uses XML documents to represent mashups, including the workspace, layouts, and included widgets. 

## the `<workspace>` element ##

The `<workspace>` element is the root element of the whole workspace, which contains all further elements. 

A `<workspace>` contains `<widget>` elements for each widget in the workspace, as well as any of the following metadata elements:

* `<title>` The name of the Workspace, such as the page title.
* `<identifier>` Globally unique identifier of the workspace. This is, for instance, a HTTP-URI of the workspace within a repository.
* `<description>` A detailed description of the Workspace functionality.
* `<creator>` The author of the Workspace.
* `<date>` The date of the last modification of the Workspace.
* `<layout>` The layout defines the structure of the workspace, like 2-columns or grid. For example "THREE COLUMNS", "TWO COLUMNS WIDE NARROW".
* `<theme>` The name of the them used to style the workspace.
* `<source>` A link to another OMDL document this one is derived from; for example to link an OMDL description at physical level to a logical-level design document.

Example:

    <workspace>
	  <identifier>12</identifier>
	  <title>Project 64: WorkSpace</title>
	  <description>Our project workspace</description>
	  <creator>Alice</creator>
	  <date>2011-08-04T17:57+02:00</date>
	  <source>http://repo.omdl.org/designs/alice/3</source>
	  <status date="Thu Aug 04 2011 17:57:26 GMT+0200(CEST)">published</status>
    </workspace>
    
## the `<status>` element ##

The current status of the workspace. It contains the following attribute:

`@date` the date of the current status, for example, when the document was published or withdrawn.

Example:

	  <status date="Thu Aug 04 2011 17:57:26 GMT+0200(CEST)">published</status>

## the `<widget>` element ##

Widget definition of one widget in the workspace. The Logical Design uses abstract definitions and the Physical Design defines a specific widget for the workspace.

Attributes:

`@id` The unique id of the widget is represented by the id attribute. Its scope is limited to the coresponding workspace.
