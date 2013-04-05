# Introduction #

OMDL uses XML documents to represent mashups, including the workspace, layouts, and included apps, at different stages of the design process.

At the _conceptual_ level, OMDL can be used to describe the overall purpose of a mashup, for example as a set of user requirements.

At the _logical_ level, OMDL can be used to describe a general mashup structure, including the type of apps to be used.

At the _physical_ level, OMDL is used to exchange the implementation of a mashup, including specific apps, layouts and theming.

## Namespace

All OMDL documents use the namespace http://omdl.org

## General Structure

The description, the syntax and structure definition as well as an example of the OMDL at each design level - conceptual, logical, physical - are provided in this section.

### Conceptual level OMDL

During the conceptual design, the workspace will be defined. A bunch of metadata will  describe the workspace semantically. The conceptual design features an abstract notation of the user goals of a workspace. Its aim is the support of unskilled users. A developer is able to talk with them and both sides act on the same foundation. This approach is designed to provide transparency and avoid misunderstandings between users and developers. An example is a meeting of a company where a project manager, who acts for 
and on behalf of developers, talks with the management. The company management normally does not have a deep understanding and interest in technical details. They just want to discuss the overall purpose of such a workspace and get an overview of the embedded 
features and its goals, that is, they want to understand the concept. 

#### Structure of OMDL at the Conceptual Level

    <?xml version="1.0"?>
    <workspace xmlns="http://omdl.org">
      <goal>{GOAL^^xsd:string}</goal>
      <status date="{DATETIME^^xsd:dateTime}">{STATUS^^xsd:string}</status>
      
      <identifier>{HTTP-URI-TO-WORKSPACE}</identifier>
      <title>{NAME^^xsd:string}</title>
      <description>{DESCRIPTION^^xsd:string}</description>
      <creator>{HTTP-URI-TO-USER-PROFILE}</creator>     
      <date>{DATETIME^^xsd:dateTime}</date>  
      <source>{HTTP-URI-TO-DOCUMENT-OF-THE-PREVIOUS-DESIGN-PHASE}</source>
    </workspace>
    
#### Example of OMDL at the Conceptual Level

    <?xml version="1.0"?>
    <workspace xmlns="http://omdl.org/">
      <goal>Show plumbers in Berlin on a map and let me call them.</goal>
      <status date="2012-07-01T13:57+02:00">conceptual design done</status>
      
      <identifier>http://repo.omdl.org/mashups/alice/CallFromMap</identifier>
      <title>Call Service from Map</title>
      <description>
        Mashup to show user-defined services for a user-defined location on a map.
        Selecting a map entry displays information about the service including
        a facility to directly call the service.
      </description>
      <creator>http://repo.omdl.org/people/alice.rdf#me</creator>
      <date>2012-07-01T14:23+37:00</date>
    </workspace>

	
### Logical level OMDL
	
In the logical design phase, the user goals of the conceptual design will be evaluated and replaced by abstract app definitions. It is closely related to the conceptual design but both phases are independent of each other. The logical design document is an 
intermediate step between an abstract description of the workspace and a  composed one with apps and additional settings. It includes abstract definitions of apps and rules that have to match during runtime. Legal constraints are taken into account as well as several other restrictions, like a time-based or region-based access policy. This phase leads to a quick overview which app types apply and allows easily to change it. The user does not need a deep understanding of the technical details or programming skills. Its aim is to create an initial set-up of used app types to achieve the desired functionality. The logical design 
could be an intermediate format that is not displayed to the user.

#### Structure of OMDL at the Logical Level

    <?xml version="1.0"?>
    <workspace xmlns="http://omdl.org/">
      <goal>{GOAL^^xsd:string}</goal>
      <status date="{DATETIME^^xsd:dateTime}">{STATUS^^xsd:string}</status>
      
      <identifier>{HTTP-URI-TO-WORKSPACE}</identifier>
      <title>{NAME^^xsd:string}</title>
      <description>{DESCRIPTION^^xsd:string}</description>
      <creator>{HTTP-URI-TO-USER-PROFILE}</creator>     
      <date>{DATETIME^^xsd:dateTime}</date>  
      <source>{HTTP-URI-TO-DOCUMENT-OF-THE-PREVIOUS-DESIGN-PHASE}</source>

      <app+">
        <type>{MAP|VOICE|VIDEO|LIST|SMS|CHAT|...}</type>
      </app>

      <ruleset* connective="{AND|OR}">
        <rule+ language="{LANGUAGE^^xsd:string}">{TEXT^^xsd:string}</rule>
      </ruleset>
    </workspace>
    
