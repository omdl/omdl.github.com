# Conceptual Level OMDL #

OMDL can be used to describe a mashup in conceptual terms without reference to specific widgets and layouts. 

## Introduction

## Specification

    <?xml version="1.0"?>
    <workspace xmlns="http://www.ict-omelette.eu/vocab/mdl/"
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
    <workspace xmlns="http://www.ict-omelette.eu/vocab/mdl/"
               xmlns:dc="http://purl.org/dc/elements/1.1/">
      <goal>Show plumbers in Berlin on a map and let me call them.</goal>
      <status date="2012-07-02T15:57+02:00">to be reviewed</status>
      <dc:identifier>{REPO-URI}</dc:identifier>
      <dc:title>{NAME}</dc:title>
      <dc:description>{DESCRIPTION}</dc:description>
      <dc:creator>{USER-URI}</dc:creator>
      <dc:date>2012-07-03T14:23+37:00</dc:date>     
    </workspace>

## Elements and Attributes

### workspace

The workspace is the foundation for creating mashups from widgets

### goal

Definition of the user goal in natural language following a defined syntax.

### status

Current status of the workspace description.

### dc:identifier

Globally unique identifier of the workspace represented by a URI linking to the workspace within a repository.

### dc:title

Name of the workspace.

### dc:description

Textual description of the workspace's functionality.

### dc:creator

Author of the workspace respresented by a URI linking to the user of a certain user repository.

### dc:date

Date of the last modification of the workspace.
