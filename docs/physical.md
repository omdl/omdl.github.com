# Physical Level OMDL #

While in the conceptual and logical design phase no real implementation was considered, the physical design is the only phase 
that is directly related to the runtime environment. The workspace is created for the runtime, i.e., all abstract definitions 
of the logical design will be replaced, e.g., with widgets, which are available in the widget repository. Furthermore, the 
rules of the physical design are transformed into executable ones; these are based on JavaScript objects which have to be 
evaluated a suitable platform during runtime. All specified elements have to be interprete by the runtime environment.
Additionally, styling information for the whole workspace and widget specific ones can be set. These are split into layout, 
theme and Cascading Style Sheets (CSS) statements. 

## Specification

    <?xml version="1.0"?>
    <workspace xmlns="http://www.ict-omelette.eu/vocab/mdl/"
               xmlns:dc="http://purl.org/dc/elements/1.1/">
      <goal>{GOAL^^xsd:string}</goal>
      <status date="{DATETIME^^xsd:dateTime}">{STATUS^^xsd:string}</status>
      <dc:identifier>{HTTP-URI-TO-THE-WORKSPACE}</dc:identifier>
      <dc:title>{NAME^^xsd:string}</dc:title>
      <dc:description>{DESCRIPTION^^xsd:string}</dc:description>
      <dc:creator>{HTTP-URI-TO-THE-USER-PROFILE}</dc:creator>     
      <dc:date>{DATETIME^^xsd:dateTime}</dc:date>  
      <dc:source>{HTTP-URI-TO-THE-CONCEPTUAL-DESIGN-DOCUMENT}</dc:source>
      <widget>
        <type></type>
      </widget>
      
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

### `<workspace>`

Workspace as the foundation for creating mashups from widgets

### `<goal>`

Definition of the user goal in natural language following a defined syntax.

### `<status>`

Current status of the workspace. 

*Attributes:*

`@date` the date of the current status, e.g. when the document was flagged as published, in progess or withdrawn.

### `<dc:identifier>`

Unique identifier of the workspace represented by a URI linking to the workspace within a repository.

### `<dc:title>`

Name of the workspace.

### `<dc:description>`

Textual description of the workspace's functionality.

### `<dc:creator>`

Author of the workspace respresented by a URI linking to the user of a certain user repository.

### `<dc:date>`

Date of the last modification of the workspace.
