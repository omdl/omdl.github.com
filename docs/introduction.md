# Introduction #

OMDL uses XML documents to represent mashups, including the workspace, layouts, and included widgets, at different stages of the design process.

At the _conceptual_ level, OMDL can be used to describe the overall purpose of a mashup, for example as a set of user requirements.

At the _logical_ level, OMDL can be used to describe a general mashup structure, including the type of widgets to be used.

At the _physical_ level, OMDL is used to exchange the implementation of a mashup, including specific widgets, layouts and theming.

## Namespace

All OMDL documents use the namespace http://omdl.org

## General structure

An OMDL document is an XML document, consisting of a `<workspace>` root element, metadata elements, and any number of `<widget>` elements.

The specific elements used differs for conceptual, logical and physical mashup documents.
