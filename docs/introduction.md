# Introduction #

OMDL uses XML documents to represent mashups, including the workspace, layouts, and included widgets. 

## Namespace

OMDL documents use the namespace http://omdl.org

## the `<workspace>` element ##

The `<workspace>` element is the root element of the whole workspace, which contains all further elements. 

A `<workspace>` contains `<widget>` elements for each widget in the workspace, as well as any of the following metadata elements:

* `<title>` The name of the Workspace, such as the page title, as a String.
* `<identifier>` Globally unique identifier of the workspace. This is, for instance, a HTTP-URI of the workspace within a repository.
* `<description>` A detailed description of the Workspace functionality, as a plain text String.
* `<creator>` The author of the Workspace, as a String.
* `<date>` The date of the last modification of the Workspace, in W3C Date-Time Format [W3CDTF].
* `<theme>` The name of the them used to style the workspace, as a String.
* `<source>` A HTTP-URI linking to another OMDL document this one is derived from; for example to link an OMDL description at physical level to a logical-level design document.

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
    
    
## the `<layout>` element ##

The layout defines the structure of the workspace.

The format of this element is a string containing the number of columns, and then any column layout hints in column order.

For example "TWO COLUMNS WIDE NARROW" would indicate a layout with two columns, with the left column wide and the right column narrow.

However, applications may ignore the layout, or apply the column numbers but not column layout hints.

## the `<status>` element ##

The current status of the workspace. It contains the following attribute:

`@date` the date of the current status, for example, when the document was published or withdrawn.

Example:

	  <status date="Thu Aug 04 2011 17:57:26 GMT+0200(CEST)">published</status>

## the `<widget>` element ##

Widget definition of one widget in the workspace. The Logical Design uses abstract definitions and the Physical Design defines a specific widget for the workspace.

Attributes:

`@id` The unique id of the widget is represented by the id attribute. Its scope is limited to the coresponding workspace.
