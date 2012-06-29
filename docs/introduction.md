# Introduction #


# <workspace> #

The `<workspace>` element is the root element of the whole workspace, which contains all further elements. 

A `workspace` contains `<widget>` elements for each widget in the workspace, as well as any of the following metadata elements:

## <title> ##

The name of the Workspace, such as the page title.

## <identifier> ##

Globally unique identifier of the workspace. This is, for instance, a HTTP-URI of the workspace within a repository.

## <description> ##

A detailed description of the Workspace functionality.

## <creator> ##

The author of the Workspace.

## <date> ##

The date of the last modification of the Workspace.

## <status> ##

The current status of the workspace.

## <layout> ##

The layout defines the structure of the workspace, like 2-columns or grid. For example "THREE COLUMNS", "TWO COLUMNS WIDE NARROW".

## <theme> ##

The name of the them used to style the workspace.

# <widget> #

Widget definition of one widget in the workspace. The Logical Design uses abstract definitions and the Physical Design defines a specific widget for the workspace.

Attributes:

'@id' The unique id of the widget is represented by the id attribute. Its scope is limited to the coresponding workspace.