#### Example of OMDL at the Logical Level

    <?xml version="1.0"?>
    <workspace xmlns="http://omdl.org/">
      <goal>Show plumbers in Berlin on a map and let me call them.</goal>
      <status date="2012-07-02T13:57+02:00">logical design done</status>
      
      <identifier>http://repo.omdl.org/mashups/alice/CallFromMap</identifier>
      <title>Call Service from Map</title>
      <description>
        Mashup to show user-defined services for a user-defined location on a map.
        Selecting a map entry displays information about the service including
        a facility to directly call the service.
      </description>
      <creator>http://repo.omdl.org/people/alice.rdf#me</creator>
      <date>2012-07-02T14:23+37:00</date>
      
      <app>
        <type>MAP</type>
      </app>
      <app>
        <type>LIST</type>
      </app>
      <app>
        <type>VOICE</type>
      </app>

      <ruleset connective="and">
        <rule language="text">The mashup is only allowed to be used within 4 am and 2 am CET</rule>
        <rule language="text">Location has to be Germany</rule>
      </ruleset>
    </workspace>

	
### Physical level OMDL
	
While in the conceptual and logical design phase no real implementation was considered, the physical design is the only phase 
that is directly related to the runtime environment. The workspace is created for the runtime, i.e., all abstract definitions 
of the logical design will be replaced, e.g., with apps, which are available in the app repository. Furthermore, the 
rules of the physical design are transformed into executable ones; these are based on JavaScript objects which have to be 
evaluated a suitable platform during runtime. All specified elements have to be interprete by the runtime environment.
Additionally, styling information for the whole workspace and app specific ones can be set. These are split into layout, 
theme and Cascading Style Sheets (CSS) statements. 

#### Structure of OMDL at the Physical Level

    <?xml version="1.0"?>
    <workspace xmlns="http://omdl.org/">
      <goal>{GOAL^^xsd:string}</goal>
      <status date="{DATETIME^^xsd:dateTime}">{STATUS^^xsd:string}</status>
      
      <identifier>{HTTP-URI-TO-WORKSPACE}</identifier>
      <title>{NAME^^xsd:string}</title>
      <description>{DESCRIPTION^^xsd:string}</description>
      <creator>{HTTP-URI-TO-USER-PROFILE}</creator>     
      <date>{DATETIME^^xsd:dateTime}</date>  
      <source>{HTTP-URI-TO-DOCUMENT-OF-THE-PREVIOUS-DESIGN-PHASE}</source>
      <thumbnail>{HTTP-URI-TO-THUMBMAIL-IMAGE}</thumbnail>
      <screenshot>{HTTP-URI-TO-SCREENSHOT-IMAGE}</screenshot>

      <app+ id="{UNIQUE-WIDGET-ID-IN-WORKSPACE}">
        <type>{MAP|VOICE|VIDEO|LIST|SMS|CHAT|...}</type>
        <identifier?>{IRI-OF-APP}</identifier>
        <link rel="source" href="{HTTP-URI-TO-WIDGET-REPOSITORY}" type="{WIDGET-CONTENT-TYPE}"/>
        <position>{TOP|MIDDLE|BOTTOM}{LEFT|CENTER|RIGHT}</position>
      </app>

      <capabilities?>
         <bandwidth?>{MINIMAL-BITRATE^^xsd:integer}</bandwith>
         <latency? mandatory="{TRUE|FALSE}">{MAXIMAL-MILLISECONDS^^xsd:integer}</latency>
         <gps? mandatory="{TRUE|FALSE}" accuracy="{MAX-RADIUS-IN-METERS^^xsd:integer}"/>
      </capabilities>

      <ruleset* connective="{AND|OR}">
        <rule+ language="{LANGUAGE^^xsd:string}">{SOURCE-CODE^^xsd:string}</rule>
      </ruleset>

      <layout>{X-COLUMNS|X-ROWS|GRID|FLOW}</layout>
      <theme?>{LABEL^^xsd:string}</theme>
      <stylesheet?>{HTTP-URI-TO-CSS-FILE}</stylesheet>

      <phaseout? date="{DEADLINE^^xsd:dateTime}">
        <holdback? unit="{HOUR|DAY|MONTH|YEAR}">{VALUE^^xsd:integer}</holdback>
        <location? type="{TYPE-OF-DATA-REPOSITOY^^xsd:integer}">{HTTP-URI-TO-DATA-DOWNLOAD}</location>
      </phaseout>
    </workspace>
    
