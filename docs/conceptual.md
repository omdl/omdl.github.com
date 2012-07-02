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
      <dc:date>{DATETIME^^xsd:dateTime}</dc:date>  
    </workspace>
    
## Example

    <?xml version="1.0"?>
    <workspace xmlns="http://www.ict-omelette.eu/vocab/mdl/"
               xmlns:dc="http://purl.org/dc/elements/1.1/">
      <goal>Show plumpers in Berlin on a map and let me call them.</goal>
      <status date="2012-07-02T15:57+02:00">to be reviewed</status>
      <dc:identifier>http://repo.omdl.org/mashups/alice/3</dc:identifier>
      <dc:title>Call Service from Map</dc:title>
      <dc:description>
        Mashup to show user-defined services for a user-defined location on a map.
        Selecting a map entry displays information about the service including
        a facility to directly call the service.
      </dc:description>
      <dc:creator>http://repo.omdl.org/people/alice.rdf#me</dc:creator>
      <dc:date>2012-07-03T14:23+37:00</dc:date>     
    </workspace>

## Elements and Attributes

### `workspace`

Workspace as the foundation for creating mashups from widgets

### `goal`

Definition of the user goal in natural language following a defined syntax.

### `status`

Current status of the workspace. 

*Attribute:*

`@date` the date of the current status, e.g. when the document was flagged as published, in progess or withdrawn.

*Example:*

      <status date="2012-07-01T16:35+45:00">published</status>

### `dc:identifier`

Unique identifier of the workspace represented by a URI linking to the workspace within a repository.

### `dc:title`

Name of the workspace.

### `dc:description`

Textual description of the workspace's functionality.

### `dc:creator`

Author of the workspace respresented by a URI linking to the user of a certain user repository.

### `dc:date`

Date of the last modification of the workspace.
