# TigerData Data Model and Dictionary

## Draft Documentation, v0.7

Drafted by Matt Chandler and Halle Burns  
Last updated on Nov 26, 2024 by Halle Burns

---

Inspiration:

* [Datacite](https://datacite-metadata-schema.readthedocs.io/en/4.5/properties/) metadata schema  
* [PREMIS](https://www.loc.gov/standards/premis/v3/premis-3-0-final.pdf) metadata schema

Other documents

* [https://github.com/pulibrary/tigerdata-app/blob/main/docs/td\_xml\_schema\_101.md](https://github.com/pulibrary/tigerdata-app/blob/main/docs/td_xml_schema_101.md)   
* [Schema documentation spreadsheets](https://drive.google.com/drive/u/0/folders/1pfwK7xDrth6NWgMel6yxaIggTb_aWrQk)

[**ChangeLog	7**](#changelog)

[**Introduction	7**](#introduction)

[Background	7](#background)

[What is TigerData?	7](#what-is-tigerdata?)

[TigerData Metadata Working Group	8](#tigerdata-metadata-working-group)

[Members	8](#members)

[Model	9](#model)

[TigerData’s Data Model	9](#tigerdata’s-data-model)

[Projects	9](#projects)

[Items	9](#items)

[Relationships	9](#relationships)

[Implementation	9](#implementation)

[Using the Data Dictionary	9](#using-the-data-dictionary)

[Groups, Elements, Sub-Elements, and Attributes	9](#groups,-elements,-sub-elements,-and-attributes)

[Attribute Usage Notes	10](#attribute-usage-notes)

[Definitions	10](#definitions)

[**TigerData Data Definitions (Resource)	12**](#tigerdata-data-definitions-\(resource\))

[1.0 resource	12](#1.0-resource)

[**TigerData Data Definitions (ProjectFields)	13**](#tigerdata-data-definitions-\(projectfields\))

[1.0 projectID	13](#1.0-projectid)

[2.0 alternativeIDs	14](#2.0-alternativeids)

[2.1 alterativeID	14](#2.1-alterativeid)

[3.0 parentProject	16](#3.0-parentproject)

[4.0 dataSponsor	17](#4.0-datasponsor)

[4.1 netID	18](#4.1-netid)

[4.2 orcid	18](#4.2-orcid)

[4.3 fullName	19](#4.3-fullname)

[4.4 givenName	19](#4.4-givenname)

[4.5 familyName	20](#4.5-familyname)

[4.6 nameDate	20](#4.6-namedate)

[4.7 alternativeNameIdentifer	21](#4.7-alternativenameidentifer)

[5.0 dataManager	22](#5.0-datamanager)

[5.1 netID	23](#5.1-netid)

[5.2 orcid	23](#5.2-orcid)

[5.3 fullName	24](#5.3-fullname)

[5.4 givenName	24](#5.4-givenname)

[5.5 familyName	25](#5.5-familyname)

[5.6 nameDate	25](#5.6-namedate)

[5.7 alternativeNameIdentifer	26](#5.7-alternativenameidentifer)

[6.0 dataUsers	27](#6.0-datausers)

[6.1 dataUser	28](#6.1-datauser)

[6.1.1 netID	29](#6.1.1-netid)

[6.1.2 orcid	30](#6.1.2-orcid)

[6.1.3 fullName	30](#6.1.3-fullname)

[6.1.4 givenName	31](#6.1.4-givenname)

[6.1.5 familyName	31](#6.1.5-familyname)

[6.1.6 nameDate	32](#6.1.6-namedate)

[6.1.7 alternativeNameIdentifer	32](#6.1.7-alternativenameidentifer)

[7.0 researchDomains	34](#7.0-researchdomains)

[7.1 researchDomain	34](#7.1-researchdomain)

[8.0 departments	36](#8.0-departments)

[8.1 department	36](#8.1-department)

[9.0 projectDirectory	38](#9.0-projectdirectory)

[9.1 projectDirectoryPath	38](#9.1-projectdirectorypath)

[9.2 requestedValue	39](#9.2-requestedvalue)

[9.3 approvedValue	40](#9.3-approvedvalue)

[10.0 title	42](#10.0-title)

[11.0 description	43](#11.0-description)

[12.0 languages	44](#12.0-languages)

[12.1 language	44](#12.1-language)

[13.0 storageCapacity	46](#13.0-storagecapacity)

[13.1 storageCapacitySetting	47](#13.1-storagecapacitysetting)

[13.1.1 size	47](#13.1.1-size)

[13.1.2 unit	48](#13.1.2-unit)

[13.2 requestedValue	49](#13.2-requestedvalue)

[13.2.1 size	49](#13.2.1-size)

[13.2.2 unit	50](#13.2.2-unit)

[13.3 approvedValue	50](#13.3-approvedvalue)

[13.3.1 size	51](#13.3.1-size)

[13.3.2 unit	51](#13.3.2-unit)

[14.0 projectVisibility	53](#14.0-projectvisibility)

[15.0 storagePerformance	54](#15.0-storageperformance)

[15.1 storagePerformanceSetting	54](#15.1-storageperformancesetting)

[15.2 requestedValue	55](#15.2-requestedvalue)

[15.3 approvedValue	56](#15.3-approvedvalue)

[16.0 numberOfFiles	58](#16.0-numberoffiles)

[17.0 hpc	59](#17.0-hpc)

[18.0 projectPurpose	60](#18.0-projectpurpose)

[19.0 provisionalProject	61](#19.0-provisionalproject)

[20.0 grantFunded	62](#20.0-grantfunded)

[21.0 fundingReferences	63](#21.0-fundingreferences)

[21.1 fundingReference	64](#21.1-fundingreference)

[21.1.1 funderName	64](#21.1.1-fundername)

[21.1.2 funderID	65](#21.1.2-funderid)

[21.1.3 awardNumber	65](#21.1.3-awardnumber)

[21.1.4 awardTitle	66](#21.1.4-awardtitle)

[22.0 dates	67](#22.0-dates)

[22.1 startDate	68](#22.1-startdate)

[22.2 endDate	68](#22.2-enddate)

[22.3 retirementDate	69](#22.3-retirementdate)

[22.4 publicationDate	69](#22.4-publicationdate)

[22.5 otherDate	70](#22.5-otherdate)

[23.0 resourceType	71](#23.0-resourcetype)

[24.0 licenses	72](#24.0-licenses)

[24.1 license	72](#24.1-license)

[25.0 dataUseAgreement	74](#25.0-datauseagreement)

[26.0 duaReferences	75](#26.0-duareferences)

[26.1 duaReference	75](#26.1-duareference)

[26.1.1 grantorName	76](#26.1.1-grantorname)

[26.1.2 duaID	77](#26.1.2-duaid)

[26.1.3 duaTitle	77](#26.1.3-duatitle)

[27.0 keywords	79](#27.0-keywords)

[27.1 keyword	80](#27.1-keyword)

[28.0 relations	81](#28.0-relations)

[28.1 relation	81](#28.1-relation)

[29.0 extendedMetadataSchemas	83](#29.0-extendedmetadataschemas)

[29.1 extendedMetadataSchema	83](#29.1-extendedmetadataschema)

[30.0 projectProvenance	85](#30.0-projectprovenance)

[30.1 submission	92](#30.1-submission)

[30.1.1 requestedBy	93](#30.1.1-requestedby)

[30.1.1.1 netID	94](#30.1.1.1-netid)

[30.1.1.2 orcid	95](#30.1.1.2-orcid)

[30.1.1.3 fullName	95](#30.1.1.3-fullname)

[30.1.1.4 givenName	96](#30.1.1.4-givenname)

[30.1.1.5 familyName	96](#30.1.1.5-familyname)

[30.1.1.6 nameDate	97](#30.1.1.6-namedate)

[30.1.1.7 alternativeNameIdentifer	97](#30.1.1.7-alternativenameidentifer)

[30.1.2 requestDateTime	98](#30.1.2-requestdatetime)

[30.1.3 approvedBy	98](#30.1.3-approvedby)

[30.1.3.1 netID	99](#30.1.3.1-netid)

[30.1.3.2 orcid	99](#30.1.3.2-orcid)

[30.1.3.3 fullName	100](#30.1.3.3-fullname)

[30.1.3.4 givenName	100](#30.1.3.4-givenname)

[30.1.3.5 familyName	101](#30.1.3.5-familyname)

[30.1.3.6 nameDate	101](#30.1.3.6-namedate)

[30.1.3.7 alternativeNameIdentifer	102](#30.1.3.7-alternativenameidentifer)

[30.1.4 approvedDateTime	102](#30.1.4-approveddatetime)

[30.1.5 deniedBy	103](#30.1.5-deniedby)

[30.1.5.1 netID	104](#30.1.5.1-netid)

[30.1.5.2 orcid	104](#30.1.5.2-orcid)

[30.1.5.3 fullName	105](#30.1.5.3-fullname)

[30.1.5.4 givenName	105](#30.1.5.4-givenname)

[30.1.5.5 familyName	106](#30.1.5.5-familyname)

[30.1.5.6 nameDate	106](#30.1.5.6-namedate)

[30.1.5.7 alternativeNameIdentifer	107](#30.1.5.7-alternativenameidentifer)

[30.1.6 denialDateTime	107](#30.1.6-denialdatetime)

[30.1.7 eventNote	108](#30.1.7-eventnote)

[30.1.7.1 noteBy	109](#30.1.7.1-noteby)

[30.1.7.1.1 netID	109](#30.1.7.1.1-netid)

[30.1.7.1.2 orcid	110](#30.1.7.1.2-orcid)

[30.1.7.1.3 fullName	110](#30.1.7.1.3-fullname)

[30.1.7.1.4 givenName	111](#30.1.7.1.4-givenname)

[30.1.7,1.5 familyName	111](#30.1.7,1.5-familyname)

[30.1.7.1.6 nameDate	112](#30.1.7.1.6-namedate)

[30.1.7.1.7 alternativeNameIdentifer	112](#30.1.7.1.7-alternativenameidentifer)

[30.1.7.2 noteDateTime	113](#30.1.7.2-notedatetime)

[30.1.7.3 eventType	113](#30.1.7.3-eventtype)

[30.1.7.4 message	114](#30.1.7.4-message)

[30.2 revisions	115](#30.2-revisions)

[30.2.1 revision	117](#30.2.1-revision)

[30.3 retirement	119](#30.3-retirement)

[30.4 publication	120](#30.4-publication)

[30.5 status	122](#30.5-status)

[30.6 schemaVersion	123](#30.6-schemaversion)

[TigerData Data Definitions (ItemFields)	125](#tigerdata-data-definitions-\(itemfields\))

[1.0 itemID	125](#1.0-itemid)

[2.0 alternativeIDs	126](#2.0-alternativeids-1)

[2.1 alterativeID	126](#2.1-alterativeid-1)

[3.0 parentProject	128](#3.0-parentproject-1)

[4.0 dataUsers	129](#4.0-datausers)

[4.1 dataUser	130](#4.1-datauser)

[4.1.1 netID	131](#4.1.1-netid)

[4.1.2 orcid	132](#4.1.2-orcid)

[4.1.3 fullName	132](#4.1.3-fullname)

[4.1.4 givenName	133](#4.1.4-givenname)

[4.1.5 familyName	133](#4.1.5-familyname)

[4.1.6 nameDate	134](#4.1.6-namedate)

[4.1.7 alternativeNameIdentifer	134](#4.1.7-alternativenameidentifer)

[5.0 title	136](#5.0-title)

[6.0 description	137](#6.0-description)

[7.0 resourceType	138](#7.0-resourcetype)

[8.0 keywords	139](#8.0-keywords)

[8.1 keyword	139](#8.1-keyword)

[9.0 relations	141](#9.0-relations)

[9.1 relation	141](#9.1-relation)

[10.0 extendedMetadataSchemas	143](#10.0-extendedmetadataschemas)

[10.1 extendedMetadataSchema	143](#10.1-extendedmetadataschema)

[11.0 languages	145](#11.0-languages)

[11.1 language	145](#11.1-language)

[12.0 licenses	147](#12.0-licenses)

[12.1 license	147](#12.1-license)

[13.0 fundingReferences	149](#13.0-fundingreferences)

[13.1 fundingReference	149](#13.1-fundingreference)

[13.1.1 funderName	150](#13.1.1-fundername)

[13.1.2 funderID	151](#13.1.2-funderid)

[13.1.3 awardNumber	151](#13.1.3-awardnumber)

[13.1.4 awardTitle	152](#13.1.4-awardtitle)

[14.0 duaReferences	153](#14.0-duareferences)

[14.1 duaReference	153](#14.1-duareference)

[14.1.1 grantorName	154](#14.1.1-grantorname)

[14.1.2 duaID	155](#14.1.2-duaid)

[14.1.3 duaTitle	155](#14.1.3-duatitle)

[15.0 dates	156](#15.0-dates)

[15.1 startDate	157](#15.1-startdate)

[15.2 endDate	157](#15.2-enddate)

[15.3 retirementDate	158](#15.3-retirementdate)

[15.4 publicationDate	158](#15.4-publicationdate)

[15.5 otherDate	159](#15.5-otherdate)

[TigerData Data Definitions (Attributes)	160](#tigerdata-data-definitions-\(attributes\))

[approved	160](#approved)

[alternativeIDType	160](#alternativeidtype)

[awardURI	161](#awarduri)

[classificationCode	161](#classificationcode)

[dateType	162](#datetype)

[dateInformation	163](#dateinformation)

[departmentAbbreviation	163](#departmentabbreviation)

[departmentCode	164](#departmentcode)

[discoverable	164](#discoverable)

[duaURI	164](#duauri)

[inherited	165](#inherited)

[itemIDType	165](#itemidtype)

[funderIDType	166](#funderidtype)

[funderIDSchema	167](#funderidschema)

[licenseID	167](#licenseid)

[licenseIDScheme	168](#licenseidscheme)

[licenseIDSchemeURI	168](#licenseidschemeuri)

[licenseURI	169](#licenseuri)

[nameIdentifierScheme	170](#nameidentifierscheme)

[projectIDType	170](#projectidtype)

[protocol	171](#protocol)

[readOnly	171](#readonly)

[relatedIDType	172](#relatedidtype)

[relatedMetadataScheme	173](#relatedmetadatascheme)

[relatedMetadataSchemeType	174](#relatedmetadataschemetype)

[relatedMetadataSchemeURI	174](#relatedmetadataschemeuri)

[relationType	175](#relationtype)

[resourceClass	178](#resourceclass)

[resourceID	178](#resourceid)

[resourceIDType	179](#resourceidtype)

[resourceTypeGeneral	179](#resourcetypegeneral)

[schemeURI	182](#schemeuri)

[subjectScheme	182](#subjectscheme)

[subjectSchemeURI	183](#subjectschemeuri)

[trackingLevel	183](#trackinglevel)

[userID	184](#userid)

[userIDType	184](#useridtype)

[valueURI	185](#valueuri)

[**Appendix	185**](#appendix)

[Appendix 1: Example XML for TigerData Projects	185](#appendix-1:-example-xml-for-tigerdata-projects)

[Appendix 2: Example XML for TigerData Items	185](#appendix-2:-example-xml-for-tigerdata-items)

# ChangeLog {#changelog}

* 2024-11-18 \- Continued drafting of the supplemental XML. Began drafting of the Introduction.  
* 2024-11-05 \- Finished up documenting attributes and items. Added a Resource Definitions field.  
* 2024-11-04 \- Finishing up the baseline for TigerData Projects. Decision was made regarding field 30 (projectProvenance) to reduce repetition of fields. Began documentation of attributes  
* 2024-10-29 \- Revamped the organization, defined the data dictionary fields. Began first pass of documenting the dictionary linearly.  
* 2024-09-30 \- Adding in sections for Introduction as well as “How to Use the Data Dictionary”  
* 2024-09-30 \- Redoing baseline organization to address the changes in schema composition  
* 2024-08-23 \- Setting up baseline document organization

# Introduction {#introduction}

## Background {#background}

### What is TigerData? {#what-is-tigerdata?}

TigerData is a comprehensive set of data and storage management tools that provide storage capacity, reliability, functionality, and performance to meet the needs of a rapidly changing research landscape and to enable new opportunities for leveraging the power of institutional data. It includes data management tools and services in concert with a community of practice that enables researchers and data managers to describe and tag their research materials, to seamlessly move them between different storage architectures, and to easily find their data and code for re-use and collaboration. The resulting ecosystem facilitates research and contributes to the stewardship of knowledge to enable reusability and preservation of data and code produced by Princeton University.

Using MediaFlux as a middleware platform, with the front-end custom-built to…

### TigerData Metadata Working Group {#tigerdata-metadata-working-group}

The TigerData Metadata Working Group (TMWG) is the central body charged with establishing and maintaining the standards and best practices for metadata within TigerData. Established in early 2023, the working group is responsible for:

* Defining the framework for operational decision making pertaining to the recording and cataloging of metadata in TigerData;  
* Codifying the minimal set of metadata required for all projects in TigerData;  
* Developing and maintaining guidelines for the use of metadata beyond the minimum standards in TigerData;  
* Discerning the application of guidance on matters relevant to metadata from the TigerData Steering Committee or other key stakeholders;  
* Interpreting the [FAIR Principles](https://www.go-fair.org/fair-principles/) and other relevant standards for data stewardship and data ethics in the University context and evaluating the extent to which TigerData design decisions and implementations align with them;  
* Disseminating the working group’s policies, guidelines, and recommendations to all relevant stakeholders.

#### Members {#members}

Charles Bentler, Member

Bobray Bordelon, Member (2023-2024)

Lori Bougher, Member

Halle Burns, Member, Co-chair (2024-present) 

Matt Chandler, Chair

Esmé Cowles, Member (2024-present), Co-chair (2023-2024)

Wind Cowles, Library Strategy Council Sponsor

Hannah Hadley, Member

Robert Knight, Member

Irene Kopaliani, Member

Meghan Testerman, Member ex-officio

#### Model {#model}

This metadata schema was designed by Matt Chandler and drafted by Matt Chandler and Halle Burns. Members of the TMWG provided feedback on the metadata design and planned implementation.

## TigerData’s Data Model {#tigerdata’s-data-model}

### Projects {#projects}

### Items {#items}

### Relationships {#relationships}

## Implementation {#implementation}

# Using the Data Dictionary {#using-the-data-dictionary}

The TigerData metadata schema is built in a modular fashion, with many elements being repeated and referenced throughout the schema, as applicable. Due to the complex and interchanging relationships between elements, the Data Dictionary is divided into several sections:

1. Resource  
2. ProjectFields  
3. ItemFields  
4. Attributes

This allows the dictionary to replicate the expected payload while also establishing repeated attributes.

## Groups, Elements, Sub-Elements, and Attributes {#groups,-elements,-sub-elements,-and-attributes}

Due to the non-linear structure and the complexity of relationships between units within the TigerData schema and infrastructure, units are organized and labeled based on their existence in the metadata hierarchy. Therefore, some units (examples include the inherited, discoverable, and trackingLevel attributes) may have multiple numerical identifiers attached to their names.

| XML Representation | Example |
| :---- | :---- |
| Group, Container, or Element | 4.0 dataSponsor |
| Sub-Element | 4.1 netID |
| Attribute | 4.0.a userID |

### Attribute Usage Notes {#attribute-usage-notes}

Attributes are only explicitly defined in the Attribute section of this document. However, attributes are frequently referenced and listed throughout the two core Data Definitions sections (both Projects and Items). 

When attributes are referenced as fields in the semantic components area, they will appear as the name of the attribute (with an accompanying hyperlink to the definition). 

*Example:*  
4.0a [userID](#userid)

For frequently utilized attributes, where a set or controlled value is indicated as part of their accompaniment in the defined Data Definition fields, the attribute will appear as the name of the attribute (with an accompanying hyperlink to the definition) followed by an equals-sign and then the set or controlled value.

*Example:*  
4.0a [userID](#userid)  
4.0b [userIDType](#useridtype) \= NetID  
4.0c inherited \= true

## Definitions {#definitions}

**Semantic Unit:** (required) Name of the unit as written in CamelCase. The unit could be an XML group, element, sub-element, or attribute.

**Semantic Components:** (optional) Name of sub-units or attributes, as applicable, written in CamelCase. The unit could be an XML container, element, sub-element, or attribute. Field is not applicable to [TigerData Attribute Definitions](#tigerdata-data-definitions-\(attributes\)).

**Used In:** (required) A list of the XML containers, elements, or sub-elements an attribute is used in. Field is only applicable to [TigerData Attribute Definitions](#tigerdata-data-definitions-\(attributes\)).

**Definition:** (required) The general description of the XML unit.

**Data Constraint:** (required) Any constraints regarding the entry of data into the unit. This could refer to data types (such as xs:string), controlled vocabulary, identifying it as an XML container, or regular expression patterns.

**Applicability:** (required) Notes whether a unit can be used for a project, an item, or both.

Controlled vocabulary:

* Projects  
* Items  
* Projects, Items

**Obligation:** (required) Whether the unit is required to validate the schema. 

Controlled vocabulary:

* Required  
* Not required

**Repeatability:** (required) Whether the unit is repeatable within the schema.

Controlled vocabulary:

* Repeatable  
* Not repeatable

**Creation/Maintenance Notes:** (optional) Information specifying any procedures (including automated) necessary for the creation or continued upkeep of the unit.

**Usage Notes:** (optional) Information specific to utilizing the unit in the metadata schema. An example of this could include how many times a unit is repeatable.

**Links:** (optional) A place to link to relevant resources. Examples include where language is based on or adapted from pre-existing metadata schemas (such as DataCite), international standards (such as ISO 8601\) or local resources (such as Princeton’s PeopleSoft).

**Example:** (required) The highest-level field in each section will contain an example written in XML, showcasing all possible options related to the documentation of a unit. Field is not applicable to [TigerData Attribute Definitions](#tigerdata-data-definitions-\(attributes\)).

## 

# TigerData Data Definitions (Resource) {#tigerdata-data-definitions-(resource)}

## 1.0 resource {#1.0-resource}

**Semantic Unit:** resource

**Semantic Components:**   
1.0a [resourceClass](#resourceclass)  
1.0b [resourceID](#resourceid)  
1.0c [resourceIDType](#resourceidtype)  
2.0 [projectFields](#tigerdata-data-definitions-\(projectfields\))  
3.0 [itemFields](#tigerdata-data-definitions-\(itemfields\))

**Definition:** Root element of any metadata record for TigerData resources (projects and items).

**Data Constraint:** Container

**Applicability:** Projects, Items

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** If the resourceClass is Project, then the projectFields group must be used. If the resourceClass is Item, then the itemFields group must be used.

**Links:** None

**Example:** See [Appendix 1](#appendix-1:-example-xml-for-tigerdata-projects) (projects) and [Appendix 2](#appendix-2:-example-xml-for-tigerdata-items) (items)

# 

# TigerData Data Definitions (ProjectFields) {#tigerdata-data-definitions-(projectfields)}

## 1.0 projectID {#1.0-projectid}

**Semantic Unit:** projectID

**Semantic Components:**  
1.0a [projectIDType](#projectidtype) \= DOI  
1.0b inherited \= false  
1.0c discoverable \= true  
1.0d trackingLevel \= trackingRecord

**Definition:** The universally unique identifier for the project.

**Data Constraint:** xs:string

Pattern: 10\\.\\d{4,9}\\/\[\\S\]+\[^-\_\!:;,.?/\\\\\\s\]

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Only DOIs, as created by Princeton’s instance of DataCite Fabrica, will be allowed in this unit. DOIs are minted automatically when individuals request TigerData project space. Princeton’s TigerData DOI prefix is 10.60803.

Standard type used for DOI values (just the prefix and suffix; not a full URL). DOI is short for Digital Object Identifier. Applies a pattern aligned with ISO 26324:2022, allowing any suffix that doesn't have whitespace and doesn't end with unexpected punctuation.

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<projectID projectIDType="DOI" inherited="false" discoverable="true" trackingLevel="ResourceRecord"\>10.60803/az09-0002\</projectID\>\`\`\`

## 

## 2.0 alternativeIDs {#2.0-alternativeids}

**Semantic Unit:** alternativeIDs

**Semantic Components:**   
2.0a discoverable \= true  
2.0b trackingLevel \= ResourceRecord  
2.1 alternativeID  
	2.1a [alternativeIDType](#alternativeidtype)  
	2.1b inherited

**Definition:** The container element for all alternative IDs for a resource

**Data Constraint:** Container

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<alternativeIDs discoverable=”true” trackingLevel=”ResourceRecord”\>  
\<alternativeID alternativeIDType="DOI" inherited="false"\>10.60803/s609-0022\</alternativeID\>  
\</alternativeIDs\>\`\`\`

### 2.1 alterativeID {#2.1-alterativeid}

**Semantic Unit:** alternativeID

**Semantic Components:**   
2.1a [alternativeIDType](#alternativeidtype)  
2.1b inherited

**Definition:** An alternative identifier for the resource (not the standard TigerData projectID or itemID).

**Data Constraint:** xs:string

**Applicability:** Projects, Items

**Obligation:** Required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Element is repeatable up to 100 times

**Links:** None

## 3.0 parentProject {#3.0-parentproject}

**Semantic Unit:** parentProject

**Semantic Components:**   
3.0a [projectIDType](#projectidtype) \= DOI  
3.0b inherited  
3.0c discoverable \= true  
3.0d trackingLevel \= ResourceRecord

**Definition:** The ID of the project to which the resource belongs directly. Takes precedence over any IsChildOf relations to other projects.

**Data Constraint:** xs:string

Pattern: 10\\.\\d{4,9}\\/\[\\S\]+\[^-\_\!:;,.?/\\\\\\s\]

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Only DOIs, as created by Princeton’s instance of DataCite Fabrica, will be allowed in this unit. DOIs are minted automatically when individuals request TigerData project space. Princeton’s TigerData DOI prefix is 10.60803.

Standard type used for DOI values (just the prefix and suffix; not a full URL). DOI is short for Digital Object Identifier. Applies a pattern aligned with ISO 26324:2022, allowing any suffix that doesn't have whitespace and doesn't end with unexpected punctuation

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<parentProject projectIDType="DOI" inherited="false" discoverable="true" trackingLevel="ResourceRecord"\>10.60803/89s3-0023\</projectID\>\`\`\`

## 

## 4.0 dataSponsor {#4.0-datasponsor}

**Semantic Unit:** dataSponsor

**Semantic Components:**   
4.0a [userID](#userid)  
4.0b [userIDType](#useridtype) \= NetID  
4.0c inherited \= true  
4.0d discoverable \= true  
4.0e trackingLevel \= ResourceRecord  
4.1 netID  
4.2 orcid  
4.3 fullName  
4.4 givenName  
4.5 familyName  
4.6 nameDate  
4.7 alternativeNameIdentifer  
4.7a [nameIdentifierScheme](#nameidentifierscheme)  
4.7b [schemeURI](#schemeuri)

**Definition:** The person who takes primary responsibility for the project

**Data Constraint:** See Usage Notes.

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:**   
This unit will contain either:

* The highest level attributes (4.0a-4.0e) and a blank field  
* The accompanying sub-elements  
* Both

**Links:** None

**Example:**   
\`\`\`\<dataSponsor userID="hb0344" userIDType="NetID" discoverable="true" inherited="true" trackingLevel="ResourceRecord"\>  
	\<netID\>hb0344\</netID\>  
	\<orcid\>https://orcid.org/0000-0003-2346-2876\</orcid\>  
	\<fullName\>Burns, Halle\</fullName\>  
	\<givenName\>Halle\</givenName\>  
	\<familyName\>Burns\</familyName\>  
	\<nameDate\>2024-10-29\</nameDate\>  
	\<alternativeNameIdentifier nameIdentifierScheme=“Scopus” schemeURI=“https://www.scopus.com/authid/detail.uri?authorId=57450022500”\>57450022500\</alternativeNameIdentifier\>  
\</dataSponsor\>\`\`\`

Also valid:  
\`\`\`\<dataSponsor userID="hb0344" userIDType="NetID" discoverable="true" inherited="true" trackingLevel="ResourceRecord"\>\</dataSponsor\>\`\`\`

### 4.1 netID {#4.1-netid}

**Semantic Unit:** netID

**Semantic Components:** None

**Definition:** The University NetID (also called the OIT NetID) is the name or user-id that identifies a person to a computer system or electronic service at Princeton.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** If this netID sub-element is included, its value should match that of the 4.0a userID attribute.

**Usage Notes:** None

**Links:** 

### 4.2 orcid {#4.2-orcid}

**Semantic Unit:** orcid

**Semantic Components:** None

**Definition:** The ORCID ID URL for the person in a given role, if available and if verified as valid against the ORCID API upon entry.

**Data Constraint:** xs:anyURI

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Must be validated against the ORCID API

**Usage Notes:** None

**Links:** 

### 4.3 fullName {#4.3-fullname}

**Semantic Unit:** fullName

**Semantic Components:** None

**Definition:** The full name of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Automatically generated based on information noted in 4.4 and 4.5. Must be verified in the format family-comma-given and matching the corresponding given and family name fields.

**Usage Notes:** None

**Links:** None

### 4.4 givenName {#4.4-givenname}

**Semantic Unit:** givenName

**Semantic Components:** None

**Definition:** The given name(s) of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** 

**Usage Notes:** If the person has multiple given names, then all should be included in this field, along with any suffixes.

**Links:** None

### 4.5 familyName {#4.5-familyname}

**Semantic Unit:** familyName

**Semantic Components:** None

**Definition:** The family name(s) of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** 

**Usage Notes:** If the person has multiple family names, then all should be included in this field.

**Links:** None

### 4.6 nameDate {#4.6-namedate}

**Semantic Unit:** nameDate

**Semantic Components:** None

**Definition:** The date at which the name metadata was recorded, using the ISO 8601 date format (YYYY-MM-DD).

**Data Constraint:** xs:date

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Automatically populated.

**Usage Notes:** None

**Links:** None

### 4.7 alternativeNameIdentifer {#4.7-alternativenameidentifer}

**Semantic Unit:** alternativeNameIdentifier

**Semantic Components:**   
4.7a [nameIdentifierScheme](#nameidentifierscheme)  
4.7b [schemeURI](#schemeuri)

**Definition:** Records alternative (non-ORCID) identifier(s) for the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

## 

## 5.0 dataManager {#5.0-datamanager}

**Semantic Unit:** dataManager

**Semantic Components:**   
5.0a [userID](#userid)  
5.0b [userIDType](#useridtype) \= NetID  
5.0c inherited  
5.0d discoverable  
5.0e trackingLevel \= ResourceRecord  
5.1 netID  
5.2 orcid  
5.3 fullName  
5.4 givenName  
5.5 familyName  
5.6 nameDate  
5.7 alternativeNameIdentifer  
5.7a [nameIdentifierScheme](#nameidentifierscheme)  
5.7b [schemeURI](#schemeuri)

**Definition:** The person who manages the day-to-day activities for the project

**Data Constraint:** See Usage Notes

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:**   
This unit will contain either:

* The highest level attributes (5.0a-5.0e) and a blank field  
* The accompanying sub-elements  
* Both

**Links:** None

**Example:**   
\`\`\`\<dataManager userID="hb0344" userIDType="NetID" discoverable="true" inherited="true" trackingLevel="ResourceRecord"\>  
	\<netID\>hb0344\</netID\>  
	\<orcid\>https://orcid.org/0000-0003-2346-2876\</orcid\>  
	\<fullName\>Burns, Halle\</fullName\>  
	\<givenName\>Halle\</givenName\>  
	\<familyName\>Burns\</familyName\>  
	\<nameDate\>2024-10-29\</nameDate\>  
	\<alternativeNameIdentifier nameIdentifierScheme=“Scopus” schemeURI=“https://www.scopus.com/authid/detail.uri?authorId=57450022500”\>57450022500\</alternativeNameIdentifier\>  
\</dataManager\>\`\`\`

Also valid:  
\`\`\`\<dataManager userID="hb0344" userIDType="NetID" discoverable="true" inherited="true" trackingLevel="ResourceRecord"\>\</dataManager\>\`\`\`

### 5.1 netID {#5.1-netid}

**Semantic Unit:** netID

**Semantic Components:** None

**Definition:** The University NetID (also called the OIT NetID) is the name or user-id that identifies a person to a computer system or electronic service at Princeton.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** If this netID sub-element is included, its value should match that of the 5.0a userID attribute.

**Usage Notes:** None

**Links:** 

### 5.2 orcid {#5.2-orcid}

**Semantic Unit:** orcid

**Semantic Components:** None

**Definition:** The ORCID ID URL for the person in a given role, if available and if verified as valid against the ORCID API upon entry.

**Data Constraint:** anyURI

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Must be validated against the ORCID API

**Usage Notes:** None

**Links:** 

### 5.3 fullName {#5.3-fullname}

**Semantic Unit:** fullName

**Semantic Components:** None

**Definition:** The full name of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Automatically generated. Must be verified in the format family-comma-given and matching the corresponding given and family name fields.

**Usage Notes:** None

**Links:** None

### 5.4 givenName {#5.4-givenname}

**Semantic Unit:** givenName

**Semantic Components:** None

**Definition:** The given name(s) of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** 

**Usage Notes:** If the person has multiple given names, then all should be included in this field, along with any suffixes.

**Links:** None

### 5.5 familyName {#5.5-familyname}

**Semantic Unit:** familyName

**Semantic Components:** None

**Definition:** The family name(s) of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** 

**Usage Notes:** If the person has multiple family names, then all should be included in this field.

**Links:** None

### 5.6 nameDate {#5.6-namedate}

**Semantic Unit:** nameDate

**Semantic Components:** None

**Definition:** The date at which the name metadata was recorded, using the ISO 8601 date format (YYYY-MM-DD).

**Data Constraint:** xs:date

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

### 5.7 alternativeNameIdentifer {#5.7-alternativenameidentifer}

**Semantic Unit:** alternativeNameIdentifier

**Semantic Components:**   
5.7a [nameIdentifierScheme](#nameidentifierscheme)  
5.7b [schemeURI](#schemeuri)

**Definition:** Records alternative (non-ORCID) identifier(s) for the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

## 

## 6.0 dataUsers {#6.0-datausers}

**Semantic Unit:** dataUsers

**Semantic Components:**   
6.0a trackingLevel \= ResourceRecord  
6.1 dataUser  
6.1a [userID](#userid)  
6.1b [userIDType](#useridtype) \= NetID  
6.1c [readOnly](#readonly)  
6.1d inherited  
6.1e discoverable  
6.1.1 netID  
6.1.2 orcid  
6.1.3 fullName  
6.1.4 givenName  
6.1.5 familyName  
6.1.6 nameDate  
6.1.7 alternativeNameIdentifer  
6.1.7a [nameIdentifierScheme](#nameidentifierscheme)  
6.1.7b [schemeURI](#schemeuri)

**Definition:** The container element for all data users of a resource.

**Data Constraint:** Container

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<dataUsers trackingLevel=”ResourceRecord”\>  
\<dataUser userID="hb0344" userIDType="NetID" readOnly=“false” discoverable="true" inherited="true"\>  
		\<netID\>hb0344\</netID\>  
		\<orcid\>https://orcid.org/0000-0003-2346-2876\</orcid\>  
		\<fullName\>Burns, Halle\</fullName\>  
		\<givenName\>Halle\</givenName\>  
		\<familyName\>Burns\</familyName\>  
		\<nameDate\>2024-10-29\</nameDate\>  
\<alternativeNameIdentifier nameIdentifierScheme=“Scopus” schemeURI=“[https://www.scopus.com/authid/detail.uri?authorId=57450022500](https://www.scopus.com/authid/detail.uri?authorId=57450022500)”\>57450022500\</alternativeNameIdentifier\>  
\</dataUser\>  
\<dataUser userID="mjc12" userIDType="NetID" readOnly=“false” discoverable="true" inherited="true"\>  
		\<netID\>mjc12\</netID\>  
		\<orcid\>https://orcid.org/0000-0001-9317-7056\</orcid\>  
		\<fullName\>Chandler, Matt\</fullName\>  
		\<givenName\>Matt\</givenName\>  
		\<familyName\>Chandler\</familyName\>  
		\<nameDate\>2024-11-05\</nameDate\>  
\<alternativeNameIdentifier nameIdentifierScheme=“Scopus” schemeURI=“https://www.webofscience.com/wos/author/record/AGR-7086-2022”\>AGR-7086-2022\</alternativeNameIdentifier\>  
\</dataUser\>  
\</dataUsers\>\`\`\`

Also valid:  
\`\`\`\<dataUsers trackingLevel=”ResourceRecord”\>  
\<dataUser userID="hb0344" userIDType="NetID" readOnly=“false” discoverable="true" inherited="true"\>\</dataUser\>  
\<dataUser userID="mjc12" userIDType="NetID" readOnly=“false” discoverable="true" inherited="true"\>\</dataUser\>  
\</dataUsers\>\`\`\`

### 6.1 dataUser {#6.1-datauser}

**Semantic Unit:** dataUser

**Semantic Unit:** dataManager

**Semantic Components:**   
6.1a [userID](#userid)  
6.1b [userIDType](#useridtype) \= NetID  
6.1c [readOnly](#readonly)  
6.1d inherited  
6.1e discoverable  
6.1.1 netID  
6.1.2 orcid  
6.1.3 fullName  
6.1.4 givenName  
6.1.5 familyName  
6.1.6 nameDate  
6.1.7 alternativeNameIdentifer  
6.1.7a [nameIdentifierScheme](#nameidentifierscheme)  
6.1.7b [schemeURI](#schemeuri)

**Definition:** The person who manages the day-to-day activities for the project

**Data Constraint:** See Usage Notes

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:**   
This unit will contain either:

* The highest level attributes (6.0a-6.0e) and a blank field  
* The accompanying sub-elements  
* Both

**Links:** None

#### 6.1.1 netID {#6.1.1-netid}

**Semantic Unit:** netID

**Semantic Components:** None

**Definition:** The University NetID (also called the OIT NetID) is the name or user-id that identifies a person to a computer system or electronic service at Princeton.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** If this netID sub-element is included, its value should match that of the 6.0a userID attribute.

**Usage Notes:** None

**Links:** 

#### 6.1.2 orcid {#6.1.2-orcid}

**Semantic Unit:** orcid

**Semantic Components:** None

**Definition:** The ORCID ID URL for the person in a given role, if available and if verified as valid against the ORCID API upon entry.

**Data Constraint:** anyURI

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Must be validated against the ORCID API

**Usage Notes:** None

**Links:** 

#### 6.1.3 fullName {#6.1.3-fullname}

**Semantic Unit:** fullName

**Semantic Components:** None

**Definition:** The full name of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Automatically generated. Must be verified in the format family-comma-given and matching the corresponding given and family name fields.

**Usage Notes:** None

**Links:** None

#### 6.1.4 givenName {#6.1.4-givenname}

**Semantic Unit:** givenName

**Semantic Components:** None

**Definition:** The given name(s) of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** 

**Usage Notes:** If the person has multiple given names, then all should be included in this field, along with any suffixes.

**Links:** None

#### 6.1.5 familyName {#6.1.5-familyname}

**Semantic Unit:** familyName

**Semantic Components:** None

**Definition:** The family name(s) of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** 

**Usage Notes:** If the person has multiple family names, then all should be included in this field.

**Links:** None

#### 6.1.6 nameDate {#6.1.6-namedate}

**Semantic Unit:** nameDate

**Semantic Components:** None

**Definition:** The date at which the name metadata was recorded, using the ISO 8601 date format (YYYY-MM-DD).

**Data Constraint:** xs:date

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

#### 6.1.7 alternativeNameIdentifer {#6.1.7-alternativenameidentifer}

**Semantic Unit:** alternativeNameIdentifier

**Semantic Components:**   
6.1.7a [nameIdentifierScheme](#nameidentifierscheme)  
6.1.7b [schemeURI](#schemeuri)

**Definition:** Records alternative (non-ORCID) identifier(s) for the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

## 

## 7.0 researchDomains {#7.0-researchdomains}

**Semantic Unit:** researchDomains

**Semantic Components:**   
7.0a discoverable \= true  
7.0b trackingLevel \= ResourceRecord  
7.1 researchDomain  
7.1a inherited

**Definition:** The container element for all research domains for a project

**Data Constraint:** Container

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<researchDomains discoverable="true" trackingLevel="ResourceRecord"\>  
	\<researchDomain inherited=”true”\>Humanities\</researchDomain\>  
	\<researchDomain inherited=”true”\>Social Sciences\</researchDomain\>  
\</researchDomains\>\`\`\`

### 7.1 researchDomain {#7.1-researchdomain}

**Semantic Unit:** researchDomain

**Semantic Components:**  
7.1a inherited

**Definition:** The general field(s) of academic research related to the project, if applicable. Options are limited to the 4 domains Princeton University uses to categorize departments.

**Data Constraint:** xs:string

Controlled vocabulary:

* Natural Sciences  
* Engineering  
* Social Sciences  
* Humanities

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** 

**Usage Notes:** No duplicate entries. Can be repeated up to four times.

**Links:** None

## 

## 8.0 departments {#8.0-departments}

**Semantic Unit:** departments

**Semantic Components:**   
8.0a discoverable \= true  
8.0b trackingLevel \= ResourceRecord  
8.1 department  
8.1a [departmentCode](#departmentcode)  
8.1b [departmentAbbreviation](#departmentabbreviation)  
8.1c inherited

**Definition:** The container element for all departments for a project.

**Data Constraint:** Container

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<departments discoverable="true" trackingLevel="ResourceRecord"\>  
\<department departmentCode=”41034” departmentAbbreviation=”LIB-Data, Rsrch & Teachng Svcs” inherited="true"\>Library \- Data, Research, and Teaching Services\</department\>  
\</departments\>\`\`\`

### 8.1 department {#8.1-department}

**Semantic Unit:** department

**Semantic Components:**   
8.1a [departmentCode](#departmentcode)  
8.1b [departmentAbbreviation](#departmentabbreviation)  
8.1c inherited

**Definition:** The primary Princeton University department(s) affiliated with the project. Use the full canonical name for each recorded department.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Repeatable up to 100 times.

**Links:** 

## 

## 9.0 projectDirectory {#9.0-projectdirectory}

**Semantic Unit:** projectDirectory

**Semantic Components:**   
9.0a [approved](#approved)  
9.0b inherited \= false  
9.0c discoverable \= false  
9.0d trackingLevel \= InternalUseOnly  
9.1 projectDirectoryPath  
9.1a [protocol](#protocol)  
9.2 requestedValue  
9.2a [protocol](#protocol)  
9.3 approvedValue  
9.3a [protocol](#protocol)

**Definition:** The locally unique name for the project’s top-level directory.

**Data Constraint:** Container

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** If no user request was received and no value has yet been approved, then this container may be empty.

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<projectDirectory approved="true" inherited="false" discoverable="false" trackingLevel="InternalUseOnly"\>  
\<projectDirectoryPath\>/tigerdata/mjc12/test-project  
\</projectDirectoryPath\>  
\<requestedValue\>/tigerdata/mjc12/test-project-1\</requestedValue\>  
\<approvedValue\>/tigerdata/mjc12/test-project\</approvedValue\>  
\</projectDirectory\>\`\`\`

### 9.1 projectDirectoryPath {#9.1-projectdirectorypath}

**Semantic Unit:** projectDirectoryPath

**Semantic Components:**   
9.1a [protocol](#protocol)

**Definition:** A current setting for projectDirectory.

**Data Constraint:** xs:string

Pattern: \[\\w\\\\/-\]{14,1000}

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** This field should be omitted until the approvedValue (9.3) is set. After approval, this field should be updated to match the approvedValue field. Note: in rare cases, the current setting may later deviate from the approved value.

**Usage Notes:** Can be repeated up to 100 times. Multiple elements are allowed to specify paths in alternative protocols.

The pattern restricts the field to alphanumeric characters, underscore, forward and backslashes, and minus-dash. The typical value is expected to start "/tigerdata/" and follow with a custom directory of at least 3 characters, hence the minimum of 14 characters. The ordinary practical limit of 1000 characters for a text field applies here, but system limitations on path length may also apply.

**Links:** None

### 9.2 requestedValue {#9.2-requestedvalue}

**Semantic Unit:** requestedValue

**Semantic Components:**   
9.2a [protocol](#protocol)

**Definition:** The requested value for the projectDirectory field.

**Data Constraint:** xs:string

Pattern: \[\\w\\\\/-\]{14,1000}

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** This field is omitted if no user request was received.

**Usage Notes:** The pattern restricts the field to alphanumeric characters, underscore, forward and backslashes, and minus-dash. The typical value is expected to start "/tigerdata/" and follow with a custom directory of at least 3 characters, hence the minimum of 14 characters. The ordinary practical limit of 1000 characters for a text field applies here, but system limitations on path length may also apply.

**Links:** None

### 9.3 approvedValue {#9.3-approvedvalue}

**Semantic Unit:** approvedValue

**Semantic Components:**   
9.3a [protocol](#protocol)

**Definition:** The approved value for the projectDirectory field.

**Data Constraint:** xs:string

Pattern: \[\\w\\\\/-\]{14,1000}

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Omitted if no system administrator has approved the value yet. Once approved, the approved attribute in the projectDirectory element (9.0a) should also be set to true.

**Usage Notes:** The pattern restricts the field to alphanumeric characters, underscore, forward and backslashes, and minus-dash. The typical value is expected to start "/tigerdata/" and follow with a custom directory of at least 3 characters, hence the minimum of 14 characters. The ordinary practical limit of 1000 characters for a text field applies here, but system limitations on path length may also apply.

**Links:** None

## 

## 10.0 title {#10.0-title}

**Semantic Unit:** title

**Semantic Components:**   
10.0a xml:lang  
10.0b inherited \= false  
10.0b discoverable \= true  
10.0d trackingLevel \= ResourceRecord

**Definition:** A plain-language title for the resource.

**Data Constraint:** xs:string

String length: 1 \- 1000

**Applicability:** Projects, Items

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<title xml:lang="en" inherited="false" discoverable="true" trackingLevel="ResourceRecord"\>Test Project 1\</title\>\`\`\`

## 

## 11.0 description {#11.0-description}

**Semantic Unit:** description

**Semantic Components:**   
11.0a xml:lang  
11.0b inherited \= false  
11.0b discoverable \= true  
11.0d trackingLevel \= ResourceRecord

**Definition:** A plain-language description of the resource and/or its contents.

**Data Constraint:** xs:string

String length: 1 \- 1000

**Applicability:** Projects, Items

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<description xml:lang="en" inherited="false" discoverable="true" trackingLevel="ResourceRecord"\>The team’s first TigerData project. This project contains approximately 5000 files, including .csv, .pdf, and .mat files.\</description\>\`\`\`

## 

## 12.0 languages {#12.0-languages}

**Semantic Unit:** languages

**Semantic Components:**   
12.0a discoverable \= true  
12.0b trackingLevel \= ResourceRecord  
12.1 language  
12.1a inherited

**Definition:** The container element for all languages for a resource.

**Data Constraint:** Container

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<languages discoverable=”true” trackingLevel=”ResourceRecord”\>  
	\<language inherited=”false”\>en\</language\>  
	\<language inherited=”false”\>fr\</language\>  
\</languages\>\`\`\`

### 12.1 language {#12.1-language}

**Semantic Unit:** language

**Semantic Components:**   
12.1a inherited

**Definition:** Language declaration for the contents of the resource.

**Data Constraint:** xs:language

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Element repeatable up to 100 times. Utilizes the xs:language constraint.

**Links:** None

## 

## 13.0 storageCapacity {#13.0-storagecapacity}

**Semantic Unit:** storageCapacity

**Semantic Components:**   
13.0a [approved](#approved)  
13.0b inherited \= false  
13.0c discoverable \= false  
13.0d trackingLevel \= InternalUseOnly  
13.1 storageCapacitySetting  
13.1.1 size  
13.1.2 unit  
13.2 requestedValue  
13.2.1 size  
13.2.2 unit  
13.3 approvedValue  
13.3.1 size  
13.3.1 unit

**Definition:** The amount of storage allotted for the project (in logical byte units).

**Data Constraint:** Container

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** If no user request was received and no value has yet been approved, then this field may be empty.

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<storageCapacity approved="true" inherited="false" discoverable="false" trackingLevel="InternalUseOnly"\>  
\<storageCapacitySetting\>  
	\<size\>1\</size\>  
\<unit\>TB\</unit\>  
\<storageCapacitySetting\>  
\<requestedValue\>  
 		\<size\>500\</size\>  
\<unit\>GB\</unit\>  
 	\</requestedValue\>  
	\<approvedValue\>  
\<size\>1\</size\>  
\<unit\>TB\</unit\>  
	\</approvedValue\>  
 \</storageCapacity\>\`\`\`

### 13.1 storageCapacitySetting {#13.1-storagecapacitysetting}

**Semantic Unit:** storageCapacitySetting

**Semantic Components:**   
13.1.1 size  
13.1.2 unit

**Definition:** The current setting for storageCapacity (omitted until approved).

**Data Constraint:** Container

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** After approval, this value should be updated to match the approvedValue (13.3). Note: in rare cases, the current setting may later deviate from the approved value.

**Usage Notes:** None

**Links:** None

#### 13.1.1 size {#13.1.1-size}

**Semantic Unit:** size

**Semantic Components:** None

**Definition:** The numeric size of the storage quantity.

**Data Constraint:** xs:decimal

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

#### 13.1.2 unit {#13.1.2-unit}

**Semantic Unit:** unit

**Semantic Components:** None

**Definition:** The logical byte unit for the storage quantity.

**Data Constraint:** xs:string

Controlled vocabulary

* B  
* KB  
* MB  
* GB  
* TB  
* PB

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Controlled vocabulary definitions:

* B \- Bytes  
* KB \- Kilobytes  
* MB \- Megabytes  
* GB \- Gigabytes  
* TB \- Terabytes  
* PB \- Petabytes

**Links:** None

### 13.2 requestedValue {#13.2-requestedvalue}

**Semantic Unit:** requestedValue

**Semantic Components:**   
13.2.1 size  
13.2.2 unit

**Definition:** The requested value for storageCapacity field.

**Data Constraint:** Container

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Container is omitted if no user request was received.

**Usage Notes:** None

**Links:** None

#### 13.2.1 size {#13.2.1-size}

**Semantic Unit:** size

**Semantic Components:** None

**Definition:** The numeric size of the storage quantity.

**Data Constraint:** xs:decimal

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

#### 13.2.2 unit {#13.2.2-unit}

**Semantic Unit:** unit

**Semantic Components:** None

**Definition:** The logical byte unit for the storage quantity.

**Data Constraint:** xs:string

Controlled vocabulary

* B  
* KB  
* MB  
* GB  
* TB  
* PB

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Controlled vocabulary definitions:

* B \- Bytes  
* KB \- Kilobytes  
* MB \- Megabytes  
* GB \- Gigabytes  
* TB \- Terabytes  
* PB \- Petabytes

**Links:** None

### 13.3 approvedValue {#13.3-approvedvalue}

**Semantic Unit:** approvedValue

**Semantic Components:**   
13.1.1 size  
13.1.2 unit

**Definition:** The approved value for storageCapacity field.

**Data Constraint:** Container

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Container omitted if a system administrator has not yet approved it. Once approved, the approved attribute on the storageCapacity container (13.0a) should also be set to true.

**Usage Notes:** None

**Links:** None

#### 13.3.1 size {#13.3.1-size}

**Semantic Unit:** size

**Semantic Components:** None

**Definition:** The numeric size of the storage quantity.

**Data Constraint:** xs:decimal

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

#### 13.3.2 unit {#13.3.2-unit}

**Semantic Unit:** unit

**Semantic Components:** None

**Definition:** The logical byte unit for the storage quantity.

**Data Constraint:** xs:string

Controlled vocabulary

* B  
* KB  
* MB  
* GB  
* TB  
* PB

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Controlled vocabulary definitions:

* B \- Bytes  
* KB \- Kilobytes  
* MB \- Megabytes  
* GB \- Gigabytes  
* TB \- Terabytes  
* PB \- Petabytes

**Links:** None

## 

## 14.0 projectVisibility {#14.0-projectvisibility}

**Semantic Unit:** projectVisibility

**Semantic Components:**   
14.0a inherited  
14.0b discoverable \= false  
14.0c trackingLevel \= InternalUseOnly

**Definition:** The level of openness to allow for the project record.

**Data Constraint:** xs:string

Controlled vocabulary:

* Restricted (Visibility is restricted to those assigned roles on the resource)  
* Limited (Visibility is limited to TigerData users)  
* Open (Visibility is open to the general public)

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<projectVisibility inherited="true" discoverable="false" trackingLevel="InternalUseOnly"\>Limited\</projectVisibility\>\`\`\`

## 

## 15.0 storagePerformance {#15.0-storageperformance}

**Semantic Unit:** storagePerformance

**Semantic Components:**   
15.0a [approved](#approved)  
15.0b inherited  
15.0c discoverable \= false  
15.0d trackingLevel \= InternalUseOnly  
15.1 storagePerformanceSetting  
15.2 requestedValue  
15.3 approvedValue

**Definition:** The qualitative assignment for storage performance, i.e. storage tier.

**Data Constraint:** Container

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** If no user request was received and no value has yet been approved, then this container may be empty.

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<storagePerformance approved="true" inherited="true" discoverable="false" trackingLevel="InternalUseOnly"\>  
	\<storagePerformanceSetting\>Eco\</storagePerformanceSetting\>  
\<requestedValue\>Standard\</requestedValue\>  
\<approvedValue\>Eco\</approvedValue\>  
\</storagePerformance\>\`\`\`

### 15.1 storagePerformanceSetting {#15.1-storageperformancesetting}

**Semantic Unit:** storagePerformanceSetting

**Semantic Components:** None

**Definition:** The current setting for storagePerformance.

**Data Constraint:** xs:string

Controlled vocabulary:

* Eco  
* Standard  
* Premium

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Value is omitted until approved. After approval, this value should be updated to match the approved field (15.3). Note: in rare cases, the current setting may later deviate from the approved value.

**Usage Notes:** Controlled vocabulary definitions

* Eco \- The most economical storage tier available in TigerData (lowest cost and smallest carbon footprint). Appropriate for long-term/low-use data, i.e. cold storage. The typical implementation is an object store system, e.g. IBM Cloud Object Storage.  
* Standard \- The middle storage tier for TigerData, used as a default. Appropriate for data that is accessed occasionally but infrequently edited, i.e. cool storage. The typical implementation is a network attached storage system, e.g. Dell PowerScale.  
* Premium \- The most performant storage tier available in TigerData. Reserved for actively edited data that needs to be close to high performance computing systems, i.e. warm storage. The typical implementation is a cluster file system, e.g. IBM General Parallel File System

**Links:** None

### 15.2 requestedValue {#15.2-requestedvalue}

**Semantic Unit:** requestedValue

**Semantic Components:** None

**Definition:** The requested value for storagePerformance.

**Data Constraint:** xs:string

Controlled vocabulary:

* Eco  
* Standard  
* Premium

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Field is omitted if no user request was received.

**Usage Notes:** Controlled vocabulary definitions

* Eco \- The most economical storage tier available in TigerData (lowest cost and smallest carbon footprint). Appropriate for long-term/low-use data, i.e. cold storage. The typical implementation is an object store system, e.g. IBM Cloud Object Storage.  
* Standard \- The middle storage tier for TigerData, used as a default. Appropriate for data that is accessed occasionally but infrequently edited, i.e. cool storage. The typical implementation is a network attached storage system, e.g. Dell PowerScale.  
* Premium \- The most performant storage tier available in TigerData. Reserved for actively edited data that needs to be close to high performance computing systems, i.e. warm storage. The typical implementation is a cluster file system, e.g. IBM General Parallel File System

**Links:** None

### 15.3 approvedValue {#15.3-approvedvalue}

**Semantic Unit:** approvedValue

**Semantic Components:** None

**Definition:** The approved value for storagePerformance.

**Data Constraint:** xs:string

Controlled vocabulary:

* Eco  
* Standard  
* Premium

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Field is omitted if a system administrator has not yet approved it. Once approved, the approved attribute on the storagePerformance element (15.0a) should also be set to true.

**Usage Notes:** Controlled vocabulary definitions

* Eco \- The most economical storage tier available in TigerData (lowest cost and smallest carbon footprint). Appropriate for long-term/low-use data, i.e. cold storage. The typical implementation is an object store system, e.g. IBM Cloud Object Storage.  
* Standard \- The middle storage tier for TigerData, used as a default. Appropriate for data that is accessed occasionally but infrequently edited, i.e. cool storage. The typical implementation is a network attached storage system, e.g. Dell PowerScale.  
* Premium \- The most performant storage tier available in TigerData. Reserved for actively edited data that needs to be close to high performance computing systems, i.e. warm storage. The typical implementation is a cluster file system, e.g. IBM General Parallel File System

**Links:** None

## 

## 16.0 numberOfFiles {#16.0-numberoffiles}

**Semantic Unit:** numberOfFiles

**Semantic Components:**   
16.0a inherited  
16.0b discoverable \= false  
16.0c trackingLevel \= InternalUseOnly

**Definition:** The estimated number of files the project will incorporate.

**Data Constraint:** xs:string

Controlled vocabulary:

* Less than 10,000  
* 10k \- 100k  
* 100k \- 1mil  
* More than 1 million

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<numberOfFiles inherited="false" discoverable="false" trackingLevel="InternalUseOnly"\>Less than 10,000\</numberOfFiles\>\`\`\`

## 

## 17.0 hpc {#17.0-hpc}

**Semantic Unit:** hpc

**Semantic Components:**   
17.0a inherited  
17.0b discoverable \= false  
17.0c trackingLevel \= InternalUseOnly

**Definition:** Whether the project is expected to connect to high performance computing resources.

**Data Constraint:** xs:string

Controlled vocab:

* No  
* Yes  
* Not Sure

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<hpc inherited="true" discoverable="false" trackingLevel="InternalUseOnly"\>No\</hpc\>\`\`\`

## 

## 18.0 projectPurpose {#18.0-projectpurpose}

**Semantic Unit:** projectPurpose

**Semantic Components:**   
18.0a inherited  
18.0b discoverable \= true  
18.0c trackingLevel \= InternalUseOnly

**Definition:** The high-level category for the purpose of the project.

**Data Constraint:** xs:string

Controlled vocabulary:

* Research  
* Administrative  
* Library Archive

**Applicability:** Project

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<projectPurpose inherited="true" discoverable="true" trackingLevel="InternalUseOnly"\>Research\</projectPurpose\>\`\`\`

## 

## 19.0 provisionalProject {#19.0-provisionalproject}

**Semantic Unit:** provisionalProject

**Semantic Components:**   
19.0a inherited \= true  
19.0b discoverable \= true  
19.0c trackingLevel \= InternalUseOnly

**Definition:** Whether the project is provisional.

**Data Constraint:** xs:boolean

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<provisionalProject inherited="true" discoverable="true" trackingLevel="InternalUseOnly"\>false\</provisionalProject\>\`\`\`

## 

## 20.0 grantFunded {#20.0-grantfunded}

**Semantic Unit:** grantFunded

**Semantic Components:**   
20.0a inherited  
20.0b discoverable \= false  
20.0c trackingLevel \= InternalUseOnly

**Definition:** Whether a resource is grant funded.

**Data Constraint:** xs:boolean

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<grantFunded inherited="true" discoverable="false" trackingLevel="InternalUseOnly"\>true\</grantFunded\>\`\`\`

## 

## 21.0 fundingReferences {#21.0-fundingreferences}

**Semantic Unit:** fundingReferences

**Semantic Components:**   
21.0a discoverable \= true  
21.0b trackingLevel \= ResourceRecord  
21.1 fundingReference  
21.1a inherited  
21.1.1 funderName  
	21.1.1a xml:lang  
21.1.2 funderID  
21.1.2a [funderIDType](#funderidtype)  
21.1.2b [funderIDSchema](#funderidschema)  
21.1.3 awardNumber  
21.1.3a [awardURI](#awarduri)  
21.1.4 awardTitle  
21.1.4a xml:lang

**Definition:** The container element for all funding references for a resource.

**Data Constraint:** Container

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None 

**Usage Notes:** None

**Links:** Derived from the DataCite controlled vocabulary for [resourceTypeGeneral (v4.5+)](https://datacite-metadata-schema.readthedocs.io/en/4.5/properties/resourcetype/#a-resourcetypegeneral).

**Example:**   
\`\`\`\<fundingReferences discoverable=”true” trackingLevel=”ResourceRecord”\>  
	\<fundingReference inherited=”false”\>  
		\<funderName\>National Science Foundation\</funderName\>  
		\<funderID funderIDType=”ROR” funderIDSchema=”https://ror.org/”\>https://ror.org/021nxhr62\</funderID\>  
		\<awardNumber awardURI=”https://www.nsf.gov/awardsearch/”\>NSF-DMR-2118860\</awardNumber\>  
		\<awardTitle xml:lang=”en”\>\</awardTitle\>  
	\</fundingReference\>  
\</fundingReferences\>\`\`\`

### 21.1 fundingReference {#21.1-fundingreference}

**Semantic Unit:** fundingReference

**Semantic Components:**   
21.1a inherited  
21.1.1 funderName  
21.1.1a xml:lang  
21.1.2 funderID  
21.1.2a [funderIDType](#funderidtype)  
21.1.2b [funderIDSchema](#funderidschema)  
21.1.3 awardNumber  
21.1.3a [awardURI](#awarduri)  
21.1.4 awardTitle  
21.1.4a xml:lang

**Definition:** Information about financial support (funding) for the resource being registered.

**Data Constraint:** Container

**Applicability:** Projects, Items

**Obligation:** Required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** This container can be repeated up to 100 times.

**Links:** Derived from the DataCite definitions for [FundingReference (v4.5+)](https://datacite-metadata-schema.readthedocs.io/en/4.5/properties/fundingreference/).

#### 21.1.1 funderName {#21.1.1-fundername}

**Semantic Unit:** funderName

**Semantic Components:**  
21.1.1a xml:lang

**Definition:** Records the name of the funding provider.

**Data Constraint:** xs:string

String length: 1 \- 1000

**Applicability:** Projects, Items

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

#### 21.1.2 funderID {#21.1.2-funderid}

**Semantic Unit:** funderID

**Semantic Components:**   
21.1.2a [funderIDType](#funderidtype)  
21.1.2b [funderIDSchema](#funderidschema)

**Definition:** Records the unique identifier for the funding provider.

**Data Constraint:** xs:string

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

#### 21.1.3 awardNumber {#21.1.3-awardnumber}

**Semantic Unit:** awardNumber

**Semantic Components:**   
21.1.3a [awardURI](#awarduri)

**Definition:** Records the award number for the fundingReference container.

**Data Constraint:** xs:string

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

#### 21.1.4 awardTitle {#21.1.4-awardtitle}

**Semantic Unit:** awardTitle

**Semantic Components:**   
21.1.4a xml:lang

**Definition:** Records the title for the fundingReference container.

**Data Constraint:** xs:string

String length: 1 \- 1000

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

## 

## 22.0 dates {#22.0-dates}

**Semantic Unit:** dates

**Semantic Components:**   
22.0a discoverable \= true  
22.0b trackingLevel \= ResourceRecord  
22.1 startDate  
22.1a inherited  
22.2 endDate  
22.2a inherited  
22.3 retirementDate  
22.3a inherited  
22.4 publicationDate  
22.4a inherited  
22.5 otherDate  
22.5a inherited  
22.5b [dateType](#datetype)  
22.5c [dateInformation](#dateinformation)

**Definition:** The container element for all date elements that apply to a resource.

**Data Constraint:** Container

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Unlike provenance records, these date fields are all discoverable and tracked in the resource record. If the dates element is present, then it should contain at least one sub-element.

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<dates discoverable=”true” trackingLevel=”ResourceRecord”\>  
	\<startDate inherited=”false”\>2024-11-05\</startDate\>  
	\<endDate inherited=”false”\>2025-11-05\</endDate\>  
	\<retirementDate inherited=”true”\>2027-12-31\</retirementDate\>  
	\<publicationDate inherited=”true”\>2025-12-31\</publicationDate\>  
\<otherDate inherited=”true” dateType=”Created” dateInformation=”The date the data for this project was first created”\>2024-04-15\</otherDate\>  
\</dates\>\`\`\`

### 22.1 startDate {#22.1-startdate}

**Semantic Unit:** startDate

**Semantic Components:**   
22.1a inherited

**Definition:** The date when the resource became, or will become, active (may be estimated).

**Data Constraint:** xs:date

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** The value must not be chronologically earlier than that of the approvalDateTime subfield under the submission field. Unlike provenance records, this date field is discoverable and tracked in the resource record.

**Usage Notes:** None

**Links:** None

### 22.2 endDate {#22.2-enddate}

**Semantic Unit:** endDate

**Semantic Components:**   
22.2a inherited

**Definition:** The date when the resource became, or will become, inactive (may be estimated).

**Data Constraint:** xs:date

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** The value must not be chronologically earlier than that of startDate, nor later than that of retirementDate. Unlike provenance records, this date field is discoverable and tracked in the resource record.

**Usage Notes:** None

**Links:** None

### 22.3 retirementDate {#22.3-retirementdate}

**Semantic Unit:** retirementDate

**Semantic Components:**   
22.3a inherited \= true

**Definition:** The date when the resource became, or will become, no longer useful to the primary users (may be estimated).

**Data Constraint:** xs:date

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** The value must not be chronologically earlier than that of endDate, nor later than that of the approvalDateTime subfield under the retirement field. Unlike provenance records, this date field is discoverable and tracked in the resource record.

**Usage Notes:** None

**Links:** None

### 22.4 publicationDate {#22.4-publicationdate}

**Semantic Unit:** publicationDate

**Semantic Components:**   
22.4a inherited \= true

**Definition:** The date when the resource became, or will become, publicly available (may be estimated).

**Data Constraint:** xs:date

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** The value must not be chronologically earlier than that of startDate, nor later than that of the approvalDateTime subfield under the publication field. Unlike provenance records, this date field is discoverable and tracked in the resource record.

**Usage Notes:** None

**Links:** None

### 22.5 otherDate {#22.5-otherdate}

**Semantic Unit:** otherDate

**Semantic Components:**   
22.5a inherited  
22.5b [dateType](#datetype)  
22.5c [dateInformation](#dateinformation)

**Definition:** A date or date range relevant to the resource, not captured by any other date field.

**Data Constraint:** xs:date

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Unlike provenance records, this date field is discoverable and tracked in the resource record.

**Usage Notes:** This element can be repeated up to 100 times.

**Links:** None

## 

## 23.0 resourceType {#23.0-resourcetype}

**Semantic Unit:** resourceType

**Semantic Components:**  
23.0a [resourceTypeGeneral](#resourcetypegeneral)  
23.0b inherited  
23.0c discoverable \= true  
23.0d trackingLevel \= ResourceRecord

**Definition:** A simple description of the resource, using controlled terms for TigerData resources

**Data Constraint:** xs:string

Controlled vocabulary:

* TigerData Project  
* TigerData Item

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Controlled vocabulary definitions:

* TigerData Project \- Standard resourceType value for TigerData Projects (not Items). Intended to be used in conjunction with a resourceTypeGeneral value of "Project"  
* TigerData Item \- Standard resourceType value for TigerData Items (not Projects). The value for resourceTypeGeneral may be anything other than "Project"

**Links:** Derived from the DataCite controlled vocabulary for [resourceTypeGeneral (v4.5+)](https://datacite-metadata-schema.readthedocs.io/en/4.5/properties/resourcetype/#a-resourcetypegeneral)

**Example:**   
\`\`\`\<resourceType resourceTypeGeneral="Project" inherited="false" discoverable="true" trackingLevel="ResourceRecord"\>TigerData Project  
\</resourceType\>\`\`\`

## 24.0 licenses {#24.0-licenses}

**Semantic Unit:** licenses

**Semantic Components:**   
24.0a discoverable \= true  
24.0b trackingLevel \= ResourceRecord  
24.1 license  
24.1a [licenseURI](#licenseuri)  
24.1b [licenseID](#licenseid)  
24.1c [licenseIDScheme](#licenseidscheme)  
24.1d [licenseIDSchemeURI](#licenseidschemeuri)

**Definition:** The container element for all licenses for a resource.

**Data Constraint:** Container

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<license\>  
\<license licenseURI=”https://creativecommons.org/licenses/by/4.0/” licenseID=”CC BY 4.0” licenseIDScheme=”” licenseIDSchemeURI=””\>Creative Commons Attribution 4.0 International\</license\>  
\<license licenseURI=”https://opensource.org/license/MIT” licenseID=”MIT” licenseIDScheme=”” licenseIDSchemeURI=””\>The MIT License\</license\>  
\</licenses\>\`\`\`

### 24.1 license {#24.1-license}

**Semantic Unit:** license

**Semantic Components:**   
24.1a [licenseURI](#licenseuri)  
24.1b [licenseID](#licenseid)  
24.1c [licenseIDScheme](#licenseidscheme)  
24.1d [licenseIDSchemeURI](#licenseidschemeuri)

**Definition:** Specific rights granted for copying and reusing the resource.

**Data Constraint:** xs:string

Controlled vocabulary:

* Creative Commons Public Domain Dedication 1.0 Universal  
* Creative Commons Attribution 4.0 International  
* Creative Commons Attribution-Sharealike 4.0 International  
* Creative Commons Attribution-Noncommercial 4.0 International  
* Creative Commons Attribution-Noncommercial-Sharealike 4.0 International  
* Creative Commons Attribution-Noderivatives 4.0 International  
* Creative Commons Attribution-Noncommercial-Noderivatives 4.0 International  
* The MIT License

**Applicability:** Projects, Items

**Obligation:** Required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Element is repeatable up to 100 times.

**Links:** None

## 

## 25.0 dataUseAgreement {#25.0-datauseagreement}

**Semantic Unit:** dataUseAgreement

**Semantic Components:**   
25.0a inherited  
25.0b discoverable \= false  
25.0c trackingLevel \= InternalUseOnly

**Definition:** Whether a data use agreement applies to the project.

**Data Constraint:** xs:boolean

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** If the value is true, then at least one duaReference field (26.1) must be filled. If any subproject or item contained in a project has a duaReference (26.1), then this field should be set to true.

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<dataUseAgreement inherited="true" discoverable="false" trackingLevel="InternalUseOnly"\>true\</dataUseAgreement\>\`\`\`

## 

## 26.0 duaReferences {#26.0-duareferences}

**Semantic Unit:** duaReferences

**Semantic Components:**   
26.0a discoverable \= true  
26.0b trackingLevel \= ResourceRecord  
26.1 duaReference  
26.1a inherited  
26.1.1 grantorName  
26.1.1a xml:lang  
26.1.2 duaID  
26.1.2a [duaURI](#duauri)  
26.1.3 duaTitle  
26.1.3a xml:lang

**Definition:** The container element for all DUA references for a resource. DUA is short for Data Use Agreement.

**Data Constraint:** Container

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<duaReferences discoverable=”true” trackingLevel=”ResourceRecord”\>  
	\<duaReference inherited=”true”\>  
		\<grantorName xml:lang=”en”\>\</grantorName\>  
		\<duaID duaURI=””\>\</duaID\>  
		\<duaTitle xml:lang=”en”\>\</duaTitle\>  
	\</duaReference\>  
\</duaReferences\>\`\`\`

### 26.1 duaReference {#26.1-duareference}

**Semantic Unit:** duaReference

**Semantic Components:**   
26.1a inherited  
26.1.1 grantorName  
26.1.1a xml:lang  
26.1.2 duaID  
26.1.2a [duaURI](#duauri)  
26.1.3 duaTitle  
26.1.3a xml:lang

**Definition:** Information about formal agreements governing data use pertaining to the resource. DUA is short for Data Use Agreement.

**Data Constraint:** Container

**Applicability:** Projects, Items

**Obligation:** Required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Container can be repeated up to 100 times

**Links:** None

#### 26.1.1 grantorName {#26.1.1-grantorname}

**Semantic Unit:** grantorName

**Semantic Components:**   
26.1.1a xml:lang

**Definition:** Records the name of the DUA grantor.

**Data Constraint:** xs:string

String length: 1 \- 1000

**Applicability:** Projects, Items

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

#### 26.1.2 duaID {#26.1.2-duaid}

**Semantic Unit:** duaID

**Semantic Components:**   
26.1.2a [duaURI](#duauri)

**Definition:** Records the identifier for the DUA.

**Data Constraint:** xs:string

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

#### 26.1.3 duaTitle {#26.1.3-duatitle}

**Semantic Unit:** duaTitle

**Semantic Components:**   
26.1.3a xml:lang

**Definition:** Records the title for the DUA

**Data Constraint:** xs:string

String length: 1 \- 1000

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

## 

## 27.0 keywords {#27.0-keywords}

**Semantic Unit:** keywords

**Semantic Components:**   
27.0a discoverable \= true  
27.0b trackingLevel \= ResourceRecord  
27.1 keyword  
27.1a [subjectScheme](#subjectscheme)  
27.1b [subjectSchemeURI](#subjectschemeuri)  
27.1c [valueURI](#valueuri)  
27.1d [classificationCode](#classificationcode)  
27.1e inherited

**Definition:** The container element for all keywords for a resource.

**Data Constraint:** Container

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<keywords discoverable=”true” trackingLevel=”ResourceRecord”\>  
\<keyword subjectScheme=”Library of Congress Subject Headings (LCSH)” subjectSchemeURI=”https://id.loc.gov/authorities/subjects.html” valueURI=”http://id.loc.gov/authorities/subjects/sh2015001855”\>data curation\</keyword\>  
\<keyword subjectScheme=”ANZSRC FoR” subjectSchemeURI=”https://www.abs.gov.au/statistics/classifications/australian-and-new-zealand-standard-research-classification-anzsrc/latest-release” classificationCode=”4605”\>data management and data science\</keyword\>  
\</keywords\>

### 27.1 keyword {#27.1-keyword}

**Semantic Unit:** keyword

**Semantic Components:**   
27.1a [subjectScheme](#subjectscheme)  
27.1b [subjectSchemeURI](#subjectschemeuri)  
27.1c [valueURI](#valueuri)  
27.1d [classificationCode](#classificationcode)  
27.1e inherited

**Definition:** Tags for subject headings, content types, or other keywords.

**Data Constraint:** xs:string

**Applicability:** Projects, Items

**Obligation:** Required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Element repeatable up to 100 times.

**Links:** None

## 

## 28.0 relations {#28.0-relations}

**Semantic Unit:** relations

**Semantic Components:**   
28.0a discoverable \= true  
28.0b trackingLevel \= ResourceRecord  
28.1 relation  
28.1a [relatedIDType](#relatedidtype)  
28.1b [relationType](#relationtype)  
28.1c [relatedMetadataScheme](#relatedmetadatascheme)  
28.1d [relatedMetadataSchemeURI](#relatedmetadataschemeuri)  
28.1e [relatedMetadataSchemeType](#relatedmetadataschemetype)  
28.1f [resourceTypeGeneral](#resourcetypegeneral)  
28.1g inherited

**Definition:** The container element for all relations for a resource.

**Data Constraint:** Container

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<relations discoverable=”true” trackingLevel=”ResourceRecord”\>  
\<relation relatedIDType=”” relatedMetadataScheme=”” relatedMetadataSchemeURI=”” relatedMetadataSchemeType=”” resourceTypeGeneral=”” inherited=”false”\>\</relation\>  
\</relations\>\`\`\`

### 28.1 relation {#28.1-relation}

**Semantic Unit:** relation

**Semantic Components:**   
28.1a [relatedIDType](#relatedidtype)  
28.1b [relationType](#relationtype)  
28.1c [relatedMetadataScheme](#relatedmetadatascheme)  
28.1d [relatedMetadataSchemeURI](#relatedmetadataschemeuri)  
28.1e [relatedMetadataSchemeType](#relatedmetadataschemetype)  
28.1f [resourceTypeGeneral](#resourcetypegeneral)  
28.1g inherited

**Definition:** Specifies a related TigerData project or item, a published paper, or any other digital object.

**Data Constraint:** xs:string

String length: 1 \- 1000

**Applicability:** Projects, Items

**Obligation:** Required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Element is repeatable up to 100 times

**Links:** None

## 

## 29.0 extendedMetadataSchemas {#29.0-extendedmetadataschemas}

**Semantic Unit:** extendedMetadataSchemas

**Semantic Components:**   
29.0a discoverable \= false  
29.0b trackingLevel \= InternalUseOnly  
29.1 extendedMetadataSchema  
29.1a inherited

**Definition:** The container element for all extended metadata schemas for a resource.

**Data Constraint:** Container

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:** 

### 29.1 extendedMetadataSchema {#29.1-extendedmetadataschema}

**Semantic Unit:** extendedMetadataSchema

**Semantic Components:**   
29.1a inherited

**Definition:** An indication of which TigerData supported metadata schemas should apply to a resource.

**Data Constraint:** xs:string

String length: 1 \- 1000

**Applicability:** Projects, Items

**Obligation:** Required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** This element can be repeated up to 100 times.

**Links:** None

## 

## 30.0 projectProvenance {#30.0-projectprovenance}

**Semantic Unit:** projectProvenance

**Semantic Components:**   
30.1 submission  
30.1a inherited \= false  
30.1b discoverable \= false  
30.1c trackingLevel \= InternalUseOnly  
30.1.1 requestedBy  
30.1.1a [userID](#userid)  
30.1.1b [userIDType](#useridtype) \= NetID  
30.1.1.1 netID  
30.1.1.2 orcid  
30.1.1.3 fullName  
30.1.1.4 givenName  
30.1.1.5 familyName  
30.1.1.6 nameDate  
30.1.1.7 alternativeNameIdentifer  
30.1.1.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.1.1.7b [schemeURI](#schemeuri)  
30.1.2 requestDateTime  
30.1.3 approvedBy  
30.1.3a [userID](#userid)  
30.1.3b [userIDType](#useridtype) \= NetID  
30.1.3.1 netID  
30.1.3.2 orcid  
30.1.3.3 fullName  
30.1.3.4 givenName  
30.1.3.5 familyName  
30.1.3.6 nameDate  
30.1.3.7 alternativeNameIdentifer  
30.1.3.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.1.3.7b [schemeURI](#schemeuri)  
30.1.4 approvedDateTime  
30.1.5 deniedBy  
30.1.5a [userID](#userid)  
30.1.5b [userIDType](#useridtype) \= NetID  
30.1.5.1 netID  
30.1.5.2 orcid  
30.1.5.3 fullName  
30.1.5.4 givenName  
30.1.5.5 familyName  
30.1.5.6 nameDate  
30.1.5.7 alternativeNameIdentifer  
30.1.5.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.1.5.7b [schemeURI](#schemeuri)  
30.1.6 denialDateTime  
30.1.7 eventNote  
30.1.7.1 noteBy  
30.1.7.1a [userID](#userid)  
30.1.7.1b [userIDType](#useridtype) \= NetID  
30.1.7.1.1 netID  
30.1.7.1.2 orcid  
30.1.7.1.3 fullName  
30.1.7.1.4 givenName  
30.1.7.1.5 familyName  
30.1.7.1.6 nameDate  
30.1.7.1.7 alternativeNameIdentifer  
30.1.7.1.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.1.7.1.7b [schemeURI](#schemeuri)  
30.1.7.2 noteDateTime  
30.1.7.3 eventType  
30.1.7.4 message  
30.1.7.4a xml:lang  
30.2 revisions  
30.2a discoverable \= false  
30.2b trackingLevel \= InternalUseOnly  
30.2.1 revision  
30.2.1a inherited  
30.2.1.1 requestedBy  
30.2.1.1a [userID](#userid)  
30.2.1.1b [userIDType](#useridtype) \= NetID  
30.2.1.1.1 netID  
30.2.1.1.2 orcid  
30.2.1.1.3 fullName  
30.2.1.1.4 givenName  
30.2.1.1.5 familyName  
30.2.1.1.6 nameDate  
30.2.1.1.7 alternativeNameIdentifer  
30.2.1.1.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.2.1.1.7b [schemeURI](#schemeuri)  
30.2.1.2 requestDateTime  
30.2.1.3 approvedBy  
30.2.3a [userID](#userid)  
30.2.3b [userIDType](#useridtype) \= NetID  
30.2.3.1 netID  
30.2.3.2 orcid  
30.2.3.3 fullName  
30.2.3.4 givenName  
30.2.3.5 familyName  
30.2.3.6 nameDate  
30.2.3.7 alternativeNameIdentifer  
30.2.3.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.2.3.7b s[chemeURI](#schemeuri)  
30.2.1.4 approvedDateTime  
30.2.1.5 deniedBy  
30.2.1.5a [userID](#userid)  
30.2.1.5b [userIDType](#useridtype) \= NetID  
30.2.1.5.1 netID  
30.2.1.5.2 orcid  
30.2.1.5.3 fullName  
30.2.1.5.4 givenName  
30.2.1.5.5 familyName  
30.2.1.5.6 nameDate  
30.2.1.5.7 alternativeNameIdentifer  
30.2.1.5.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.2.1.5.7b [schemeURI](#schemeuri)  
30.2.1.6 denialDateTime  
30.2.1.7 eventNote  
30.2.1.7.1 noteBy  
30.2.1.7.1a [userID](#userid)  
30.2.1.7.1b [userIDType](#useridtype) \= NetID  
30.2.1.7.1.1 netID  
30.2.1.7.1.2 orcid  
30.2.1.7.1.3 fullName  
30.2.1.7.1.4 givenName  
30.2.1.7.1.5 familyName  
30.2.1.7.1.6 nameDate  
30.2.1.7.1.7 alternativeNameIdentifer  
30.2.1.7.1.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.2.1.7.1.7b [schemeURI](#schemeuri)  
30.2.1.7.2 noteDateTime  
30.2.1.7.3 eventType  
30.2.1.7.4 message  
30.2.1.7.4a xml:lang  
30.3 retirement  
30.3a inherited \= true  
30.3b discoverable \= false  
30.3c trackingLevel \= InternalUseOnly  
30.3.1 requestedBy  
30.3.1a [userID](#userid)  
30.3.1b [userIDType](#useridtype) \= NetID  
30.3.1.1 netID  
30.3.1.2 orcid  
30.3.1.3 fullName  
30.3.1.4 givenName  
30.3.1.5 familyName  
30.3.1.6 nameDate  
30.3.1.7 alternativeNameIdentifer  
30.3.1.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.3.1.7b [schemeURI](#schemeuri)  
30.3.2 requestDateTime  
30.3.3 approvedBy  
30.3.1.3a [userID](#userid)  
30.3.1.3b [userIDType](#useridtype) \= NetID  
30.3.1.3.1 netID  
30.3.1.3.2 orcid  
30.3.1.3.3 fullName  
30.3.1.3.4 givenName  
30.3.1.3.5 familyName  
30.3.1.3.6 nameDate  
30.3.1.3.7 alternativeNameIdentifer  
30.3.1.3.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.3.1.3.7b [schemeURI](#schemeuri)  
30.3.4 approvedDateTime  
30.3.5 deniedBy  
30.3.5a [userID](#userid)  
30.3.5b [userIDType](#useridtype) \= NetID  
30.3.5.1 netID  
30.3.5.2 orcid  
30.3.5.3 fullName  
30.3.5.4 givenName  
30.3.5.5 familyName  
30.3.5.6 nameDate  
30.3.5.7 alternativeNameIdentifer  
30.3.5.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.3.5.7b [schemeURI](#schemeuri)  
30.3.6 denialDateTime  
30.3.7 eventNote  
30.3.7.1 noteBy  
30.3.7.1a [userID](#userid)  
30.3.7.1b [userIDType](#useridtype) \= NetID  
30.3.7.1.1 netID  
30.3.7.1.2 orcid  
30.3.7.1.3 fullName  
30.3.7.1.4 givenName  
30.3.7.1.5 familyName  
30.3.7.1.6 nameDate  
30.3.7.1.7 alternativeNameIdentifer  
30.3.7.1.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.3.7.1.7b [schemeURI](#schemeuri)  
30.3.7.2 noteDateTime  
30.3.7.3 eventType  
30.3.7.4 message  
30.3.7.4a xml:lang  
30.4 publication  
30.4a inherited \= true  
30.4b discoverable \= false  
30.4c trackingLevel \= InternalUseOnly  
30.4.1 requestedBy  
30.4.1a [userID](#userid)  
30.4.1b [userIDType](#useridtype) \= NetID  
30.4.1.1 netID  
30.4.1.2 orcid  
30.4.1.3 fullName  
30.4.1.4 givenName  
30.4.1.5 familyName  
30.4.1.6 nameDate  
30.4.1.7 alternativeNameIdentifer  
30.4.1.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.4.1.7b [schemeURI](#schemeuri)  
30.4.2 requestDateTime  
30.4.3 approvedBy  
30.4.3a [userID](#userid)  
30.4.3b [userIDType](#useridtype) \= NetID  
30.4.3.1 netID  
30.4.3.2 orcid  
30.4.3.3 fullName  
30.4.3.4 givenName  
30.4.3.5 familyName  
30.4.3.6 nameDate  
30.4.3.7 alternativeNameIdentifer  
30.4.3.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.4.3.7b [schemeURI](#schemeuri)  
30.4.4 approvedDateTime  
30.4.5 deniedBy  
30.4.5a [userID](#userid)  
30.4.5b [userIDType](#useridtype) \= NetID  
30.4.5.1 netID  
30.4.5.2 orcid  
30.4.5.3 fullName  
30.4.5.4 givenName  
30.4.5.5 familyName  
30.4.5.6 nameDate  
30.4.5.7 alternativeNameIdentifer  
30.4.5.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.4.5.7b [schemeURI](#schemeuri)  
30.4.6 denialDateTime  
30.4.7 eventNote  
30.4.7.1 noteBy  
30.4.7.1a [userID](#userid)  
30.4.7.1b [userIDType](#useridtype) \= NetID  
30.4.7.1.1 netID  
30.4.7.1.2 orcid  
30.4.7.1.3 fullName  
30.4.7.1.4 givenName  
30.4.7.1.5 familyName  
30.4.7.1.6 nameDate  
30.4.7.1.7 alternativeNameIdentifer  
30.4.7.1.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.4.7.1.7b [schemeURI](#schemeuri)  
30.4.7.2 noteDateTime  
30.4.7.3 eventType  
30.4.7.4 message  
30.4.7.4a xml:lang  
30.5 status  
30.5a inherited  
30.5b discoverable \= true  
30.5c trackingLevel \= InternalUseOnly  
30.6 schemaVersion  
30.6a inherited  
30.6b discoverable \= true  
30.6c trackingLevel \= InternalUseOnly

**Definition:** The container element for all TigerData project provenance fields.

**Data Constraint:** Container

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<projectProvenance\>  
\<submission inherited=”false” discoverable=”false” trackingLevel=”InternalUseOnly”\>  
		\<requestedBy userID=”hb0344” userIDType=”NetID”\>  
			\<netID\>hb0344\</netID\>  
			\<orcid\>https://orcid.org/0000-0003-2346-2876\</orcid\>  
			\<fullName\>Burns, Halle\</fullName\>  
			\<givenName\>Halle\</givenName\>  
			\<familyName\>Burns\</familyName\>  
			\<nameDate\>2024-10-29\</nameDate\>  
\<alternativeNameIdentifier nameIdentifierScheme=“Scopus” schemeURI=“https://www.scopus.com/authid/detail.uri?authorId=57450022500”\>57450022500  
\</alternativeNameIdentifier\>  
		\</requestedBy\>  
		\<requestedDate\>2024-10-29\</requestedDate\>  
		\<approvedBy userID="cbentler" userIDType="NetID"\>\</approvedBy\>  
		\<approvedDate\>2024-11-01\</approvedDate\>  
		\<eventNote\>  
			\<noteBy userID="cbentler" userIDType="NetID"\>\</noteBy\>  
			\<noteDateTime\>2024-11-01-06:00\</noteDateTime\>  
			\<eventType\>Collection\</eventType\>  
\<message\>Project requested on 2024-10-29. Approved as is. Project created in system on 2024-11-01. MFAID assigned at this time\</message\>  
		\<eventNote\>  
	\</submission\>  
\<status inherited=”false” discoverable=”true” trackingLevel=”InternalUseOnly\>Approved\</status\>  
\<schemaVersion inherited=”false” discoverable=”true” trackingLevel=”InternalUseOnly\>0.7\</schemaVersion\>  
\</projectProvenance\>\`\`\`

NOTE: The submission (30.1), revision (30.2.1), retirement (30.3), publication (30.4), status (30.5), and schemaVersion (30.6) elements all contain the same sub-elements and documentation. Instead of listing and repeating the full documentation for each field, the sub-elements documentation will only appear under submission (30.1).

### 30.1 submission {#30.1-submission}

**Semantic Unit:** submission

**Semantic Components:**   
30.1a inherited \= false  
30.1b discoverable \= false  
30.1c trackingLevel \= InternalUseOnly  
30.1.1 requestedBy  
30.1.1a [userID](#userid)  
30.1.1b [userIDType](#useridtype) \= NetID  
30.1.1.1 netID  
30.1.1.2 orcid  
30.1.1.3 fullName  
30.1.1.4 givenName  
30.1.1.5 familyName  
30.1.1.6 nameDate  
30.1.1.7 alternativeNameIdentifer  
30.1.1.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.1.1.7b [schemeURI](#schemeuri)  
30.1.2 requestDateTime  
30.1.3 approvedBy  
30.1.3a [userID](#userid)  
30.1.3b [userIDType](#useridtype) \= NetID  
30.1.3.1 netID  
30.1.3.2 orcid  
30.1.3.3 fullName  
30.1.3.4 givenName  
30.1.3.5 familyName  
30.1.3.6 nameDate  
30.1.3.7 alternativeNameIdentifer  
30.1.3.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.1.3.7b [schemeURI](#schemeuri)  
30.1.4 approvedDateTime  
30.1.5 deniedBy  
30.1.5a [userID](#userid)  
30.1.5b [userIDType](#useridtype) \= NetID  
30.1.5.1 netID  
30.1.5.2 orcid  
30.1.5.3 fullName  
30.1.5.4 givenName  
30.1.5.5 familyName  
30.1.5.6 nameDate  
30.1.5.7 alternativeNameIdentifer  
30.1.5.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.1.5.7b [schemeURI](#schemeuri)  
30.1.6 denialDateTime  
30.1.7 eventNote  
30.1.7.1 noteBy  
30.1.7.1a [userID](#userid)  
30.1.7.1b [userIDType](#useridtype) \= NetID  
30.1.7.1.1 netID  
30.1.7.1.2 orcid  
30.1.7.1.3 fullName  
30.1.7.1.4 givenName  
30.1.7.1.5 familyName  
30.1.7.1.6 nameDate  
30.1.7.1.7 alternativeNameIdentifer  
30.1.7.1.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.1.7.1.7b [schemeURI](#schemeuri)  
30.1.7.2 noteDateTime  
30.1.7.3 eventType  
30.1.7.4 message  
30.1.7.4a xml:lang

**Definition:** A record of a project’s initial submission.

**Data Constraint:** Container

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

#### 30.1.1 requestedBy {#30.1.1-requestedby}

**Semantic Unit:** requestedBy

**Semantic Components:**   
30.1.1a [userID](#userid)  
30.1.1b [userIDType](#useridtype) \= NetID  
30.1.1.1 netID  
30.1.1.2 orcid  
30.1.1.3 fullName  
30.1.1.4 givenName  
30.1.1.5 familyName  
30.1.1.6 nameDate  
30.1.1.7 alternativeNameIdentifer  
30.1.1.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.1.1.7b [schemeURI](#schemeuri)

**Definition:** The person who made the request. May be an eligible Data Sponsor, a System Administrator, or a technical service account

**Data Constraint:** Container

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

##### 30.1.1.1 netID {#30.1.1.1-netid}

**Semantic Unit:** netID

**Semantic Components:** None

**Definition:** The University NetID (also called the OIT NetID) is the name or user-id that identifies a person to a computer system or electronic service at Princeton.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** If this netID sub-element is included, its value should match that of the 6.0a userID attribute.

**Usage Notes:** None

**Links:** 

##### 30.1.1.2 orcid {#30.1.1.2-orcid}

**Semantic Unit:** orcid

**Semantic Components:** None

**Definition:** The ORCID ID URL for the person in a given role, if available and if verified as valid against the ORCID API upon entry.

**Data Constraint:** xs:anyURI

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Must be validated against the ORCID API

**Usage Notes:** None

**Links:** 

##### 30.1.1.3 fullName {#30.1.1.3-fullname}

**Semantic Unit:** fullName

**Semantic Components:** None

**Definition:** The full name of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Automatically generated. Must be verified in the format family-comma-given and matching the corresponding given and family name fields.

**Usage Notes:** None

**Links:** None

##### 30.1.1.4 givenName {#30.1.1.4-givenname}

**Semantic Unit:** givenName

**Semantic Components:** None

**Definition:** The given name(s) of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** 

**Usage Notes:** If the person has multiple given names, then all should be included in this field, along with any suffixes.

**Links:** None

##### 30.1.1.5 familyName {#30.1.1.5-familyname}

**Semantic Unit:** familyName

**Semantic Components:** None

**Definition:** The family name(s) of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** 

**Usage Notes:** If the person has multiple family names, then all should be included in this field.

**Links:** None

##### 30.1.1.6 nameDate {#30.1.1.6-namedate}

**Semantic Unit:** nameDate

**Semantic Components:** None

**Definition:** The date at which the name metadata was recorded, using the ISO 8601 date format (YYYY-MM-DD).

**Data Constraint:** xs:date

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

##### 30.1.1.7 alternativeNameIdentifer {#30.1.1.7-alternativenameidentifer}

**Semantic Unit:** alternativeNameIdentifier

**Semantic Components:**   
6.7a [nameIdentifierScheme](#nameidentifierscheme)  
6.7b [schemeURI](#schemeuri)

**Definition:** Records alternative (non-ORCID) identifier(s) for the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

#### 30.1.2 requestDateTime {#30.1.2-requestdatetime}

**Semantic Unit:** requestDateTime

**Semantic Components:** None

**Definition:** The date and time the request was made.

**Data Constraint:** xs:dateTime

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** 

**Usage Notes:** Include the time zone at the location of the host institution. Princeton University is in the Eastern Time Zone (UTC-05:00 during Eastern Standard Time and UTC-04:00 during Eastern Daylight Time).

**Links:** None

#### 30.1.3 approvedBy {#30.1.3-approvedby}

**Semantic Unit:** approvedBy

**Semantic Components:**   
30.1.3a [userID](#userid)  
30.1.3b [userIDType](#useridtype) \= NetID  
30.1.3.1 netID  
30.1.3.2 orcid  
30.1.3.3 fullName  
30.1.3.4 givenName  
30.1.3.5 familyName  
30.1.3.6 nameDate  
30.1.3.7 alternativeNameIdentifer  
30.1.3.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.1.3.7b [schemeURI](#schemeuri)

**Definition:** The person who approved the request. Should be a System Administrator.

**Data Constraint:** Container

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

##### 30.1.3.1 netID {#30.1.3.1-netid}

**Semantic Unit:** netID

**Semantic Components:** None

**Definition:** The University NetID (also called the OIT NetID) is the name or user-id that identifies a person to a computer system or electronic service at Princeton.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** If this netID sub-element is included, its value should match that of the 6.0a userID attribute.

**Usage Notes:** None

**Links:** 

##### 30.1.3.2 orcid {#30.1.3.2-orcid}

**Semantic Unit:** orcid

**Semantic Components:** None

**Definition:** The ORCID ID URL for the person in a given role, if available and if verified as valid against the ORCID API upon entry.

**Data Constraint:** xs:anyURI

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Must be validated against the ORCID API

**Usage Notes:** None

**Links:** 

##### 30.1.3.3 fullName {#30.1.3.3-fullname}

**Semantic Unit:** fullName

**Semantic Components:** None

**Definition:** The full name of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Automatically generated. Must be verified in the format family-comma-given and matching the corresponding given and family name fields.

**Usage Notes:** None

**Links:** None

##### 30.1.3.4 givenName {#30.1.3.4-givenname}

**Semantic Unit:** givenName

**Semantic Components:** None

**Definition:** The given name(s) of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** 

**Usage Notes:** If the person has multiple given names, then all should be included in this field, along with any suffixes.

**Links:** None

##### 30.1.3.5 familyName {#30.1.3.5-familyname}

**Semantic Unit:** familyName

**Semantic Components:** None

**Definition:** The family name(s) of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** 

**Usage Notes:** If the person has multiple family names, then all should be included in this field.

**Links:** None

##### 30.1.3.6 nameDate {#30.1.3.6-namedate}

**Semantic Unit:** nameDate

**Semantic Components:** None

**Definition:** The date at which the name metadata was recorded, using the ISO 8601 date format (YYYY-MM-DD).

**Data Constraint:** xs:date

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

##### 30.1.3.7 alternativeNameIdentifer {#30.1.3.7-alternativenameidentifer}

**Semantic Unit:** alternativeNameIdentifier

**Semantic Components:**   
6.7a [nameIdentifierScheme](#nameidentifierscheme)  
6.7b [schemeURI](#schemeuri)

**Definition:** Records alternative (non-ORCID) identifier(s) for the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

#### 30.1.4 approvedDateTime {#30.1.4-approveddatetime}

**Semantic Unit:** approvedDateTime

**Semantic Components:** None

**Definition:** The date and time the request was approved.

**Data Constraint:** xs:dateTime

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Include the time zone at the location of the host institution. Princeton University is in the Eastern Time Zone (UTC-05:00 during Eastern Standard Time and UTC-04:00 during Eastern Daylight Time).

**Links:** None

#### 30.1.5 deniedBy {#30.1.5-deniedby}

**Semantic Unit:** deniedBy

**Semantic Components:**   
30.1.5a [userID](#userid)  
30.1.5b [userIDType](#useridtype) \= NetID  
30.1.5.1 netID  
30.1.5.2 orcid  
30.1.5.3 fullName  
30.1.5.4 givenName  
30.1.5.5 familyName  
30.1.5.6 nameDate  
30.1.5.7 alternativeNameIdentifer  
30.1.5.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.1.5.7b [schemeURI](#schemeuri)

**Definition:** The person who denied the request. Should be a System Administrator.

**Data Constraint:** Container

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

##### 30.1.5.1 netID {#30.1.5.1-netid}

**Semantic Unit:** netID

**Semantic Components:** None

**Definition:** The University NetID (also called the OIT NetID) is the name or user-id that identifies a person to a computer system or electronic service at Princeton.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** If this netID sub-element is included, its value should match that of the 6.0a userID attribute.

**Usage Notes:** None

**Links:** 

##### 30.1.5.2 orcid {#30.1.5.2-orcid}

**Semantic Unit:** orcid

**Semantic Components:** None

**Definition:** The ORCID ID URL for the person in a given role, if available and if verified as valid against the ORCID API upon entry.

**Data Constraint:** xs:anyURI

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Must be validated against the ORCID API

**Usage Notes:** None

**Links:** 

##### 30.1.5.3 fullName {#30.1.5.3-fullname}

**Semantic Unit:** fullName

**Semantic Components:** None

**Definition:** The full name of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Automatically generated. Must be verified in the format family-comma-given and matching the corresponding given and family name fields.

**Usage Notes:** None

**Links:** None

##### 30.1.5.4 givenName {#30.1.5.4-givenname}

**Semantic Unit:** givenName

**Semantic Components:** None

**Definition:** The given name(s) of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** 

**Usage Notes:** If the person has multiple given names, then all should be included in this field, along with any suffixes.

**Links:** None

##### 30.1.5.5 familyName {#30.1.5.5-familyname}

**Semantic Unit:** familyName

**Semantic Components:** None

**Definition:** The family name(s) of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** 

**Usage Notes:** If the person has multiple family names, then all should be included in this field.

**Links:** None

##### 30.1.5.6 nameDate {#30.1.5.6-namedate}

**Semantic Unit:** nameDate

**Semantic Components:** None

**Definition:** The date at which the name metadata was recorded, using the ISO 8601 date format (YYYY-MM-DD).

**Data Constraint:** xs:date

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

##### 30.1.5.7 alternativeNameIdentifer {#30.1.5.7-alternativenameidentifer}

**Semantic Unit:** alternativeNameIdentifier

**Semantic Components:**   
6.7a [nameIdentifierScheme](#nameidentifierscheme)  
6.7b [schemeURI](#schemeuri)

**Definition:** Records alternative (non-ORCID) identifier(s) for the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

#### 30.1.6 denialDateTime {#30.1.6-denialdatetime}

**Semantic Unit:** denialDateTime

**Semantic Components:** None

**Definition:** The date and time the request was denied.

**Data Constraint:** xs:dateTime

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Include the time zone at the location of the host institution. Princeton University is in the Eastern Time Zone (UTC-05:00 during Eastern Standard Time and UTC-04:00 during Eastern Daylight Time).

**Links:** None

#### 30.1.7 eventNote {#30.1.7-eventnote}

**Semantic Unit:** eventNote

**Semantic Components:**   
30.1.7.1 noteBy  
30.1.7.1a [userID](#userid)  
30.1.7.1b [userIDType](#useridtype) \= NetID  
30.1.7.1.1 netID  
30.1.7.1.2 orcid  
30.1.7.1.3 fullName  
30.1.7.1.4 givenName  
30.1.7.1.5 familyName  
30.1.7.1.6 nameDate  
30.1.7.1.7 alternativeNameIdentifer  
30.1.7.1.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.1.7.1.7b [schemeURI](#schemeuri)  
30.1.7.2 noteDate  
30.1.7.3 eventType  
30.1.7.4 message  
30.2.7.4a xml:lang

**Definition:** A supplementary record of noteworthy details for a given provenance event.

**Data Constraint:** Container

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** This container can be repeated up to 100 times. Intended to be retained in a running log of all noteworthy events.

**Links:** None

##### 30.1.7.1 noteBy {#30.1.7.1-noteby}

**Semantic Unit:** noteBy

**Semantic Components:**   
30.1.7.1a [userID](#userid)  
30.1.7.1b [userIDType](#useridtype) \= NetID  
30.1.7.1.1 netID  
30.1.7.1.2 orcid  
30.1.7.1.3 fullName  
30.1.7.1.4 givenName  
30.1.7.1.5 familyName  
30.1.7.1.6 nameDate  
30.1.7.1.7 alternativeNameIdentifer  
30.1.7.1.7a [nameIdentifierScheme](#nameidentifierscheme)  
30.1.7.1.7b [schemeURI](#schemeuri)

**Definition:** The person making the note. Should be a System Administrator.

**Data Constraint:** Container

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

###### *30.1.7.1.1 netID* {#30.1.7.1.1-netid}

**Semantic Unit:** netID

**Semantic Components:** None

**Definition:** The University NetID (also called the OIT NetID) is the name or user-id that identifies a person to a computer system or electronic service at Princeton.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** If this netID sub-element is included, its value should match that of the 6.0a userID attribute.

**Usage Notes:** None

**Links:** 

###### *30.1.7.1.2 orcid* {#30.1.7.1.2-orcid}

**Semantic Unit:** orcid

**Semantic Components:** None

**Definition:** The ORCID ID URL for the person in a given role, if available and if verified as valid against the ORCID API upon entry.

**Data Constraint:** xs:anyURI

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Must be validated against the ORCID API

**Usage Notes:** None

**Links:** 

###### *30.1.7.1.3 fullName* {#30.1.7.1.3-fullname}

**Semantic Unit:** fullName

**Semantic Components:** None

**Definition:** The full name of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Automatically generated. Must be verified in the format family-comma-given and matching the corresponding given and family name fields.

**Usage Notes:** None

**Links:** None

###### *30.1.7.1.4 givenName* {#30.1.7.1.4-givenname}

**Semantic Unit:** givenName

**Semantic Components:** None

**Definition:** The given name(s) of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** 

**Usage Notes:** If the person has multiple given names, then all should be included in this field, along with any suffixes.

**Links:** None

###### *30.1.7,1.5 familyName* {#30.1.7,1.5-familyname}

**Semantic Unit:** familyName

**Semantic Components:** None

**Definition:** The family name(s) of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** 

**Usage Notes:** If the person has multiple family names, then all should be included in this field.

**Links:** None

###### *30.1.7.1.6 nameDate* {#30.1.7.1.6-namedate}

**Semantic Unit:** nameDate

**Semantic Components:** None

**Definition:** The date at which the name metadata was recorded, using the ISO 8601 date format (YYYY-MM-DD).

**Data Constraint:** xs:date

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

###### *30.1.7.1.7 alternativeNameIdentifer* {#30.1.7.1.7-alternativenameidentifer}

**Semantic Unit:** alternativeNameIdentifier

**Semantic Components:**   
6.7a [nameIdentifierScheme](#nameidentifierscheme)  
6.7b [schemeURI](#schemeuri)

**Definition:** Records alternative (non-ORCID) identifier(s) for the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

##### 30.1.7.2 noteDateTime {#30.1.7.2-notedatetime}

**Semantic Unit:** noteDateTime

**Semantic Components:** None

**Definition:** The date and time the note was made.

**Data Constraint:** xs:dateTime

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Include the time zone at the location of the host institution. Princeton University is in the Eastern Time Zone (UTC-05:00 during Eastern Standard Time and UTC-04:00 during Eastern Daylight Time).

**Links:** None

##### 30.1.7.3 eventType {#30.1.7.3-eventtype}

**Semantic Unit:** eventType

**Semantic Components:** None

**Definition:** A general category label for the event note.

**Data Constraint:** xs:string

Controlled vocabulary:

* Collection  
* Directory  
* Quota  
* Tier  
* Sponsor  
* Denial  
* Other

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Controlled vocabulary definitions  
:

* Collection \- Event note records the assignment of or change to the project's Mediaflux collection ID  
* Directory \- Event note pertains to the project's directory or mount point  
* Quota \- Event note pertains to the project's quota settings in Mediaflux  
* Tier \- Event note pertains to the project's storage tier  
* Sponsor \- Event note records any changes to the project's Data Sponsor  
* Denial \- Event note explains the denial of the project request  
* Other \- The event note is not otherwise classified

**Links:** None

##### 30.1.7.4 message {#30.1.7.4-message}

**Semantic Unit:** message

**Semantic Components:**   
30.1.7.4a xml:lang

**Definition:** The plain-language message contents of the event note

**Data Constraint:** xs:string

String length: 1 \- 1000

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

### 30.2 revisions {#30.2-revisions}

**Semantic Unit:** revisions

**Semantic Components:**   
30.2a discoverable \= false  
30.2b trackingLevel \= InternalUseOnly  
30.2.1 revision  
30.2.1a inherited  
30.2.1.1 requestedBy  
30.2.1.1a userID  
30.2.1.1b userIDType \= NetID  
30.2.1.1.1 netID  
30.2.1.1.2 orcid  
30.2.1.1.3 fullName  
30.2.1.1.4 givenName  
30.2.1.1.5 familyName  
30.2.1.1.6 nameDate  
30.2.1.1.7 alternativeNameIdentifer  
30.2.1.1.7a nameIdentifierScheme  
30.2.1.1.7b schemeURI  
30.2.1.2 requestDateTime  
30.2.1.3 approvedBy  
30.2.1.3a userID  
30.2.1.3b userIDType \= NetID  
30.2.1.3.1 netID  
30.2.1.3.2 orcid  
30.2.1.3.3 fullName  
30.2.1.3.4 givenName  
30.2.1.3.5 familyName  
30.2.1.3.6 nameDate  
30.2.1.3.7 alternativeNameIdentifer  
30.2.1.3.7a nameIdentifierScheme  
30.2.1.3.7b schemeURI  
30.2.1.4 approvedDateTime  
30.2.1.5 deniedBy  
30.2.1.5a userID  
30.2.1.5b userIDType \= NetID  
30.2.1.5.1 netID  
30.2.1.5.2 orcid  
30.2.1.5.3 fullName  
30.2.1.5.4 givenName  
30.2.1.5.5 familyName  
30.2.1.5.6 nameDate  
30.2.1.5.7 alternativeNameIdentifer  
30.2.1.5.7a nameIdentifierScheme  
30.2.1.5.7b schemeURI  
30.2.1.6 denialDateTime  
30.2.1.7 eventNote  
30.2.1.7.1 noteBy  
30.2.7.1a userID  
30.2.7.1b userIDType  
30.2.7.1.1 netID  
30.2.7.1.2 orcid  
30.2.7.1.3 fullName  
30.2.7.1.4 givenName  
30.2.7.1.5 familyName  
30.2.7.1.6 nameDate  
30.2.7.1.7 alternativeNameIdentifer  
30.2.7.1.7a nameIdentifierScheme  
30.2.7.1.7b schemeURI  
30.2.1.7.2 noteDateTime  
30.2.1.7.3 eventType  
30.2.1.7.4 message  
30.2.1.7.4a xml:lang

**Definition:** The container element for all revision records.

**Data Constraint:** Container

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

*NOTE: See 30.1 for full sub-element documentation*

#### 30.2.1 revision {#30.2.1-revision}

**Semantic Unit:** revision

**Semantic Components:**   
30.2.1a inherited  
30.2.1.1 requestedBy  
30.2.1.1a userID  
30.2.1.1b userIDType \= NetID  
30.2.1.1.1 netID  
30.2.1.1.2 orcid  
30.2.1.1.3 fullName  
30.2.1.1.4 givenName  
30.2.1.1.5 familyName  
30.2.1.1.6 nameDate  
30.2.1.1.7 alternativeNameIdentifer  
30.2.1.1.7a nameIdentifierScheme  
30.2.1.1.7b schemeURI  
30.2.1.2 requestDateTime  
30.2.1.3 approvedBy  
30.2.1.3a userID  
30.2.1.3b userIDType \= NetID  
30.2.1.3.1 netID  
30.2.1.3.2 orcid  
30.2.1.3.3 fullName  
30.2.1.3.4 givenName  
30.2.1.3.5 familyName  
30.2.1.3.6 nameDate  
30.2.1.3.7 alternativeNameIdentifer  
30.2.1.3.7a nameIdentifierScheme  
30.2.1.3.7b schemeURI  
30.2.1.4 approvedDateTime  
30.2.1.5 deniedBy  
30.2.1.5a userID  
30.2.1.5b userIDType \= NetID  
30.2.1.5.1 netID  
30.2.1.5.2 orcid  
30.2.1.5.3 fullName  
30.2.1.5.4 givenName  
30.2.1.5.5 familyName  
30.2.1.5.6 nameDate  
30.2.1.5.7 alternativeNameIdentifer  
30.2.1.5.7a nameIdentifierScheme  
30.2.1.5.7b schemeURI  
30.2.1.6 denialDateTime  
30.2.1.7 eventNote  
30.2.1.7.1 noteBy  
30.2.1.7.1 noteBy  
30.2.7.1a userID  
30.2.7.1b userIDType \= NetID  
30.2.7.1.1 netID  
30.2.7.1.2 orcid  
30.2.7.1.3 fullName  
30.2.7.1.4 givenName  
30.2.7.1.5 familyName  
30.2.7.1.6 nameDate  
30.2.7.1.7 alternativeNameIdentifer  
30.2.7.1.7a nameIdentifierScheme  
30.2.7.1.7b schemeURI  
30.2.1.7.2 noteDateTime  
30.2.1.7.3 eventType  
30.2.1.7.4 message  
30.2.1.7.4a xml:lang

**Definition:** A record of a major revision to an active project.

**Data Constraint:** Container

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Container repeatable up to 100 times.

**Links:** None

*NOTE: See 30.1 for full sub-element documentation*

### 30.3 retirement {#30.3-retirement}

**Semantic Unit:** retirement

**Semantic Components:**   
30.3a inherited \= true  
30.3b discoverable \= false  
30.3c trackingLevel \= InternalUseOnly  
30.3.1 requestedBy  
30.3.1a userID  
30.3.1b userIDType \= NetID  
30.3.1.1 netID  
30.3.1.2 orcid  
30.3.1.3 fullName  
30.3.1.4 givenName  
30.3.1.5 familyName  
30.3.1.6 nameDate  
30.3.1.7 alternativeNameIdentifer  
30.3.1.7a nameIdentifierScheme  
30.3.1.7b schemeURI  
30.3.2 requestDateTime  
30.3.3 approvedBy  
30.3.3a userID  
30.3.3b userIDType \= NetID  
30.3.3.1 netID  
30.3.3.2 orcid  
30.3.3.3 fullName  
30.3.3.4 givenName  
30.3.3.5 familyName  
30.3.3.6 nameDate  
30.3.3.7 alternativeNameIdentifer  
30.3.3.7a nameIdentifierScheme  
30.3.3.7b schemeURI  
30.3.4 approvedDateTime  
30.3.5 deniedBy  
30.3.5a userID  
30.3.5b userIDType \= NetID  
30.3.5.1 netID  
30.3.5.2 orcid  
30.3.5.3 fullName  
30.3.5.4 givenName  
30.3.5.5 familyName  
30.3.5.6 nameDate  
30.3.5.7 alternativeNameIdentifer  
30.3.5.7a nameIdentifierScheme  
30.3.5.7b schemeURI  
30.3.6 denialDateTime  
30.3.7 eventNote  
30.3.7.1 noteBy  
30.3.7.1a userID  
30.3.7.1b userIDType \= NetID  
30.3.7.1.1 netID  
30.3.7.1.2 orcid  
30.3.7.1.3 fullName  
30.3.7.1.4 givenName  
30.3.7.1.5 familyName  
30.3.7.1.6 nameDate  
30.3.7.1.7 alternativeNameIdentifer  
30.3.7.1.7a nameIdentifierScheme  
30.3.7.1.7b schemeURI  
30.3.7.2 noteDateTime  
30.3.7.3 eventType  
30.3.7.4 message  
30.3.7.4a xml:lang

**Definition:** A record of a project’s retirement.

**Data Constraint:** Container

**Applicability:** Project

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

*NOTE: See 30.1 for full sub-element documentation*

### 30.4 publication {#30.4-publication}

**Semantic Unit:** publication

**Semantic Components:**   
30.4a inherited \= true  
30.4b discoverable \= false  
30.4c trackingLevel \= InternalUseOnly  
30.4.1 requestedBy  
30.4.1a userID  
30.4.1b userIDType \= NetID  
30.4.1.1 netID  
30.4.1.2 orcid  
30.4.1.3 fullName  
30.4.1.4 givenName  
30.4.1.5 familyName  
30.4.1.6 nameDate  
30.4.1.7 alternativeNameIdentifer  
30.4.1.7a nameIdentifierScheme  
30.4.1.7b schemeURI  
30.4.2 requestDateTime  
30.4.3 approvedBy  
30.4.3a userID  
30.4.3b userIDType \= NetID  
30.4.3.1 netID  
30.4.3.2 orcid  
30.4.3.3 fullName  
30.4.3.4 givenName  
30.4.3.5 familyName  
30.4.3.6 nameDate  
30.4.3.7 alternativeNameIdentifer  
30.4.3.7a nameIdentifierScheme  
30.4.3.7b schemeURI  
30.4.4 approvedDateTime  
30.4.5 deniedBy  
30.4.5a userID  
30.4.5b userIDType \= NetID  
30.4.5.1 netID  
30.4.5.2 orcid  
30.4.5.3 fullName  
30.4.5.4 givenName  
30.4.5.5 familyName  
30.4.5.6 nameDate  
30.4.5.7 alternativeNameIdentifer  
30.4.5.7a nameIdentifierScheme  
30.4.5.7b schemeURI  
30.4.6 denialDateTime  
30.4.7 eventNote  
30.4.7.1 noteBy  
30.4.7.1a userID  
30.4.7.1b userIDType \= NetID  
30.4.7.1.1 netID  
30.4.7.1.2 orcid  
30.4.7.1.3 fullName  
30.4.7.1.4 givenName  
30.4.7.1.5 familyName  
30.4.7.1.6 nameDate  
30.4.7.1.7 alternativeNameIdentifer  
30.4.7.1.7a nameIdentifierScheme  
30.4.7.1.7b schemeURI  
30.4.7.2 noteDateTime  
30.4.7.3 eventType  
30.4.7.4 message  
30.4.7.4a xml:lang

**Definition:** A record of a project’s publication.

**Data Constraint:** Container

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

*NOTE: See 30.1 for full sub-element documentation*

### 30.5 status {#30.5-status}

**Semantic Unit:** status

**Semantic Components:**   
30.5a inherited  
30.5b discoverable \= true  
30.5c trackingRecord \= InternalUseOnly

**Definition:** The current status of the project.

**Data Constraint:** xs:string

Controlled vocabulary:

* Active  
* Approved  
* Pending  
* Published   
* Retired

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Controlled vocabulary definitions:

* Active \- The project is live: approved and available to users. Applies if the submission field has complete approvedBy and approvalDateTime subfields, the frontend has confirmed the project's collection ID in Mediaflux, and the project has been neither retired nor published  
* Approved \- The project has been approved, but it is not yet active. Applies if the submission field has complete approvedBy and approvalDateTime subfields, but the frontend has not yet confirmed the project's collection ID in Mediaflux  
* Pending \- The project has been submitted, but not yet approved. Applies if the submission field lacks complete approvedBy or approvalDateTime subfields.  
* Published \- The project has been published. Applies if the the publication field has complete approvedBy and approvalDateTime subfields  
* Retired \- The project has been retired and is no longer active. Applies if the retirement field has complete approvedBy and approvalDateTime subfields

**Links:** None

### 30.6 schemaVersion {#30.6-schemaversion}

**Semantic Unit:** schemaVersion

**Semantic Components:**   
30.6a inherited  
30.6b discoverable \= true  
30.6c trackingLevel \= InternalUseOnly

**Definition:** The version of the TigerData Standard Metadata Schema used.

**Data Constraint:** xs:string

String length: 1 \- 1000

**Applicability:** Projects

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

# 

# TigerData Data Definitions (ItemFields) {#tigerdata-data-definitions-(itemfields)}

## 1.0 itemID {#1.0-itemid}

**Semantic Unit:** itemID

**Semantic Components:**   
1.0a [itemIDType](#itemidtype) \= MFAID  
1.0b inherited \= false  
1.0c discoverable \= false  
1.0d trackingLevel \= InternalUseOnly

**Definition:** The unique identifier for the item. TigerData items use Mediaflux Asset IDs as their primary identifiers.

**Data Constraint:** xs:integer

Integer minimum: 1  
Integer maximum: 9223372036854775807

**Applicability:** Items

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Standard type used for Mediaflux Asset ID (MFAID) values. Per Mediaflux Concepts v 0.10 (2021), asset IDs must be in the range \[1,9223372036854775807\]. If an item also has any other IDs, they all should be included under alternativeIDs

**Links:** None

**Example:** 

## 2.0 alternativeIDs {#2.0-alternativeids-1}

**Semantic Unit:** alternativeIDs

**Semantic Components:**   
2.0a discoverable \= true  
2.0b trackingLevel \= ResourceRecord  
2.1 alternativeID  
	2.1a [alternativeIDType](#alternativeidtype)  
	2.1b inherited

**Definition:** The container element for all alternative IDs for a resource

**Data Constraint:** Container

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<alternativeIDs discoverable=”true” trackingLevel=”ResourceRecord”\>  
\<alternativeID alternativeIDType="DOI" inherited="false"\>10.60803/s609-0022\</alternativeID\>  
\</alternativeIDs\>\`\`\`

### 2.1 alterativeID {#2.1-alterativeid-1}

**Semantic Unit:** alternativeID

**Semantic Components:**   
2.1a [alternativeIDType](#alternativeidtype)  
2.1b inherited

**Definition:** An alternative identifier for the resource (not the standard TigerData projectID or itemID).

**Data Constraint:** xs:string

**Applicability:** Projects, Items

**Obligation:** Required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Element is repeatable up to 100 times

**Links:** None

## 

## 3.0 parentProject {#3.0-parentproject-1}

**Semantic Unit:** parentProject

**Semantic Components:**   
3.0a [projectIDType](#projectidtype) \= DOI  
3.0b inherited  
3.0c discoverable \= true  
3.0d trackingLevel \= ResourceRecord

**Definition:** The ID of the project to which the resource belongs directly. Takes precedence over any IsChildOf relations to other projects.

**Data Constraint:** xs:string

Pattern: 10\\.\\d{4,9}\\/\[\\S\]+\[^-\_\!:;,.?/\\\\\\s\]

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Only DOIs, as created by Princeton’s instance of DataCite Fabrica, will be allowed in this unit. DOIs are minted automatically when individuals request TigerData project space. Princeton’s TigerData DOI prefix is 10.60803.

Standard type used for DOI values (just the prefix and suffix; not a full URL). DOI is short for Digital Object Identifier. Applies a pattern aligned with ISO 26324:2022, allowing any suffix that doesn't have whitespace and doesn't end with unexpected punctuation

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<parentProject projectIDType="DOI" inherited="false" discoverable="true" trackingLevel="ResourceRecord"\>10.60803/89s3-0023\</projectID\>\`\`\`

## 

## 4.0 dataUsers {#4.0-datausers}

**Semantic Unit:** dataUsers

**Semantic Components:**   
4.0a trackingLevel \= ResourceRecord  
4.1 dataUser  
4.1a [userID](#userid)  
4.1b [userIDType](#useridtype) \= NetID  
4.1c [readOnly](#readonly)  
4.1d inherited  
4.1e discoverable  
4.1.1 netID  
4.1.2 orcid  
4.1.3 fullName  
4.1.4 givenName  
4.1.5 familyName  
4.1.6 nameDate  
4.1.7 alternativeNameIdentifer  
4.1.7a [nameIdentifierScheme](#nameidentifierscheme)  
4.1.7b [schemeURI](#schemeuri)

**Definition:** The container element for all data users of a resource.

**Data Constraint:** Container

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<dataUsers trackingLevel=”ResourceRecord”\>  
\<dataUser userID="hb0344" userIDType="NetID" readOnly=“false” discoverable="true" inherited="true"\>  
		\<netID\>hb0344\</netID\>  
		\<orcid\>https://orcid.org/0000-0003-2346-2876\</orcid\>  
		\<fullName\>Burns, Halle\</fullName\>  
		\<givenName\>Halle\</givenName\>  
		\<familyName\>Burns\</familyName\>  
		\<nameDate\>2024-10-29\</nameDate\>  
\<alternativeNameIdentifier nameIdentifierScheme=“Scopus” schemeURI=“[https://www.scopus.com/authid/detail.uri?authorId=57450022500](https://www.scopus.com/authid/detail.uri?authorId=57450022500)”\>57450022500\</alternativeNameIdentifier\>  
\</dataUser\>  
\<dataUser userID="mjc12" userIDType="NetID" readOnly=“false” discoverable="true" inherited="true"\>  
		\<netID\>mjc12\</netID\>  
		\<orcid\>https://orcid.org/0000-0001-9317-7056\</orcid\>  
		\<fullName\>Chandler, Matt\</fullName\>  
		\<givenName\>Matt\</givenName\>  
		\<familyName\>Chandler\</familyName\>  
		\<nameDate\>2024-11-05\</nameDate\>  
\<alternativeNameIdentifier nameIdentifierScheme=“Scopus” schemeURI=“https://www.webofscience.com/wos/author/record/AGR-7086-2022”\>AGR-7086-2022\</alternativeNameIdentifier\>  
\</dataUser\>  
\</dataUsers\>\`\`\`

Also valid:  
\`\`\`\<dataUsers trackingLevel=”ResourceRecord”\>  
\<dataUser userID="hb0344" userIDType="NetID" readOnly=“false” discoverable="true" inherited="true"\>\</dataUser\>  
\<dataUser userID="mjc12" userIDType="NetID" readOnly=“false” discoverable="true" inherited="true"\>\</dataUser\>  
\</dataUsers\>\`\`\`

### 4.1 dataUser {#4.1-datauser}

**Semantic Unit:** dataUser

**Semantic Unit:** dataManager

**Semantic Components:**   
4.1a [userID](#userid)  
4.1b [userIDType](#useridtype) \= NetID  
4.1c [readOnly](#readonly)  
4.1d inherited  
4.1e discoverable  
4.1.1 netID  
4.1.2 orcid  
4.1.3 fullName  
4.1.4 givenName  
4.1.5 familyName  
4.1.6 nameDate  
4.1.7 alternativeNameIdentifer  
4.1.7a [nameIdentifierScheme](#nameidentifierscheme)  
4.1.7b [schemeURI](#schemeuri)

**Definition:** The person who manages the day-to-day activities for the project

**Data Constraint:** See Usage Notes

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:**   
This unit will contain either:

* The highest level attributes (6.0a-6.0e) and a blank field  
* The accompanying sub-elements  
* Both

**Links:** None

#### 4.1.1 netID {#4.1.1-netid}

**Semantic Unit:** netID

**Semantic Components:** None

**Definition:** The University NetID (also called the OIT NetID) is the name or user-id that identifies a person to a computer system or electronic service at Princeton.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** If this netID sub-element is included, its value should match that of the 6.0a userID attribute.

**Usage Notes:** None

**Links:** 

#### 4.1.2 orcid {#4.1.2-orcid}

**Semantic Unit:** orcid

**Semantic Components:** None

**Definition:** The ORCID ID URL for the person in a given role, if available and if verified as valid against the ORCID API upon entry.

**Data Constraint:** anyURI

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Must be validated against the ORCID API

**Usage Notes:** None

**Links:** 

#### 4.1.3 fullName {#4.1.3-fullname}

**Semantic Unit:** fullName

**Semantic Components:** None

**Definition:** The full name of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Automatically generated. Must be verified in the format family-comma-given and matching the corresponding given and family name fields.

**Usage Notes:** None

**Links:** None

#### 4.1.4 givenName {#4.1.4-givenname}

**Semantic Unit:** givenName

**Semantic Components:** None

**Definition:** The given name(s) of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** 

**Usage Notes:** If the person has multiple given names, then all should be included in this field, along with any suffixes.

**Links:** None

#### 4.1.5 familyName {#4.1.5-familyname}

**Semantic Unit:** familyName

**Semantic Components:** None

**Definition:** The family name(s) of the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** 

**Usage Notes:** If the person has multiple family names, then all should be included in this field.

**Links:** None

#### 4.1.6 nameDate {#4.1.6-namedate}

**Semantic Unit:** nameDate

**Semantic Components:** None

**Definition:** The date at which the name metadata was recorded, using the ISO 8601 date format (YYYY-MM-DD).

**Data Constraint:** xs:date

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

#### 4.1.7 alternativeNameIdentifer {#4.1.7-alternativenameidentifer}

**Semantic Unit:** alternativeNameIdentifier

**Semantic Components:**   
4.1.7a [nameIdentifierScheme](#nameidentifierscheme)  
4.1.7b [schemeURI](#schemeuri)

**Definition:** Records alternative (non-ORCID) identifier(s) for the person in a given role.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

## 

## 5.0 title {#5.0-title}

**Semantic Unit:** title

**Semantic Components:**   
5.0a xml:lang  
5.0b inherited \= false  
5.0b discoverable \= true  
5.0d trackingLevel \= ResourceRecord

**Definition:** A plain-language title for the resource.

**Data Constraint:** xs:string

String length: 1 \- 1000

**Applicability:** Projects, Items

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<title xml:lang="en" inherited="false" discoverable="true" trackingLevel="ResourceRecord"\>Test Project 1\</title\>\`\`\`

## 

## 6.0 description {#6.0-description}

**Semantic Unit:** description

**Semantic Components:**   
6.0a xml:lang  
6.0b inherited \= false  
6.0b discoverable \= true  
6.0d trackingLevel \= ResourceRecord

**Definition:** A plain-language description of the resource and/or its contents.

**Data Constraint:** xs:string

String length: 1 \- 1000

**Applicability:** Projects, Items

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<description xml:lang="en" inherited="false" discoverable="true" trackingLevel="ResourceRecord"\>The team’s first TigerData project. This project contains approximately 5000 files, including .csv, .pdf, and .mat files.\</description\>\`\`\`

## 

## 7.0 resourceType {#7.0-resourcetype}

**Semantic Unit:** resourceType

**Semantic Components:**  
7.0a [resourceTypeGeneral](#resourcetypegeneral)  
7.0b inherited  
7.0c discoverable \= true  
7.0d trackingLevel \= ResourceRecord

**Definition:** A simple description of the resource, using controlled terms for TigerData resources

**Data Constraint:** xs:string

Controlled vocabulary:

* TigerData Project  
* TigerData Item

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Controlled vocabulary definitions:

* TigerData Project \- Standard resourceType value for TigerData Projects (not Items). Intended to be used in conjunction with a resourceTypeGeneral value of "Project"  
* TigerData Item \- Standard resourceType value for TigerData Items (not Projects). The value for resourceTypeGeneral may be anything other than "Project"

**Links:** Derived from the DataCite controlled vocabulary for [resourceTypeGeneral (v4.5+)](https://datacite-metadata-schema.readthedocs.io/en/4.5/properties/resourcetype/#a-resourcetypegeneral)

**Example:**   
\`\`\`\<resourceType resourceTypeGeneral="Project" inherited="false" discoverable="true" trackingLevel="ResourceRecord"\>TigerData Project  
\</resourceType\>\`\`\`

## 

## 8.0 keywords {#8.0-keywords}

**Semantic Unit:** keywords

**Semantic Components:**   
8.0a discoverable \= true  
8.0b trackingLevel \= ResourceRecord  
8.1 keyword  
8.1a [subjectScheme](#subjectscheme)  
8.1b [subjectSchemeURI](#subjectschemeuri)  
8.1c [valueURI](#valueuri)  
8.1d [classificationCode](#classificationcode)  
8.1e inherited

**Definition:** The container element for all keywords for a resource.

**Data Constraint:** Container

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:** 

### 8.1 keyword {#8.1-keyword}

**Semantic Unit:** keyword

**Semantic Components:**   
8.1a [subjectScheme](#subjectscheme)  
8.1b [subjectSchemeURI](#subjectschemeuri)  
8.1c [valueURI](#valueuri)  
8.1d [classificationCode](#classificationcode)  
8.1e inherited

**Definition:** Tags for subject headings, content types, or other keywords.

**Data Constraint:** xs:string

**Applicability:** Projects, Items

**Obligation:** Required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Element repeatable up to 100 times.

**Links:** None

## 

## 9.0 relations {#9.0-relations}

**Semantic Unit:** relations

**Semantic Components:**   
9.0a discoverable \= true  
9.0b trackingLevel \= ResourceRecord  
9.1 relation  
9.1a [relatedIDType](#relatedidtype)  
9.1b [relationType](#relationtype)  
9.1c [relatedMetadataScheme](#relatedmetadatascheme)  
9.1d [relatedMetadataSchemeURI](#relatedmetadataschemeuri)  
9.1e [relatedMetadataSchemeType](#relatedmetadataschemetype)  
9.1f [resourceTypeGeneral](#resourcetypegeneral)  
9.1g inherited

**Definition:** The container element for all relations for a resource.

**Data Constraint:** Container

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:** 

### 9.1 relation {#9.1-relation}

**Semantic Unit:** relation

**Semantic Components:**   
9.1a [relatedIDType](#relatedidtype)  
9.1b [relationType](#relationtype)  
9.1c [relatedMetadataScheme](#relatedmetadatascheme)  
9.1d [relatedMetadataSchemeURI](#relatedmetadataschemeuri)  
9.1e [relatedMetadataSchemeType](#relatedmetadataschemetype)  
9.1f [resourceTypeGeneral](#resourcetypegeneral)  
9.1g inherited

**Definition:** Specifies a related TigerData project or item, a published paper, or any other digital object.

**Data Constraint:** xs:string

String length: 1 \- 1000

**Applicability:** Projects, Items

**Obligation:** Required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Element is repeatable up to 100 times

**Links:** None

## 

## 10.0 extendedMetadataSchemas {#10.0-extendedmetadataschemas}

**Semantic Unit:** extendedMetadataSchemas

**Semantic Components:**   
10.0a discoverable \= false  
10.0b trackingLevel \= InternalUseOnly  
10.1 extendedMetadataSchema  
10.1a inherited

**Definition:** The container element for all extended metadata schemas for a resource.

**Data Constraint:** Container

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:** 

### 10.1 extendedMetadataSchema {#10.1-extendedmetadataschema}

**Semantic Unit:** extendedMetadataSchema

**Semantic Components:**   
10.1a inherited

**Definition:** An indication of which TigerData supported metadata schemas should apply to a resource.

**Data Constraint:** xs:string

String length: 1 \- 1000

**Applicability:** Projects, Items

**Obligation:** Required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** This element can be repeated up to 100 times.

**Links:** None

## 

## 11.0 languages {#11.0-languages}

**Semantic Unit:** languages

**Semantic Components:**   
11.0a discoverable \= true  
11.0b trackingLevel \= ResourceRecord  
11.1 language  
11.1a inherited

**Definition:** The container element for all languages for a resource.

**Data Constraint:** Container

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:**   
\`\`\`\<languages discoverable=”true” trackingLevel=”ResourceRecord”\>  
	\<language inherited=”false”\>en\</language\>  
	\<language inherited=”false”\>fr\</language\>  
\</languages\>\`\`\`

### 11.1 language {#11.1-language}

**Semantic Unit:** language

**Semantic Components:**   
11.1a inherited

**Definition:** Language declaration for the contents of the resource.

**Data Constraint:** xs:language

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Element repeatable up to 100 times. Utilizes the xs:language constraint.

**Links:** None

## 

## 12.0 licenses {#12.0-licenses}

**Semantic Unit:** licenses

**Semantic Components:**   
12.0a discoverable \= true  
12.0b trackingLevel \= ResourceRecord  
12.1 license  
12.1a [licenseURI](#licenseuri)  
12.1b [licenseID](#licenseid)  
12.1c [licenseIDScheme](#licenseidscheme)  
12.1d [licenseIDSchemeURI](#licenseidschemeuri)

**Definition:** The container element for all licenses for a resource.

**Data Constraint:** Container

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:** 

### 12.1 license {#12.1-license}

**Semantic Unit:** license

**Semantic Components:**   
12.1a [licenseURI](#licenseuri)  
12.1b [licenseID](#licenseid)  
12.1c [licenseIDScheme](#licenseidscheme)  
12.1d [licenseIDSchemeURI](#licenseidschemeuri)

**Definition:** Specific rights granted for copying and reusing the resource.

**Data Constraint:** xs:string

Controlled vocabulary:

* Creative Commons Public Domain Dedication 1.0 Universal  
* Creative Commons Attribution 4.0 International  
* Creative Commons Attribution-Sharealike 4.0 International  
* Creative Commons Attribution-Noncommercial 4.0 International  
* Creative Commons Attribution-Noncommercial-Sharealike 4.0 International  
* Creative Commons Attribution-Noderivatives 4.0 International  
* Creative Commons Attribution-Noncommercial-Noderivatives 4.0 International  
* The MIT License

**Applicability:** Projects, Items

**Obligation:** Required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Element is repeatable up to 100 times.

**Links:** None

## 

## 13.0 fundingReferences {#13.0-fundingreferences}

**Semantic Unit:** fundingReferences

**Semantic Components:**   
13.0a discoverable \= true  
13.0b trackingLevel \= ResourceRecord  
13.1 fundingReference  
13.1a inherited  
13.1.1 funderName  
	13.1.1a xml:lang  
13.1.2 funderID  
13.1.2a [funderIDType](#funderidtype)  
13.1.2b [funderIDSchema](#funderidschema)  
13.1.3 awardNumber  
13.1.3a [awardURI](#awarduri)  
13.1.4 awardTitle  
13.1.4a xml:lang

**Definition:** The container element for all funding references for a resource.

**Data Constraint:** Container

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None 

**Usage Notes:** None

**Links:** Derived from the DataCite controlled vocabulary for [resourceTypeGeneral (v4.5+)](https://datacite-metadata-schema.readthedocs.io/en/4.5/properties/resourcetype/#a-resourcetypegeneral).

**Example:** 

### 13.1 fundingReference {#13.1-fundingreference}

**Semantic Unit:** fundingReference

**Semantic Components:**   
13.1a inherited  
13.1.1 funderName  
13.1.1a xml:lang  
13.1.2 funderID  
13.1.2a [funderIDType](#funderidtype)  
13.1.2b [funderIDSchema](#funderidschema)  
13.1.3 awardNumber  
13.1.3a [awardURI](#awarduri)  
13.1.4 awardTitle  
13.1.4a xml:lang

**Definition:** Information about financial support (funding) for the resource being registered.

**Data Constraint:** Container

**Applicability:** Projects, Items

**Obligation:** Required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** This container can be repeated up to 100 times.

**Links:** Derived from the DataCite definitions for [FundingReference (v4.5+)](https://datacite-metadata-schema.readthedocs.io/en/4.5/properties/fundingreference/).

#### 13.1.1 funderName {#13.1.1-fundername}

**Semantic Unit:** funderName

**Semantic Components:**  
13.1.1a xml:lang

**Definition:** Records the name of the funding provider.

**Data Constraint:** xs:string

String length: 1 \- 1000

**Applicability:** Projects, Items

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

#### 13.1.2 funderID {#13.1.2-funderid}

**Semantic Unit:** funderID

**Semantic Components:**   
13.1.2a [funderIDType](#funderidtype)  
13.1.2b [funderIDSchema](#funderidschema)

**Definition:** Records the unique identifier for the funding provider.

**Data Constraint:** xs:string

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

#### 13.1.3 awardNumber {#13.1.3-awardnumber}

**Semantic Unit:** awardNumber

**Semantic Components:**   
13.1.3a [awardURI](#awarduri)

**Definition:** Records the award number for the fundingReference container.

**Data Constraint:** xs:string

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

#### 13.1.4 awardTitle {#13.1.4-awardtitle}

**Semantic Unit:** awardTitle

**Semantic Components:**   
13.1.4a xml:lang

**Definition:** Records the title for the fundingReference container.

**Data Constraint:** xs:string

String length: 1 \- 1000

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

## 

## 14.0 duaReferences {#14.0-duareferences}

**Semantic Unit:** duaReferences

**Semantic Components:**   
14.0a discoverable \= true  
14.0b trackingLevel \= ResourceRecord  
14.1 duaReference  
14.1a inherited  
14.1.1 grantorName  
26.1.1a xml:lang  
14.1.2 duaID  
26.1.2a [duaURI](#duauri)  
14.1.3 duaTitle  
14.1.3a xml:lang

**Definition:** The container element for all DUA references for a resource. DUA is short for Data Use Agreement.

**Data Constraint:** Container

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

**Example:** 

### 14.1 duaReference {#14.1-duareference}

**Semantic Unit:** duaReference

**Semantic Components:**   
14.1a inherited  
14.1.1 grantorName  
14.1.1a xml:lang  
14.1.2 duaID  
14.1.2a [duaURI](#duauri)  
14.1.3 duaTitle  
14.1.3a xml:lang

**Definition:** Information about formal agreements governing data use pertaining to the resource. DUA is short for Data Use Agreement.

**Data Constraint:** Container

**Applicability:** Projects, Items

**Obligation:** Required

**Repeatability:** Repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** Container can be repeated up to 100 times

**Links:** None

#### 14.1.1 grantorName {#14.1.1-grantorname}

**Semantic Unit:** grantorName

**Semantic Components:**   
14.1.1a xml:lang

**Definition:** Records the name of the DUA grantor.

**Data Constraint:** xs:string

String length: 1 \- 1000

**Applicability:** Projects, Items

**Obligation:** Required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

#### 14.1.2 duaID {#14.1.2-duaid}

**Semantic Unit:** duaID

**Semantic Components:**   
14.1.2a [duaURI](#duauri)

**Definition:** Records the identifier for the DUA.

**Data Constraint:** xs:string

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

#### 14.1.3 duaTitle {#14.1.3-duatitle}

**Semantic Unit:** duaTitle

**Semantic Components:**   
14.1.3a xml:lang

**Definition:** Records the title for the DUA

**Data Constraint:** xs:string

String length: 1 \- 1000

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

## 15.0 dates {#15.0-dates}

**Semantic Unit:** dates

**Semantic Components:**   
15.0a discoverable \= true  
15.0b trackingLevel \= ResourceRecord  
15.1 startDate  
15.1a inherited  
15.2 endDate  
15.2a inherited  
15.3 retirementDate  
15.3a inherited  
15.4 publicationDate  
15.4a inherited  
15.5 otherDate  
15.5a inherited  
15.5b [dateType](#datetype)  
15.5c [dateInformation](#dateinformation)

**Definition:** The container element for all date elements that apply to a resource.

**Data Constraint:** Container

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Unlike provenance records, these date fields are all discoverable and tracked in the resource record. If the dates element is present, then it should contain at least one sub-element.

**Usage Notes:** None

**Links:** None

**Example:** 

### 15.1 startDate {#15.1-startdate}

**Semantic Unit:** startDate

**Semantic Components:**   
15.1a inherited

**Definition:** The date when the resource became, or will become, active (may be estimated).

**Data Constraint:** xs:date

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** The value must not be chronologically earlier than that of the approvalDateTime subfield under the submission field. Unlike provenance records, this date field is discoverable and tracked in the resource record.

**Usage Notes:** None

**Links:** None

### 15.2 endDate {#15.2-enddate}

**Semantic Unit:** endDate

**Semantic Components:**   
15.2a inherited

**Definition:** The date when the resource became, or will become, inactive (may be estimated).

**Data Constraint:** xs:date

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** The value must not be chronologically earlier than that of startDate, nor later than that of retirementDate. Unlike provenance records, this date field is discoverable and tracked in the resource record.

**Usage Notes:** None

**Links:** None

### 15.3 retirementDate {#15.3-retirementdate}

**Semantic Unit:** retirementDate

**Semantic Components:**   
15.3a inherited \= true

**Definition:** The date when the resource became, or will become, no longer useful to the primary users (may be estimated).

**Data Constraint:** xs:date

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** The value must not be chronologically earlier than that of endDate, nor later than that of the approvalDateTime subfield under the retirement field. Unlike provenance records, this date field is discoverable and tracked in the resource record.

**Usage Notes:** None

**Links:** None

### 15.4 publicationDate {#15.4-publicationdate}

**Semantic Unit:** publicationDate

**Semantic Components:**   
15.4a inherited \= true

**Definition:** The date when the resource became, or will become, publicly available (may be estimated).

**Data Constraint:** xs:date

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** The value must not be chronologically earlier than that of startDate, nor later than that of the approvalDateTime subfield under the publication field. Unlike provenance records, this date field is discoverable and tracked in the resource record.

**Usage Notes:** None

**Links:** None

### 15.5 otherDate {#15.5-otherdate}

**Semantic Unit:** otherDate

**Semantic Components:**   
15.5a inherited  
15.5b [dateType](#datetype)  
15.5c [dateInformation](#dateinformation)

**Definition:** A date or date range relevant to the resource, not captured by any other date field.

**Data Constraint:** xs:date

**Applicability:** Projects, Items

**Obligation:** Not required

**Repeatability:** Not repeatable

**Creation/Maintenance Notes:** Unlike provenance records, this date field is discoverable and tracked in the resource record.

**Usage Notes:** This element can be repeated up to 100 times.

**Links:** None

# 

# TigerData Data Definitions (Attributes) {#tigerdata-data-definitions-(attributes)}

## approved {#approved}

**Semantic Unit:** approved

**Used In:** [projectDirectory](#9.0-projectdirectory) (9.0), [storageCapacity](#13.0-storagecapacity) (13.0), and [storagePerformance](#15.0-storageperformance) (15.0) of Project Definitions

**Definition:** Standard attribute to specify whether a given field has an approved value. Applies to fields which have a request-approval framework, including projectDirectory, storageCapacity, and storagePerformance.

**Data Constraint:** xs:boolean

**Applicability:** Projects

**Obligation:** Not required

**Creation/Maintenance Notes:** None

**Usage Notes:** This attribute is only ever set to true once the approvedValue fields (9.3, 13.3, and 15.3) contain values.

**Links:** None

## alternativeIDType {#alternativeidtype}

**Semantic Unit:** alternativeIDType

**Used In:** [alternativeID](#2.1-alterativeid) (2.1) of Project Definitions and [alternativeID](#2.1-alterativeid-1) (2.1) of Item Definitions

**Definition:** A simple description of the alternative ID type (e.g. "Local accession number").

**Data Constraint:** xs:string

String length: 1 \- 1000

**Applicability:** Projects, Items

**Obligation:** Not required

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

## awardURI {#awarduri}

**Semantic Unit:** awardURI

**Used In:** [awardNumber](#21.1.3-awardnumber) (21.1.3) of Project Definitions and [awardNumber](#13.1.3-awardnumber) (13.1.3) of Item Definitions

**Definition:** Records the URI for the awardNumber.

**Data Constraint:** xs:anyURI

**Applicability:** Projects, Items

**Obligation:** Not required

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

## classificationCode {#classificationcode}

**Semantic Unit:** classificationCode

**Used In:** [keyword](#27.1-keyword) (27.1) of Project Definitions and [keyword](#8.1-keyword) (8.1) of Item Definitions

**Definition:** The classification code used for the subject term in the subject scheme.

**Data Constraint:**  xs:string

String length: 1 \- 1000

**Applicability:** Projects, Items

**Obligation:** Not required

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** Derived from DataCite [Subject attribute definitions (v4.5)](https://datacite-metadata-schema.readthedocs.io/en/4.5/properties/subject/).

## dateType {#datetype}

**Semantic Unit:** dateType

**Used In:** [otherDate](#22.5-otherdate) (22.5) of Project Definitions and [otherDate](#15.5-otherdate) (15.5) of Item Definitions

**Definition:** 

**Data Constraint:** xs:string

Controlled vocabulary:

* Copyrighted  
* Collected  
* Created  
* Updated  
* Valid  
* Other

**Applicability:** Projects, Items

**Obligation:** Required

**Creation/Maintenance Notes:** Controlled vocabulary definitions:

* Copyrighted \- The specific, documented date at which the resource receives a copyrighted status  
* Collected \- The date or date range in which the resource content was collected  
* Created \- The date the resource itself was put together; this could refer to a timeframe in ancient history, a date range, or a single date for a final component, e.g., the finalized file with all the data.  
* Updated \- The date of the last update to the resource, when the resource is being added to. May be a range  
* Valid \- The date or date range during which the dataset or resource is accurate  
* Other \- Other date that does not fit into an existing category

**Usage Notes:** None

**Links:** None

## dateInformation {#dateinformation}

**Semantic Unit:** dateInformation

**Used In:** [otherDate](#22.5-otherdate) (22.5) of Project Definitions and [otherDate](#15.5-otherdate) (15.5) of Item Definitions

**Definition:** More information about the value of otherDate.

**Data Constraint:** xs:string

String length: 1 \- 1000

**Applicability:** Projects, Items

**Obligation:** Not required

**Creation/Maintenance Notes:** None

**Usage Notes:** Recommended if dateType is Other.

**Links:** None

## departmentAbbreviation {#departmentabbreviation}

**Semantic Unit:** departmentAbbreviation

**Used In:** [department](#8.1-department) (8.1) of Projects Definitions

**Definition:** Records the common abbreviation for the department, if available.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Creation/Maintenance Notes:** 

**Usage Notes:** None

**Links:** 

## departmentCode {#departmentcode}

**Semantic Unit:** departmentCode

**Used In:** [department](#8.1-department) (8.1) of Projects Definitions

**Definition:** Records the numerical code for the department, if available.

**Data Constraint:** xs:integer

**Applicability:** Projects

**Obligation:** Not required

**Creation/Maintenance Notes:** This field will automatically populate, pulling data from the University’s instance of PeopleSoft.

**Usage Notes:** None

**Links:** 

## discoverable {#discoverable}

**Semantic Unit:** discoverable

**Used In:** Many fields

**Definition:** Standard attribute to specify whether a given field should be discoverable to search operations within TigerData systems.

**Data Constraint:** xs:boolean

**Applicability:** Projects, Items

**Obligation:** Not required

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

## duaURI {#duauri}

**Semantic Unit:** duaURI

**Used In:** [duaID](#26.1.2-duaid) (26.1.2) in Projects Definitions and [duaID](#14.1.2-duaid) (14.1.2) in Item Definitions.

**Definition:** Records the URI for the DUA.

**Data Constraint:** xs:anyURI

**Applicability:** Projects, Items

**Obligation:** Not required

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

## inherited {#inherited}

**Semantic Unit:** inherited

**Used In:** Many fields

**Definition:** Standard attribute to specify whether a given field's value should be inherited by child resources.

**Data Constraint:** xs:boolean

**Applicability:** Projects, Items

**Obligation:** Not required

**Creation/Maintenance Notes:** None

**Usage Notes:** Inheritance is limited to the applicability of the field to the child resource (e.g., researchDomain may be inherited by a subproject but not an item).

**Links:** None

## itemIDType {#itemidtype}

**Semantic Unit:** itemIDType

**Used In:** [itemID](#1.0-itemid) (1.0) in Items Definitions

**Definition:** Makes explicit that itemID is always given as a Mediaflux Asset ID.

**Data Constraint:** xs:string

Controlled vocabulary:

* MFAID

**Applicability:** Items

**Obligation:** 

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

## funderIDType {#funderidtype}

**Semantic Unit:** funderIDType

**Used In:** [funderID](#21.1.2-funderid) (21.1.2) in Projects Documentation and [funderID](#13.1.2-funderid) (13.1.2) in Items Documentation.

**Definition:** Records the type of identifier used for funderID.

**Data Constraint:** xs:string

Controlled vocabulary:

* Crossref Funder ID  
* GRID  
* ISNI  
* ROR  
* Other

**Applicability:** Projects, Items

**Obligation:** Required

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

## funderIDSchema {#funderidschema}

**Semantic Unit:** funderIDSchema

**Used In:** [funderID](#21.1.2-funderid) (21.1.2) in Projects Documentation and [funderID](#13.1.2-funderid) (13.1.2) in Items Documentation.

**Definition:** Records the schema that defines funderIDType.

**Data Constraint:** xs:anyURI

**Applicability:** Projects, Items

**Obligation:** Not required

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

## licenseID {#licenseid}

**Semantic Unit:** licenseID

**Used In:** [license](#24.1-license) (24.1) in Projects Documentation and [license](#12.1-license) (12.1) in Items Documentation.

**Definition:** Specifies the short, standardized version of the license name.

**Data Constraint:** xs:string

Controlled vocabulary:

* CC0 1.0  
* CC BY 4.0  
* CC BY-SA 4.0  
* CC BY-NC 4.0  
* CC BY-NC-SA 4.0  
* CC BY-ND 4.0  
* CC BY-NC-ND 4.0  
* MIT

**Applicability:** Projects, Items

**Obligation:** Required

**Creation/Maintenance Notes:** This short-hand documentation of the license will automatically populate to ensure it correlates to the value in the [license](#24.1-license) field.

**Usage Notes:** None

**Links:** None

## licenseIDScheme {#licenseidscheme}

**Semantic Unit:** licenseIDScheme

**Used In:** [license](#24.1-license) (24.1) in Projects Documentation and [license](#12.1-license) (12.1) in Items Documentation.

**Definition:** Specifies the scheme used for [licenseID](#licenseid).

**Data Constraint:** xs:string

**Applicability:** Projects, Items

**Obligation:** 

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** A list of commonly used licenses can be found at [SPDX](https://spdx.org/licenses/).

## licenseIDSchemeURI {#licenseidschemeuri}

**Semantic Unit:** licenseIDSchemeURI

**Used In:** [license](#24.1-license) (24.1) in Projects Documentation and [license](#12.1-license) (12.1) in Items Documentation.

**Definition:** Specifies the URI of the scheme given by [licenseIDScheme](#licenseidscheme).

**Data Constraint:** xs:anyURI

**Applicability:** Projects, Items

**Obligation:** 

**Creation/Maintenance Notes:** This URI will automatically populate based on the selected value in the [license](#24.1-license) field.

**Usage Notes:** None

**Links:** A list of commonly used licenses can be found at [SPDX](https://spdx.org/licenses/).

## licenseURI {#licenseuri}

**Semantic Unit:** licenseURI

**Used In:** [license](#24.1-license) (24.1) in Projects Documentation and [license](#12.1-license) (12.1) in Items Documentation.

**Definition:** Specifies the URI of the license.

**Data Constraint:** xs:string

Controlled vocabulary:

* [https://creativecommons.org/publicdomain/zero/1.0/](https://creativecommons.org/publicdomain/zero/1.0/)  
* [https://creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/)  
* [https://creativecommons.org/licenses/by-sa/4.0/](https://creativecommons.org/licenses/by-sa/4.0/)  
* [https://creativecommons.org/licenses/by-nc/4.0/](https://creativecommons.org/licenses/by-nc/4.0/)  
* [https://creativecommons.org/licenses/by-nc-sa/4.0/](https://creativecommons.org/licenses/by-nc-sa/4.0/)  
* [https://creativecommons.org/licenses/by-nd/4.0/](https://creativecommons.org/licenses/by-nd/4.0/)  
* [https://creativecommons.org/licenses/by-nc-nd/4.0/](https://creativecommons.org/licenses/by-nc-nd/4.0/)  
* [https://opensource.org/license/MIT](https://opensource.org/license/MIT)

**Applicability:** Projects, Items

**Obligation:** Required

**Creation/Maintenance Notes:** This short-hand documentation of the license should correlate to the value in the [license](#24.1-license) field.

**Usage Notes:** Controlled vocabulary references:

* [https://creativecommons.org/publicdomain/zero/1.0/](https://creativecommons.org/publicdomain/zero/1.0/) (CC0 1.0)  
* [https://creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/) (CC BY 4.0)  
* [https://creativecommons.org/licenses/by-sa/4.0/](https://creativecommons.org/licenses/by-sa/4.0/) (CC BY-SA 4.0)  
* [https://creativecommons.org/licenses/by-nc/4.0/](https://creativecommons.org/licenses/by-nc/4.0/) (CC BY-NC 4.0)  
* [https://creativecommons.org/licenses/by-nc-sa/4.0/](https://creativecommons.org/licenses/by-nc-sa/4.0/) (CC BY-NC-SA 4.0)  
* [https://creativecommons.org/licenses/by-nd/4.0/](https://creativecommons.org/licenses/by-nd/4.0/) (CC BY-ND 4.0)  
* [https://creativecommons.org/licenses/by-nc-nd/4.0/](https://creativecommons.org/licenses/by-nc-nd/4.0/) (CC BY-NC-ND 4.0)  
* [https://opensource.org/license/MIT](https://opensource.org/license/MIT) (MIT)

**Links:** None

## nameIdentifierScheme {#nameidentifierscheme}

**Semantic Unit:** nameIdentifierScheme

**Used In:** alternativeNameIdentifier ([4.7](#4.7-alternativenameidentifer), [5.7](#5.7-alternativenameidentifer), and [6.1.7](#6.1.7-alternativenameidentifer)) and multiple fields in [projectProvenance](#30.0-projectprovenance) (30.0) in Projects Documentation and [alternativeNameIdentifier](#4.1.7-alternativenameidentifer) (4.1.7) in Items Documentation.

**Definition:** The name of the scheme to which the name identifier belongs (required when an alternative name identifier is given).

**Data Constraint:** xs:string

**Applicability:** Projects, Items

**Obligation:** Required

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

## projectIDType {#projectidtype}

**Semantic Unit:** projectIDType

**Used In:** [projectID](#1.0-projectid) (1.0) and [parentProject](#3.0-parentproject) (3.0) in Projects Documentation and [parentProject](#3.0-parentproject-1) (3.0) in Items Documentation

**Definition:** Makes explicit that the project ID is always given as a DOI

**Data Constraint:** xs:string

Controlled vocabulary: 

* DOI

**Applicability:** Projects, Items

**Obligation:** Required

**Creation/Maintenance Notes:** None

**Usage Notes:** This unit is a fixed entry and cannot be altered.

**Links:** None

## protocol {#protocol}

**Semantic Unit:** protocol

**Used In:** [projectDirectoryPath](#9.1-projectdirectorypath) (9.1), [requestedValue](#9.2-requestedvalue) (9.2), and [approvedValue](#9.3-approvedvalue) (9.3) in Projects Documentation.

**Definition:** The storage connection protocol that defines how the path is written.

**Data Constraint:** xs:string

**Applicability:** Projects

**Obligation:** Not required

**Creation/Maintenance Notes:** 

**Usage Notes:** None

**Links:** None

## readOnly {#readonly}

**Semantic Unit:** readOnly

**Used In:** [dataUser](#6.1-datauser) (6.1) in Projects Documentation and [dataUse](#4.1-datauser)r (4.1) in Items Documentation

**Definition:** Declares whether the Data User has read-only access to the designated TigerData project or item.

**Data Constraint:** xs:boolean

**Applicability:** Projects, Items

**Obligation:** Required

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

## relatedIDType {#relatedidtype}

**Semantic Unit:** relatedIDType

**Used In:** [relation](#28.1-relation) (28.1) in Projects Documentation and [relation](#9.1-relation) (9.1) in Items documentation.

**Definition:** The type of the relation.

**Data Constraint:** xs:string

Controlled vocabulary:

* ARK   
* arXiv  
* bibcode  
* DOI  
* EAN13  
* EISSN  
* Handle  
* IGSN  
* ISBN  
* ISSN  
* ISTC  
* LISSN  
* LSID  
* MFAID  
* PMID  
* PURL  
* UPC  
* URL  
* URN  
* w3id

**Applicability:** Projects, Items

**Obligation:** 

**Creation/Maintenance Notes:** None

**Usage Notes:** Controlled vocabulary definitions:

* ARK \- A URI designed to support long-term access to information objects. Stands for Archival Resource Key  
* arXiv \- arXiv.org is a repository of preprints of scientific papers in the fields of mathematics, physics, astronomy, computer science, quantitative biology, statistics, and quantitative finance  
* bibcode \- astrophysics Data System bibliographic codes  
* DOI \- A character string used to uniquely identify an object. A DOI name is divided into two parts, a prefix and a suffix, separated by a slash.  
* EAN13 \- European Article Number (now renamed International Article Number, but retaining the original acronym). A 13-digit barcoding standard that is a superset of the original 12-digit Universal Product Code (UPC) system.  
* EISSN \- ISSN used to identify periodicals in electronic form (eISSN or e-ISSN).  
* Handle \- This refers specifically to an ID in the Handle system operated by the Corporation for National Research Initiatives (CNRI).  
* IGSN \- A code that uniquely identifies samples from our natural environment and related features-of-interest. IGSN is short for International Generic Sample Number  
* ISBN \- A unique numeric book identifier. There are 2 formats: a 10-digit ISBN format and a 13-digit ISBN. ISBN is short for International Standard Book Number  
* ISSN \- A unique 8-digit number used to identify a print or electronic periodical publication. ISSN is short for International Standard Serial Number  
* ISTC \- A unique “number” assigned to a textual work. An ISTC consists of 16 numbers and/or letters. ISTC is short for International Standard Text Code  
* LISSN \- The linking ISSN or ISSN-L enables collocation or linking among different media versions of a continuing resource.  
* LSID \- A unique identifier for data in the Life Science domain.  
* MFAID \- A Mediaflux Asset ID number. Include the domain and namespace to make the ID as persistent as possible  
* PMID \- A unique number assigned to each PubMed record.  
* PURL \- Persistent Uniform Resource Locator  
* UPC \- A barcode symbology used for tracking trade items in stores. Its most common form, the UPC-A, consists of 12 numerical digits. UPC is short for Universal Product Code  
* URL \- Also known as web address, a URL is a specific character string that constitutes a reference to a resource. URL is short for Universal Resource Locator  
* URN \- A unique and persistent identifier of an electronic document. URN is short for Universal Resource Name  
* w3id \- Mostly used to publish vocabularies and ontologies. The letters ‘w3’ stand for “World Wide Web”.

**Links:** Derived from the DataCite controlled vocabulary for [relatedIdentifierType](https://datacite-metadata-schema.readthedocs.io/en/4.5/properties/relatedidentifier/#a-relatedidentifiertype) (v4.5+)

## relatedMetadataScheme {#relatedmetadatascheme}

**Semantic Unit:** relatedMetadataScheme

**Used In:** [relation](#28.1-relation) (28.1) in Projects Documentation and [relation](#9.1-relation) (9.1) in Items documentation.

**Definition:** The name of the related metadata scheme.

**Data Constraint:** xs:string

String length: 1 \- 1000

**Applicability:** Projects, Items

**Obligation:** Not required

**Creation/Maintenance Notes:** None

**Usage Notes:** Use only with HasMetadata and IsMetadataFor relationTypes. Derived from DataCite [RelatedIdentifier attribute definitions](https://datacite-metadata-schema.readthedocs.io/en/4.5/properties/relatedidentifier/) (v4.5).

**Links:** None

## relatedMetadataSchemeType {#relatedmetadataschemetype}

**Semantic Unit:** relatedMetadataSchemeType

**Used In:** [relation](#28.1-relation) (28.1) in Projects Documentation and [relation](#9.1-relation) (9.1) in Items documentation.

**Definition:** The type of the related metadata scheme (e.g. XSD, DDT, Turtle).

**Data Constraint:** xs:string

String length: 1 \- 1000

**Applicability:** Projects, Items

**Obligation:** Not required

**Creation/Maintenance Notes:** None

**Usage Notes:** Use only with HasMetadata and IsMetadataFor relationTypes. Derived from DataCite [RelatedIdentifier attribute definitions](https://datacite-metadata-schema.readthedocs.io/en/4.5/properties/relatedidentifier/) (v4.5).

**Links:** None

## relatedMetadataSchemeURI {#relatedmetadataschemeuri}

**Semantic Unit:** relatedMetadataSchemeURI

**Used In:** [relation](#28.1-relation) (28.1) in Projects Documentation and [relation](#9.1-relation) (9.1) in Items documentation.

**Definition:** The URI of the related metadata scheme

**Data Constraint:** xs:anyURI

**Applicability:** Projects, Items

**Obligation:** Not required

**Creation/Maintenance Notes:** None

**Usage Notes:** Use only with HasMetadata and IsMetadataFor relationTypes. Derived from DataCite [RelatedIdentifier attribute definitions](https://datacite-metadata-schema.readthedocs.io/en/4.5/properties/relatedidentifier/) (v4.5).

**Links:** None

## relationType {#relationtype}

**Semantic Unit:** relationType

**Used In:** [relation](#28.1-relation) (28.1) in Projects Documentation and [relation](#9.1-relation) (9.1) in Items documentation.

**Definition:** 

**Data Constraint:** xs:string

Controlled vocabulary:

* IsCitedBy  
* Cites  
* IsSupplementTo  
* IsSupplementedBy  
* IsContinuedBy  
* Continues  
* Describes  
* IsDescribedBy  
* HasMetadata  
* IsMetadataFor  
* HasVersion  
* IsVersionOf  
* IsNewVersionOf  
* IsPreviousVersionOf  
* IsPartOf  
* HasPart  
* IsPublishedIn  
* IsReferencedBy  
* References  
* IsDocumentedBy  
* Documents  
* IsCompiledBy  
* Compiles  
* IsVariantFormOf  
* IsOriginalFormOf  
* IsIdenticalTo  
* IsReviewedBy  
* Reviews  
* IsDerivedFrom  
* IsSourceOf  
* IsRequiredBy  
* Requires  
* Obseletes  
* IsObseletedBy  
* IsCollectedBy  
* Collects  
* HasSubproject  
* IsSubprojectOf  
* HasItem  
* IsItemOf

**Applicability:** Projects, Items

**Obligation:** Required

**Creation/Maintenance Notes:** None

**Usage Notes:** Controlled vocabulary definitions:

* IsCitedBy \- B includes A in a citation  
* Cites \- A includes B in a citation  
* IsSupplementTo \- A is a supplement to B  
* IsSupplementedBy \- B is a supplement to A  
* IsContinuedBy \- A is continued by the work B  
* Continues \- A is a continuation of the work B  
* Describes \- A describes B  
* IsDescribedBy \- A is described by B  
* HasMetadata \- A has additional metadata B  
* IsMetadataFor \- Indicates additional metadata A for a resource B  
* HasVersion \- A has a version B  
* IsVersionOf \- A is a version of B  
* IsNewVersionOf \- A is a new edition of B, where the new edition has been modified or updated  
* IsPreviousVersionOf \- A is a previous edition of B  
* IsPartOf \- A is a portion of B; may be used for elements of a series. Do not use for formal relationships between TigerData projects, subprojects, or items  
* HasPart \- A includes the part B. Do not use for formal relationships between TigerData projects, subprojects, or items  
* IsPublishedIn \- A is published inside B, but is independent of other things published inside of B  
* IsReferencedBy \- A is used as a source of information by B  
* References \- B is used as a source of information for A  
* IsDocumentedBy \- B is documentation about/explaining A  
* Documents \- A is documentation about/explaining B  
* IsCompiledBy \- B is used to compile or create A  
* Compiles \- B is the result of a compile or creation event using A  
* IsVariantFormOf \- A is a variant or different form of B  
* IsOriginalFormOf \- A is the original form of B  
* IsIdenticalTo \- A is identical to B, for use when there is a need to register two separate instances of the same resource  
* IsReviewedBy \- A is reviewed by B  
* Reviews \- A is a review of B  
* IsDerivedFrom \- B is a source upon which A is based  
* IsSourceOf \- A is a source upon which B is based  
* IsRequiredBy \- A is required by B  
* Requires \- A requires B  
* Obsoletes \- A replaces B  
* IsObsoletedBy \- A is replaced by B  
* IsCollectedBy \- A is collected by B  
* Collects \- A collects B  
* HasSubproject \- A and B are both projects, and A includes B as a subproject. Use only with formal relationships between TigerData projects and subprojects  
* IsSubprojectOf \- A and B are both projects, and B includes A as a subproject. Use only with formal relationships between TigerData projects and subprojects  
* HasItem \- A is either a project or an item, B is an item, and A includes B. Use only with formal relationships between TigerData projects and/or items  
* IsItemOf \- A is an item, B is either a project or an item, and B includes A. Use only with formal relationships between TigerData projects and/or items.

**Links:** Derived from the DataCite [controlled vocabulary for relationType](https://datacite-metadata-schema.readthedocs.io/en/4.5/properties/relatedidentifier/#b-relationtype) (v4.5+)

## resourceClass {#resourceclass}

**Semantic Unit:** resourceClass

**Used In:** [resource](#1.0-resource) (1.0) as part of Resource Documentation

**Definition:** Specifies the class of a given resource: either Project or Item.

**Data Constraint:** xs:string

Controlled vocabulary:

* Project  
* Item

**Applicability:** Projects, Items

**Obligation:** Required

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

## resourceID {#resourceid}

**Semantic Unit:** resourceID

**Used In:** [resource](#1.0-resource) (1.0) as part of Resource Documentation

**Definition:** The unique identifier for the resource within TigerData systems.

**Data Constraint:** xs:string

String length: 1 \- 1000

**Applicability:** Projects, Items

**Obligation:** Required

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

## resourceIDType {#resourceidtype}

**Semantic Unit:** resourceIDType

**Used In:** [resource](#1.0-resource) (1.0) as part of Resource Documentation

**Definition:** If the resourceClass is Project, then the resourceID should be a DOI; if Item, then the resourceID should be a Mediaflux AssetID (MFAID).

**Data Constraint:** xs:string

Controlled vocabulary:

* DOI  
* MFAID

**Applicability:** Projects, Items

**Obligation:** Required

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

## resourceTypeGeneral {#resourcetypegeneral}

**Semantic Unit:** resourceTypeGeneral

**Used In:** [resourceType](#23.0-resourcetype) (23.0) and [relation](#28.1-relation) (28.1) in Projects Documentation and [resourceType](#7.0-resourcetype) (7.0) and [relation](#9.1-relation) (9.1) in Items Documentation

**Definition:** Standard attribute to specify the general type for a resource.

**Data Constraint:** xs:string

Controlled vocabulary:

* Audiovisual  
* Book  
* BookChapter  
* Collection  
* ComputationalNotebook  
* ConferencePaper  
* ConferenceProceedings  
* DataPaper  
* Dataset  
* Dissertation  
* Event  
* Image  
* Instrument  
* InteractiveResource  
* Journal  
* JournalArticle  
* Model  
* PeerReview  
* PhysicalObject  
* Preprint  
* Project  
* Report  
* Service  
* Software  
* Sound  
* Standard  
* StudyRegistration  
* Text  
* Workflow  
* Other

**Applicability:** Projects, Items

**Obligation:** 

**Creation/Maintenance Notes:** None

**Usage Notes:** Controlled vocabulary definitions:

* Audiovisual \- A series of visual representations imparting an impression of motion when shown in succession. May or may not include sound.  
* Book \- A medium for recording information in the form of writing or images, typically composed of many pages bound together and protected by a cover.  
* BookChapter \- One of the main divisions of a book.  
* Collection \- An aggregation of resources, which may encompass collections of one resourceType as well as those of mixed types. A collection is described as a group; its parts may also be separately described.  
* ComputationalNotebook \- A virtual notebook environment used for literate programming.  
* ConferencePaper \- Article that is written with the goal of being accepted to a conference.  
* ConferenceProceedings \- Collection of academic papers published in the context of an academic conference.  
* DataPaper \- A factual and objective publication with a focused intent to identify and describe specific data, sets of data, or data collections to facilitate discoverability.  
* Dataset \- Data encoded in a defined structure.  
* Dissertation \- A written essay, treatise, or thesis, especially one written by a candidate for the degree of Doctor of Philosophy.  
* Event \- A non-persistent, time-based occurrence.  
* Image \- A visual representation other than text.  
* Instrument \- A device, tool or apparatus used to obtain, measure and/or analyze data.  
* InteractiveResource \- A resource requiring interaction from the user to be understood, executed, or experienced.  
* Journal \- A scholarly publication consisting of articles that is published regularly throughout the year.  
* JournalArticle \- A written composition on a topic of interest, which forms a separate part of a journal.  
* Model \- An abstract, conceptual, graphical, mathematical or visualization model that represents empirical objects, phenomena, or physical processes.  
* PeerReview \- Evaluation of scientific, academic, or professional work by others working in the same field.  
* PhysicalObject \- A physical object or substance.  
* Preprint \- A version of a scholarly or scientific paper that precedes formal peer review and publication in a peer-reviewed scholarly or scientific journal.  
* Project \- A planned endeavor or activity, frequently collaborative, intended to achieve a particular aim using allocated resources such as budget, time, and expertise  
* Report \- A document that presents information in an organized format for a specific audience and purpose.  
* Service \- An organized system of apparatus, appliances, staff, etc., for supplying some function(s) required by end users.  
* Software \- A computer program other than a computational notebook, in either source code (text) or compiled form. Use this type for general software components supporting scholarly research. Use the “ComputationalNotebook” value for virtual notebooks.  
* Sound \- A resource primarily intended to be heard.  
* Standard \- Something established by authority, custom, or general consent as a model, example, or point of reference.  
* StudyRegistration \- A detailed, time-stamped description of a research plan, often openly shared in a registry or published in a journal before the study is conducted to lend accountability and transparency in the hypothesis generating and testing process.  
* Text \- A resource consisting primarily of words for reading that is not covered by any other textual resource type in this list.  
* Workflow \- A structured series of steps which can be executed to produce a final outcome, allowing users a means to specify and enact their work in a more reproducible manner.  
* Other \- A type of resource not otherwise described by defined types.

**Links:** Derived from the DataCite controlled vocabulary for [resourceTypeGeneral](https://datacite-metadata-schema.readthedocs.io/en/4.5/properties/resourcetype/#a-resourcetypegeneral) (v4.5+).

## schemeURI {#schemeuri}

**Semantic Unit:** schemeURI

**Used In:** alternativeNameIdentifier ([4.7](#4.7-alternativenameidentifer), [5.7](#5.7-alternativenameidentifer), and [6.1.7](#6.1.7-alternativenameidentifer)) and multiple fields in [projectProvenance](#30.0-projectprovenance) (30.0) in Projects Documentation and [alternativeNameIdentifier](#4.1.7-alternativenameidentifer) (4.1.7) in Items Documentation.

**Definition:** The URI of the scheme to which the name identifier belongs (required when an alternative name identifier is given)

**Data Constraint:** xs:anyURI

**Applicability:** Projects, Items

**Obligation:** Required

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

## subjectScheme {#subjectscheme}

**Semantic Unit:** subjectScheme

**Used In:** [keyword](#27.1-keyword) (27.1) of Project Definitions and [keyword](#8.1-keyword) (8.1) of Item Definitions

**Definition:** The name of the subject scheme or classification code or authority if one is used.

**Data Constraint:**  xs:string

String length: 1 \- 1000

**Applicability:** Projects, Items

**Obligation:** Not required

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** Derived from DataCite [Subject attribute definitions](https://datacite-metadata-schema.readthedocs.io/en/4.5/properties/subject/#a-subjectscheme) (v4.5)

## subjectSchemeURI {#subjectschemeuri}

**Semantic Unit:** subjectSchemeURI

**Used In:** [keyword](#27.1-keyword) (27.1) of Project Definitions and [keyword](#8.1-keyword) (8.1) of Item Definitions

**Definition:** The URI of the subject identifier scheme.

**Data Constraint:** xs:anyURI

**Applicability:** Projects, Items

**Obligation:** Not required

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** Derived from DataCite [Subject attribute definitions](https://datacite-metadata-schema.readthedocs.io/en/4.5/properties/subject/#b-schemeuri) (v4.5)

## trackingLevel {#trackinglevel}

**Semantic Unit:** trackingLevel

**Used In:** Many fields

**Definition:** Standard attribute to specify the tracking level of a given field

**Data Constraint:** xs:string

Controlled vocabulary:

* ResourceRecord  
* InternalUseOnly

**Applicability:** Projects, Items

**Obligation:** Not required

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

## userID {#userid}

**Semantic Unit:** userID

**Used In:** [dataSponsor](#4.0-datasponsor) (4.0), [dataManager](#5.0-datamanager) (5.0), [dataUser](#6.1-datauser) (6.1), and multiple fields in [projectProvenance](#30.0-projectprovenance) (30.0) of Projects Definitions and [dataUser](#4.1-datauser) (4.1) of Item Definitions

**Definition:** Specifies the (locally) unique user ID.

**Data Constraint:** xs:string

String pattern: \[a-z0-9\]{2,8}

**Applicability:** Projects, Items

**Obligation:** Required

**Creation/Maintenance Notes:** 

**Usage Notes:** If a value is given for the sub-element netID, then it should match the value given for userID

**Links:** None

## userIDType {#useridtype}

**Semantic Unit:** userIDType

**Used In:** [dataSponsor](#4.0-datasponsor) (4.0), [dataManager](#5.0-datamanager) (5.0), [dataUser](#6.1-datauser) (6.1), and multiple fields in [projectProvenance](#30.0-projectprovenance) (30.0) of Projects Definitions and [dataUser](#4.1-datauser) (4.1) of Item Definitions

**Definition:** Makes explicit that Princeton NetIDs are always used as the identifier for userID

**Data Constraint:** xs:string

Controlled vocabulary:

* NetID

**Applicability:** Projects, Items

**Obligation:** Required

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** None

## valueURI {#valueuri}

**Semantic Unit:** valueURI

**Used In:** [keyword](#27.1-keyword) (27.1) of Project Definitions and [keyword](#8.1-keyword) (8.1) of Item Definitions

**Definition:** The URI of the subject term.

**Data Constraint:** xs:anyURI

**Applicability:** Projects, Items

**Obligation:** Not required

**Creation/Maintenance Notes:** None

**Usage Notes:** None

**Links:** Derived from DataCite [Subject attribute definitions](https://datacite-metadata-schema.readthedocs.io/en/4.5/properties/subject/#c-valueuri) (v4.5).

# Appendix {#appendix}

## Appendix 1: Example XML for TigerData Projects {#appendix-1:-example-xml-for-tigerdata-projects}

## Appendix 2: Example XML for TigerData Items {#appendix-2:-example-xml-for-tigerdata-items}