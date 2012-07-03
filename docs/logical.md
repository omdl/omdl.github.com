# Logical Level OMDL #

In the logical design phase, the user goals of the conceptual design will be evaluated and replaced by abstract widget definitions. It is closely related to the conceptual design but both phases are independent of each other. The logical design document is an 
intermediate step between an abstract description of the workspace and a  composed one with widgets and additional settings. It includes abstract definitions of widgets and rules that have to match during runtime. Legal constraints are taken into account as well as several other restrictions, like a time-based or region-based access policy. This phase leads to a quick overview which widget types apply and allows easily to change it. The user does not need a deep understanding of the technical details or programming skills. Its aim is to create an initial set-up of used widget types to achieve the desired functionality. The logical design 
could be an intermediate format that is not displayed to the user.

## Specification

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

      <widget+">
        <type>{MAP|VOICE|VIDEO|LIST|SMS|CHAT|...}</type>
      </widget>

      <ruleset* connective="{AND|OR}">
        <rule+ language="{LANGUAGE^^xsd:string}">{TEXT^^xsd:string}</rule>
      </ruleset>
    </workspace>
    
## Example

    <?xml version="1.0"?>
    <workspace xmlns="http://www.ict-omelette.eu/vocab/mdl/"
               xmlns:dc="http://purl.org/dc/elements/1.1/">
      <goal>Show plumpers in Berlin on a map and let me call them.</goal>
      <status date="2012-07-02T13:57+02:00">logical design done</status>
      
      <dc:identifier>http://repo.omdl.org/mashups/alice/CallFromMap</dc:identifier>
      <dc:title>Call Service from Map</dc:title>
      <dc:description>
        Mashup to show user-defined services for a user-defined location on a map.
        Selecting a map entry displays information about the service including
        a facility to directly call the service.
      </dc:description>
      <dc:creator>http://repo.omdl.org/people/alice.rdf#me</dc:creator>
      <dc:date>2012-07-02T14:23+37:00</dc:date>
      
      <widget>
        <type>MAP</type>
      </widget>
      <widget>
        <type>LIST</type>
      </widget>
      <widget>
        <type>VOICE</type>
      </widget>

      <ruleset connective="and">
        <rule language="text">The mashup is only allowed to be used within 4 am and 2 am CET</rule>
        <rule language="text">Location has to be Germany</rule>
      </ruleset>
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

### `<widget>`

*Keywords:* `#logical` `#physical` `#mandatory`

Definition of a widget in the workspace. The `<widget>` element can occur once or several times.

*Parent element:* `<workspace>`

### `<type>`

*Keywords:* `#logical` `#physical` `#mandatory`

Type of the widget. Valid content values are: `map`, `voice`, `video`, `list`, `sms`, `chat` 

*Parent element:* `<widget>`
 
### `<ruleset>`

*Keywords:* `#logical` `#physical` `#optional`

Optional frame element containing rules or combination of rules associated to the mashup or contained widgets. 
The `<ruleset>` element is optinal, can be cascaded, i.e. the `<ruleset>` is allowed to have a `<ruleset>` child element, and can occur several times the 2. level (child level).

*Attributes:*
`@connective` Sets how the rules within the ruleset have to be evaluated, i.e. have all rules within a ruleset be fulfilled ('and' combination) or just one ('or' combination). Valid values are 'and' or 'or'.

*Parent element:* `<workspace>`

### `<rule>`

*Keywords:* `#logical` `#physical`

Rule that has to be fulfilled in order to run the mashup. The rule have to be written in natural language during the logical design and in a programming language during the physical design. At least one `rule` element has to be present within a `ruleset`.

*Attributes:*
`@language` Language the rule is written in. Should be 'text' in the logical phase and 'javascript' in the physical phase.

*Parent element:* `<ruleset>`
