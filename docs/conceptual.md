# Conceptual Level OMDL #

During the conceptual design, the workspace will be defined. A bunch of metadata will  describe the workspace semantically. The conceptual design features an abstract notation of the user goals of a workspace. Its aim is the support of unskilled users. A developer is able to talk with them and both sides act on the same foundation. This approach is designed to provide transparency and avoid misunderstandings between users and developers. An example is a meeting of a company where a project manager, who acts for 
and on behalf of developers, talks with the management. The company management normally does not have a deep understanding and interest in technical details. They just want to discuss the overall purpose of such a workspace and get an overview of the embedded 
features and its goals, that is, they want to understand the concept. 

## Structure

    <?xml version="1.0"?>
    <workspace xmlns="http://www.ict-omelette.eu/vocab/mdl/"
               xmlns:dc="http://purl.org/dc/elements/1.1/">
      <goal>{GOAL^^xsd:string}</goal>
      <status date="{DATETIME^^xsd:dateTime}">{STATUS^^xsd:string}</status>
      
      <dc:identifier>{HTTP-URI-TO-WORKSPACE}</dc:identifier>
      <dc:title>{NAME^^xsd:string}</dc:title>
      <dc:description>{DESCRIPTION^^xsd:string}</dc:description>
      <dc:creator>{HTTP-URI-TO-USER-PROFILE}</dc:creator>     
      <dc:date>{DATETIME^^xsd:dateTime}</dc:date>  
      <dc:source>{HTTP-URI-TO-DOCUMENT-OF-THE-PREVIOUS-DESIGN-PHASE}</dc:source>
    </workspace>
    
## Example

    <?xml version="1.0"?>
    <workspace xmlns="http://www.ict-omelette.eu/vocab/mdl/"
               xmlns:dc="http://purl.org/dc/elements/1.1/">
      <goal>Show plumpers in Berlin on a map and let me call them.</goal>
      <status date="2012-07-01T13:57+02:00">conceptual design done</status>
      
      <dc:identifier>http://repo.omdl.org/mashups/alice/CallFromMap</dc:identifier>
      <dc:title>Call Service from Map</dc:title>
      <dc:description>
        Mashup to show user-defined services for a user-defined location on a map.
        Selecting a map entry displays information about the service including
        a facility to directly call the service.
      </dc:description>
      <dc:creator>http://repo.omdl.org/people/alice.rdf#me</dc:creator>
      <dc:date>2012-07-01T14:23+37:00</dc:date>
    </workspace>

## Elements and Attributes

### `<workspace>`

*Keywords:* `#conceptual` `#logical` `#physical` `#mandatory`

Workspace as the foundation for creating mashups from widgets.

### `<goal>`

*Keywords:* `#conceptual` `#logical` `#physical` `#mandatory`

Definition of the user goal in natural language following a defined syntax.

*Parent element:* `<workspace>`

### `<status>`

*Keywords:* `#conceptual` `#logical` `#physical` `#mandatory`

Current status of the workspace. 

*Attributes:*
`@date` the date of the current status, e.g. when the document was flagged as published, in progess or withdrawn.

*Parent element:* `<workspace>`

### `<dc:identifier>`

*Keywords:* `#conceptual` `#logical` `#physical` `#mandatory`

Unique identifier of the workspace represented by a URI linking to the workspace within a repository.

*Parent element:* `<workspace>`

### `<dc:title>`

*Keywords:* `#conceptual` `#logical` `#physical` `#mandatory`

Name of the workspace.

*Parent element:* `<workspace>`

### `<dc:description>`

*Keywords:* `#conceptual` `#logical` `#physical` `#mandatory`

Textual description of the workspace's functionality.

*Parent element:* `<workspace>`

### `<dc:creator>`

*Keywords:* `#conceptual` `#logical` `#physical` `#mandatory`

Author of the workspace respresented by a URI linking to the user of a certain user repository.

*Parent element:* `<workspace>`

### `<dc:date>`

*Keywords:* `#conceptual` `#logical` `#physical` `#mandatory`

Date of the last modification of the workspace.

*Parent element:* `<workspace>`