#### Example of OMDL at the Physical Level

    <?xml version="1.0"?>
    <workspace xmlns="http://omdl.org/">
      <goal>Show plumbers in Berlin on a map and let me call them.</goal>
      <status date="2012-07-02T15:57+02:00">physical design done</status>
      
      <identifier>http://repo.omdl.org/mashups/alice/CallFromMap</identifier>
      <title>Call Service from Map</title>
      <description>
        Mashup to show user-defined services for a user-defined location on a map.
        Selecting a map entry displays information about the service including
        a facility to directly call the service.
      </description>
      <creator>http://repo.omdl.org/people/alice.rdf#me</creator>
      <date>2012-07-03T14:23+37:00</date>
      
      <app id="http://repo.omdl.org/mashups/alice/CallFromMap/1">
        <type>MAP</type>
        <link rel="source" href="http://repo.omdl.org/apps/map/MyFancyMap" type="application/widget"/>
        <position>TOPLEFT</position>
      </app>
      <app id="http://repo.omdl.org/mashups/alice/CallFromMap/2">
        <type>LIST</type>
        <link rel="source" href="http://repo.omdl.org/apps/list/ResultInfo" type="application/widget"/>
        <position>TOPRIGHT</position>
      </app>
      <app id="http://repo.omdl.org/mashups/alice/CallFromMap/3">
        <type>VOICE</type>
        <link rel="source" href="http://repo.omdl.org/apps/list/CallItForMe" type="application/widget"/>
        <position>BOTTOMRIGHT</position>
      </app>

      <capabilities>
         <bandwidth>128</bandwith>
         <latency mandatory="true">200</latency>
         <gps mandatory="true" accuracy="100"/>
      </capabilities>

      <ruleset connective="AND">
        <rule language="javascript">
           {context.Date}.getUTCHours() >= 4 || {context.Date}.getUTCHours() <= 2
        </rule>
        <rule language="javascript">{context.Client}.location == 'DE'</rule>
      </ruleset>

      <layout>GRID</layout>
      <stylesheet>http://repo.omdl.org/mashups/alice/3/_data/special.css</stylesheet>

      <phaseout>
        <date>2015-01-01T01:00+00:00</date>
        <holdback unit="month">1</holdback>
        <location type="archive">http://repo.omdl.org/mashups/oldschool/location>
      </phaseout>
    </workspace>

	
## Elements and Attributes


### `<workspace>`

*Keywords:* `#conceptual` `#logical` `#physical` `#mandatory`

Workspace as the foundation for creating mashups from apps.

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

### `<identifier>`

*Keywords:* `#conceptual` `#logical` `#physical` `#mandatory`

Unique identifier of the workspace represented by a URI linking to the workspace within a repository.

*Parent element:* `<workspace>`

### `<title>`

*Keywords:* `#conceptual` `#logical` `#physical` `#mandatory`

Name of the workspace.

*Parent element:* `<workspace>`

### `<description>`

*Keywords:* `#conceptual` `#logical` `#physical` `#mandatory`

Textual description of the workspace's functionality.

*Parent element:* `<workspace>`

### `<creator>`

*Keywords:* `#conceptual` `#logical` `#physical` `#mandatory`

Author of the workspace respresented by a URI linking to the user of a certain user repository.

*Parent element:* `<workspace>`

### `<date>`

*Keywords:* `#conceptual` `#logical` `#physical` `#mandatory`

Date of the last modification of the workspace.

*Parent element:* `<workspace>`

### `<source>`

*Keywords:* `#logical` `#physical` `#mandatory`

URI to the workspace description of the previous design phase, i.e. 
- if currently in logical design phase, then URI to document of conceptual phase
- if currently in physical design phase, then URI to document of logical phase

*Parent element:* `<workspace>`

### `<app>`

*Keywords:* `#logical` `#physical` `#mandatory`

Definition of an app in the workspace. The `<app>` element can occur once or several times.

 *Attributes:*
`@id` Unique identifier of the app is represented by a link to the app within the workspace environment. This attribute is allowed
to occur only in the physical phase.

*Parent element:* `<workspace>`

### `<type>`

*Keywords:* `#logical` `#physical` `#mandatory`

Type of the app. Valid content values are: `map`, `voice`, `video`, `list`, `sms`, `chat` 

*Parent element:* `<app>`

### `<link rel="source" href="http://somewhere.com/" type="application/widget">`

*Keywords:* `#physical` `#mandatory`

Link to the app source in a repository, e.g., the download location for a .wgt file or the location of an OpenSocial gadget.xml.

For W3C Widgets, the `type` attribute is `application/widget`; for OpenSocial it is `application/vnd-opensocial+xml`.

*Parent element:* `<app>`

### `<identifier>`

*Keywords:* `#physical` `#optional`

Optional identifier for the app, typically an IRI in the cae of W3C widgets. An identifier can be used to locate an app within an existing environment or download from a marketplace, rather than using a specific download link. This is optional as not all widgets have identifiers.

*Parent element:* `<app>`
 
### `<position>`

*Keywords:* `#physical` `#mandatory`

