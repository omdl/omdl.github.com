# Conceptual Level OMDL #

OMDL can be used to describe a mashup in conceptual terms without reference to specific widgets and layouts. 

## Introduction

## Specification

    <?xml version="1.0"?>
    <workspace xmlns="http://omdl.org"
               xmlns:dc="http://purl.org/dc/elements/1.1/">
      <goal>{GOAL^^xsd:string}</goal>
      <status date="{DATETIME^^xsd:dateTime}">{STATUS^^xsd:string}</status>
      <dc:identifier>{REPO-URI}</dc:identifier>
      <dc:title>{NAME^^xsd:string}</dc:title>
      <dc:description>{DESCRIPTION^^xsd:string}</dc:description>
      <dc:creator>{USER-URI}</dc:creator>     
      <dc:date>2011-08-04T15:57+02:00</dc:date>  
    </workspace>
    
## Example

    <?xml version="1.0"?>
    <workspace xmlns="http://omdl.org"
               xmlns:dc="http://purl.org/dc/elements/1.1/">
      <goal>Show plumbers in Berlin on a map and let me call them.</goal>
      <status date="2012-07-02T15:57+02:00">to be reviewed</status>
      <dc:identifier>{REPO-URI}</dc:identifier>
      <dc:title>{NAME}</dc:title>
      <dc:description>{DESCRIPTION}</dc:description>
      <dc:creator>{USER-URI}</dc:creator>
      <dc:date>2012-07-03T14:23+37:00</dc:date>     
    </workspace>

## Elements and Attributes used at conceptual level

### the `workspace` element

Any elements can be used for the workspace - see [introduction](documentation.html)

### the `widget` element

At conceptual level, the following elements and attributes can be used for widgets:

TODO list widget child elements here
