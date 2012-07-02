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
      
      <dc:identifier>{HTTP-URI-TO-WORKSPACE}</dc:identifier>
      <dc:title>{NAME^^xsd:string}</dc:title>
      <dc:description>{DESCRIPTION^^xsd:string}</dc:description>
      <dc:creator>{HTTP-URI-TO-USER-PROFILE}</dc:creator>     
      <dc:date>{DATETIME^^xsd:dateTime}</dc:date>  
      <dc:source>{HTTP-URI-TO-CONCEPTUAL-DESIGN-DOCUMENT}</dc:source>

      <widget+ id="{UNIQUE-WIDGET-ID-IN-WORKSPACE}">
        <type>{MAP|VOICE|VIDEO|LIST|SMS|CHAT|...}</type>
        <source>{HTTP-URI-TO-WIDGET-REPOSITORY}</source>
        <position>{TOP|MIDDLE|BOTTOM}{LEFT|CENTER|RIGHT}</position>
      </widget>

      <qos?>
         <bandwidth?>{MINIMAL-BITRATE^^xsd:integer}</bandwith>
         <latency? mandatory="{TRUE|FALSE}">{MAXIMAL-MILLISECONDS^^xsd:integer}</latency>
         <gps? mandatory="{TRUE|FALSE}" accuracy="{MAX-RADIUS-IN-METERS^^xsd:integer}"/>
      </qos>

      <ruleset* connective="{AND|OR}">
        <rule+ language="{LANGUAGE^^xsd:string}">{SOURCE-CODE^^xsd:string}</rule>
      </ruleset>

      <layout>{X-COLUMNS|X-ROWS|GRID|FLOW}</layout>
      <theme?>{LABEL^^xsd:string}</theme>
      <stylesheet?>{HTTP-URI-TO-CSS-FILE}</stylesheet>

      <phaseout>
        <date>{DEADLINE^^xsd:dateTime}</date>
        <holdback? unit="{HOUR|DAY|MONTH|YEAR}">{VALUE^^xsd:integer}</holdback>
        <location? type="{TYPE-OF-DATA-REPOSITOY^^xsd:integer}">{HTTP-URI-TO-DATA-DOWNLOAD}</location>
      </phaseout>
    </workspace>
    
## Example

    <?xml version="1.0"?>
    <workspace xmlns="http://www.ict-omelette.eu/vocab/mdl/"
               xmlns:dc="http://purl.org/dc/elements/1.1/">
      <goal>Show plumpers in Berlin on a map and let me call them.</goal>
      <status date="2012-07-02T15:57+02:00">physical design done</status>
      
      <dc:identifier>http://repo.omdl.org/mashups/alice/CallFromMap</dc:identifier>
      <dc:title>Call Service from Map</dc:title>
      <dc:description>
        Mashup to show user-defined services for a user-defined location on a map.
        Selecting a map entry displays information about the service including
        a facility to directly call the service.
      </dc:description>
      <dc:creator>http://repo.omdl.org/people/alice.rdf#me</dc:creator>
      <dc:date>2012-07-03T14:23+37:00</dc:date>
      
      <widget id="http://repo.omdl.org/mashups/alice/CallFromMap/1">
        <type>MAP</type>
        <source>http://repo.omdl.org/widgets/map/MyFancyMap</source>
        <position>TOPLEFT</position>
      </widget>
      <widget id="http://repo.omdl.org/mashups/alice/CallFromMap/2">
        <type>LIST</type>
        <source>http://repo.omdl.org/widgets/list/ResultInfo</source>
        <position>TOPRIGHT</position>
      </widget>
      <widget id="http://repo.omdl.org/mashups/alice/CallFromMap/3">
        <type>VOICE</type>
        <source>http://repo.omdl.org/widgets/list/CallItForMe</source>
        <position>BOTTOMRIGHT</position>
      </widget>

      <qos>
         <bandwidth>128</bandwith>
         <latency mandatory="true">200</latency>
         <gps mandatory="true" accuracy="100"/>
      </qos>

      <ruleset connective="and">
        <rule language="javascript">
           {context.Date}.getUTCHours() >= 4 || {context.Date}.getUTCHours() <= 2
        </rule>
        <rule language="javascript">{context.Client}.location == 'DE'/rule>
      </ruleset>

      <layout>grid</layout>
      <stylesheet>http://repo.omdl.org/mashups/alice/3/_data/special.css</stylesheet>

      <phaseout>
        <date>2015-01-01T01:00+00:00</date>
        <holdback unit="month">1</holdback>
        <location type="archive">http://repo.omdl.org/mashups/oldschool/location>
      </phaseout>
    </workspace>

## Elements and Attributes

### `<workspace>`

Workspace as the foundation for creating mashups from widgets

*Supported in Phase:* Conceptual, Logical, Physical

### `<goal>`

Definition of the user goal in natural language following a defined syntax.

*Supported in Phase:* Conceptual, Logical, Physical

### `<status>`

Current status of the workspace. 

*Attributes:*

`@date` the date of the current status, e.g. when the document was flagged as published, in progess or withdrawn.

*Supported in Phase:* Conceptual, Logical, Physical

### `<dc:identifier>`

Unique identifier of the workspace represented by a URI linking to the workspace within a repository.

*Supported in Phase:* Conceptual, Logical, Physical

### `<dc:title>`

Name of the workspace.

*Supported in Phase:* Conceptual, Logical, Physical

### `<dc:description>`

Textual description of the workspace's functionality.

*Supported in Phase:* Conceptual, Logical, Physical

### `<dc:creator>`

Author of the workspace respresented by a URI linking to the user of a certain user repository.

*Supported in Phase:* Conceptual, Logical, Physical

### `<dc:date>`

Date of the last modification of the workspace.

*Supported in Phase:* Conceptual, Logical, Physical