A textual placement hint for the app consisting of one or both of the following keywords:
- one of TOP, MIDDLE, BOTTOM for the vertical placement
- one of LEFT, CENTER, RIGHT for the horizontal placement

For example: "TOP LEFT", "BOTTOM", "MIDDLE CENTER"

*Parent element:* `<app>`
 
### `<capabilities>`

*Keywords:* `#physical` `#optional`

Optional frame element containing quality of service criteria, which have to be fulfilled in order to run the mashup.

*Parent element:* `<workspace>`
 
### `<bandwidth>`

*Keywords:* `#physical` `#optional`

Optional specification of the minimal bandwidth in kbit/s that have to be available. The bandwidth value is an integer.

*Parent element:* `<capabilities>`
 
### `<latency>`

*Keywords:* `#physical` `#optional`

Optional specification of the maximal allowed latency in milliseconds. The latency value is an integer.

*Attributes:*
`@mandatory` Defines if non-compliance has to be treated as critical. Is A valid value is either 'true' or 'false'.

*Parent element:* `<capabilities>`

### `<gps>`

*Keywords:* `#physical` `#optional`

Optional specification of the minimal valid accuracy as a radius in meters the subject is located in. The accuracy value is an integer.

*Attributes:*
`@mandatory` Defines if non-compliance has to be treated as critical. A valid value is either 'true' or 'false'.

*Parent element:* `<capabilities>`
 
### `<ruleset>`

*Keywords:* `#logical` `#physical` `#optional`

Optional frame element containing rules or combination of rules associated to the mashup or contained apps. 
The `<ruleset>` element is optional, can be cascaded, i.e. the `<ruleset>` is allowed to have a `<ruleset>` child element, and can occur several times the 2. level (child level).

*Attributes:*
`@connective` Sets how the rules within the ruleset have to be evaluated, i.e. have all rules within a ruleset be fulfilled ('AND' combination) or just one ('OR' combination). Valid values are 'AND' or 'OR'.

*Parent element:* `<workspace>`

### `<rule>`

*Keywords:* `#logical` `#physical`

Rule that has to be fulfilled in order to run the mashup. The rule have to be written in natural language during the logical design and in a programming language during the physical design. At least one `rule` element has to be present within a `ruleset`.

*Attributes:*
`@language` Language the rule is written in. Should be 'text' in the logical phase and 'javascript' in the physical phase.

*Parent element:* `<ruleset>`

### `<layout>`

*Keywords:* `#physical`

Layout defines the structure of the workspace. The format of this element is a string containing the number of columns, and any column layout hints in column order. Valid values are 'X-COLUMNS', 'X-ROWS', 'GRID', 'FLOW' or "TWO COLUMNS WIDE NARROW", which indicates a layout with two columns, with the left column wide and the right column narrow.

Applications may ignore the layout, or apply the column numbers but not column layout hints.

*Parent element:* `<workspace>`

### `<theme>`

*Keywords:* `#physical` `#optional`

Optional name of the theme used to style the workspace. Valid values are ___TODO___

*Parent element:* `<workspace>`

### `<stylesheet>`

*Keywords:* `#physical` `#optional`

Optional stylesheet to be used for the workspace. The stylesheet has to be referenced by a URI.

*Parent element:* `<workspace>`

### `<phaseout>`

*Keywords:* `#physical` `#optional`

Frame element containing data related to the phase out of the mashup.

*Attributes:*
`@date` the date of the phase out of the mashup. Value has to be of type datetime.

*Parent element:* `<workspace>`

### `<holdback>`

*Keywords:* `#physical` `#optional`

Optional duration the mashup has to be hold back from automatic removal. The value is an integer.

*Attributes:*
`@unit` Unit of the duration. Valid values are 'hour', 'day', 'month' or 'year'.

*Parent element:* `<phaseout>`

### `<location>`

*Keywords:* `#physical` `#optional`

Optional URI the mashup has to be archived to before automatic removal at deadline. Deadline is calculated from date and holdback time.

*Attributes:*
`@type` Type of the location; in most caes 'archive'. The value is a string.

*Parent element:* `<phaseout>`

### `<screenshot>`

*Keywords:* `#phyiscal` `#optional`

Optional string that gives the URL of a screenshot of the mashup in use. This must be an image on a public web site that is not blocked by robots.txt. PNG is the preferred format, though GIF and JPG are also acceptable.

*Parent element:* `<workspace>`

### `<thumbnail>`

*Keywords:* `#phyiscal` `#optional`

Optional string that gives the URL of a thumbnail image or icon to display for the mashup. This must be an image on a public web site that is not blocked by robots.txt. PNG is the preferred format, though GIF and JPG are also acceptable.

*Parent element:* `<workspace>`
