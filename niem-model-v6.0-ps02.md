
<div class="row">
  <div class="column">
    <img
      src="https://docs.oasis-open-projects.org/templates/logo/open-projects-logo-2020-large.png"
      alt="OASIS OP Logo" style="width:100%" />
  </div>
  <div class="column">
    <img
      src="https://github.com/niemopen/oasis-open-project/raw/main/artwork/NIEM-NO-Logo-v5.png"
      alt="NIEMOpen Logo" style="width:65%" />
  </div>
</div>

-------

# NIEM Model Version 6.0

## Project Specification 02

## 26 March 2025

&nbsp;

#### This stage:

https://docs.oasis-open.org/niemopen/niem-model/v6.0/ps02/niem-model-v6.0-ps02.html (Authoritative) \
https://docs.oasis-open.org/niemopen/niem-model/v6.0/ps02/niem-model-v6.0-ps02.pdf

#### Previous stage:

https://docs.oasis-open.org/niemopen/niem-model/v6.0/ps01/niem-model-v6.0-ps01.html (Authoritative) \
https://docs.oasis-open.org/niemopen/niem-model/v6.0/ps01/niem-model-v6.0-ps01.pdf

#### Latest stage:

https://docs.oasis-open.org/niemopen/niem-model/v6.0/niem-model-v6.0.html (Authoritative) \
https://docs.oasis-open.org/niemopen/niem-model/v6.0/niem-model-v6.0.pdf

#### Open Project:

[NIEMOpen Business Architecture Committee (NBAC) of the OASIS NIEMOpen OP](http://www.niemopen.org/)

#### Project Chair:

Katherine Escobar (katherine.b.escobar.civ@mail.mil), [Joint Staff J6](https://www.jcs.mil/Directorates/J6-C4-Cyber/)

#### NBAC Technical Steering Committee Chairs:

Kamran Atri (katri@a4safe.com), [A4SAFE](https://a4safe.com/) \
Thomas Krul (thomas.krul@ecn.forces.gc.ca), [Public Safety Canada](https://www.publicsafety.gc.ca) \
Paul Wormeli (pwormeli@WormeliConsulting.com), [Wormeli Consulting LLC](https://wormeliconsulting.com/)

#### Editor:

Christina Medlin (christina.medlin@gtri.gatech.edu), [Georgia Tech Research Institute](https://gtri.gatech.edu/)

#### Additional artifacts:

This prose specification is one component of a Work Product that also includes:

- Complete XML Schema:
  - NIEM Core Schema: https://docs.oasis-open.org/niemopen/niem-model/v6.0/ps02/xsd/niem-core.xsd
  - NIEM Domain Schemas: https://docs.oasis-open.org/niemopen/niem-model/v6.0/ps02/xsd/domains/
  - NIEM Adapter Schemas: https://docs.oasis-open.org/niemopen/niem-model/v6.0/ps02/xsd/adapters/
  - NIEM Auxiliary Schemas: https://docs.oasis-open.org/niemopen/niem-model/v6.0/ps02/xsd/auxiliary/
  - NIEM Code Schemas: https://docs.oasis-open.org/niemopen/niem-model/v6.0/ps02/xsd/codes/
  - NIEM External Schemas: https://docs.oasis-open.org/niemopen/niem-model/v6.0/ps02/xsd/external/
  - NIEM Utility Schemas: https://docs.oasis-open.org/niemopen/niem-model/v6.0/ps02/xsd/utility/

- NIEM Documentation files, including:

  - NIEM README: https://docs.oasis-open.org/niemopen/niem-model/v6.0/ps02/README.md/
  - NIEM documentation files: https://docs.oasis-open.org/niemopen/niem-model/v6.0/ps02/docs/

- Other artifacts:

  - NIEM CSV files: https://docs.oasis-open.org/niemopen/niem-model/v6.0/ps02/csv/
  - NIEM JSON-LD files: https://docs.oasis-open.org/niemopen/niem-model/v6.0/ps02/json-ld/
  - NIEM XML Catalog: https://docs.oasis-open.org/niemopen/niem-model/v6.0/ps02/xsd/xml-catalog.xml

#### Related work:

This specification replaces or supersedes:

- _NIEM 5.2_. https://release.niem.gov/niem/5.2/.

This specification is related to:

- _NIEM Naming and Design Rules (NDR) Version 6.0_. Edited by Scott Renner. 1 January 2025. OASIS Project Specification Draft 01. https://docs.oasis-open.org/niemopen/ndr/v6.0/psd01/ndr-v6.0-psd01.html. Latest stage: https://docs.oasis-open.org/niemopen/ndr/v6.0/ndr-v6.0.html.

- _NIEM Code Lists Specification Version 6.0_.  Work in progress.

- _NIEM Conformance Specification Version 6.0_. Work in progress.

- _NIEM Conformance Targets Attribute Specification Version 6.0_. Work in progress.

#### Abstract:

NIEM is a data model that enables efficient information exchange across diverse public and private organizations. NIEM can improve interoperability among message exchange partners by providing consistent rules, reusable data components, and repeatable processes.

#### Status:

This document was last revised or approved by the Project Governing Board of the OASIS NIEMOpen OP on the above date. The level of approval is also listed above. Check the "Latest stage" location noted above for possible later revisions of this document. Any other numbered Versions and other technical work produced by the Open Project (OP) are listed at http://www.niemopen.org/.

Comments on this work can be provided by opening [issues](https://github.com/niemopen/niem-model/issues/new) in the [model repository](https://github.com/niemopen/niem-model) or by sending email to the project's public comment list: niemopen-comment@lists.oasis-open-projects.org. List information is available at https://lists.oasis-open-projects.org/g/niemopen-comment.

Note that any machine-readable content ([Computer Language Definitions](https://www.oasis-open.org/policies-guidelines/tc-process-2017-05-26/#wpComponentsCompLang)) declared Normative for this Work Product is provided in separate plain text files. In the event of a discrepancy between any such plain text file and display content in the Work Product's prose narrative document(s), the content in the separate plain text file prevails.

#### Key words:

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in BCP 14 [[RFC2119](#rfc2119)] and [[RFC8174](#rfc8174)] when, and only when, they appear in all capitals, as shown here.

#### Citation format:

When referencing this specification the following citation format should be used:

**[NIEM-Model-v6.0]**

_NIEM Model Version 6.0_. Edited by Christina Medlin. 10 March 2025. OASIS Project Specification 02. https://docs.oasis-open.org/niemopen/niem-model/v6.0/ps02/niem-model-v6.0-ps02.html. Latest stage: https://docs.oasis-open.org/niemopen/niem-model/v6.0/niem-model-v6.0.html.

-------

## Notices

Copyright &copy; OASIS Open 2025. All Rights Reserved.

Distributed under the terms of the OASIS [IPR Policy](https://www.oasis-open.org/policies-guidelines/ipr/).

For complete copyright information please see the Notices section in the Appendix.

-------

# Table of Contents

- [NIEM Model Version 6.0](#niem-model-version-60)
  - [Project Specification 02](#project-specification-02)
  - [10 March 2025](#10-march-2025)
      - [This stage:](#this-stage)
      - [Previous stage:](#previous-stage)
      - [Latest stage:](#latest-stage)
      - [Open Project:](#open-project)
      - [Project Chair:](#project-chair)
      - [NBAC Technical Steering Committee Chairs:](#nbac-technical-steering-committee-chairs)
      - [Editor:](#editor)
      - [Additional artifacts:](#additional-artifacts)
      - [Related work:](#related-work)
      - [Abstract:](#abstract)
      - [Status:](#status)
      - [Key words:](#key-words)
      - [Citation format:](#citation-format)
  - [Notices](#notices)
- [Table of Contents](#table-of-contents)
- [1 Introduction](#1-introduction)
  - [1.1 Changes from earlier versions](#11-changes-from-earlier-versions)
    - [1.1.1 Changes from 5.2](#111-changes-from-52)
    - [1.1.2 Changes from 6.0 PS01](#112-changes-from-60-ps01)
  - [1.2 Glossary](#12-glossary)
    - [1.2.1 Definitions of terms](#121-definitions-of-terms)
    - [1.2.2 Acronyms and abbreviations](#122-acronyms-and-abbreviations)
- [2 The NIEM Model](#2-the-niem-model)
  - [2.1 Content](#21-content)
    - [2.1.1 NIEM Core](#211-niem-core)
    - [2.1.2 Domains](#212-domains)
    - [2.1.3 Codes](#213-codes)
    - [2.1.4 Adapters](#214-adapters)
    - [2.1.5 Auxiliary](#215-auxiliary)
    - [2.1.6 External](#216-external)
    - [2.1.7 Utility](#217-utility)
  - [2.2 The NIEM architecture](#22-the-niem-architecture)
- [3 Conformance](#3-conformance)
- [Appendix A. References](#appendix-a-references)
  - [A.1 Normative References](#a1-normative-references)
  - [A.2 Informative References](#a2-informative-references)
- [Appendix B. Acknowledgments](#appendix-b-acknowledgments)
  - [B.1 Special Thanks](#b1-special-thanks)
  - [B.2 Participants](#b2-participants)
- [Appendix C. Revision History](#appendix-c-revision-history)
- [Appendix D. Notices](#appendix-d-notices)

-------

# 1 Introduction

The NIEM model is a data model made up of a collection of properties and types defined within a set of namespaces, organized by governance authority.  NIEM components can be leveraged as reusable building blocks in information exchanges, providing consistency and well-defined semantics that support interoperability among various exchange partners.

## 1.1 Changes from earlier versions

### 1.1.1 Changes from 5.2

Significant changes to the NIEM model in version 6.0 from previous version 5.2 include:

- Core and cross-domain harmonization

- Updates to support the transition of NIEM to an OASIS Open Project, including namespace URI changes.

- Updates to support upcoming [NIEM-NDR-v6.0] changes, including:
  - **Adapter changes** - New representation terms and a simpler type syntax.
  - **Attribute augmentations** - Allows message designers to create semantically-named attribute references from simple data properties to supplemental content.
  - **Attribute wildcards** - Allows declared attributes to be added to any NIEM element property.
  - **Metadata changes** - Now treated like regular objects, can be included in types where applicable, and can be augmented and extended.
  - **Role changes** - Leverages standard type extension and the existing `structures:uri` attribute to relate different roles of the same entity in a message together, replacing the previous `RoleOf` construct.

- Updates related to new digital identity requirements led by the Emergency Management domain, including:
  - `nc:IdentificationType` and related augmentation types
  - `nc:LicenseType` _(new)_ to support other kinds of licenses with NIEM
  - `j:DriverLicenseType` and related types
  - `nc:PassportType`, which now extends `nc:IdentificationType`
  - `em:PersonIDCardType`, which has been refactored to augment `nc:IdentificationType`
  - `m:SeamanLicenseType`, which can now be represented by the new `nc:LicenseType`
  - `m:MerchantMarinerDocumentType`, which can now be represented by the new `nc:LicenseType`

- Code set updates, including:

  - Updates provided by the FBI for the National Crime Information Center (NCIC) codes
  - GENC codes, version 3-12

- Synchronized the Justice domain version number with the rest of the model

Changes to version 6.0 are described in more detail in `README.md`.

### 1.1.2 Changes from 6.0 PS01

Changes in 6.0 PS02 to support [NIEM-NDR-v6.0] include:

- Updated NDR conformance targets
- Added attribute `appinfo:referenceAttributeIndicator="true"` to metadata reference attribute declarations
- Added attribute `structures:appliesToParent` to `structures:AdapterType`, `structures:AssociationType`, and `structures:ObjectType`
- Added element `Augmentation` to `appinfo.xsd`
- Added types `Name`, `NCName`, and `QName` to the `niem-xs` namespace
- Added documentation to utility schemas
- Changed `appinfo:referenceableIndicator` to `appinfo:referenceCode`
- Removed trailing hashes from URIs in `context.json`

Other changes to the model and package include:

- Added copyright and license information to additional schema annotation documentation blocks
- Fixed missing USMTF tab in the codes documentation spreadsheet
- Fixed NCIC codes from the October 2023 update
- Updated NCIC local terminology definition
- Updated the specification document

## 1.2 Glossary

### 1.2.1 Definitions of terms

| Term | Definition |
|:---- | ----------- |
| NDR    | The NIEM Naming and Design Rules is a technical specification managed by the NTAC which governs the architecture of the model. |

### 1.2.2 Acronyms and abbreviations

| Term | Literal |
|:---- | ------- |
| NBAC   | NIEM Business Architectures Committee TSC |
| NDR    | NIEM Naming and Design Rules Specification |
| NIEM   | NIEMOpen, the NIEM Open Project under OASIS |
| NMO    | NIEM Management Office TSC |
| NTAC   | NIEM Technical Architecture Committee TSC |
| PGB    | NIEM Project Governing Board |
| TSC    | Technical Steering Committee |

-------

# 2 The NIEM Model

## 2.1 Content

Properties and types in NIEM are defined in namespaces, which are organized by governance or authoritative source:

### 2.1.1 NIEM Core

NIEM Core is the collection of general-purpose content that does not belong to any one authoritative source.  As such, this content is managed collaboratively by the NBAC, which includes representatives from the NIEM domain subcommittees.

### 2.1.2 Domains

NIEM domains are namespaces for communities of interest that have stood up their own formal governance bodies as NBAC subcommittees within NIEM.

### 2.1.3 Codes

While code sets can be defined in NIEM Core, domains, and other namespaces, code namespaces are almost exclusively comprised of code sets.  Some NIEM code namespaces are actively managed by domain subcommittees or authoritative sources which work directly with NIEM.  Other NIEM code namespaces are managed by the NBAC or domain subcommittees and reflect publicly available code sources, modified to conform to NIEM NDR rules.

### 2.1.4 Adapters

Adapters are provided by the NDR as the mechanism to support non-conformant external standards in NIEM schemas and instances without triggering conformance violations.  Like code sets, while adapters can be defined in other namespaces, adapter namespaces are for namespaces that exclusively define adapters for external standards.

### 2.1.5 Auxiliary

Auxiliary namespaces define content representing communities of interest or standards.  Unlike domains, they do not require formal governance bodies within NIEM.

### 2.1.6 External

External namespaces in NIEM are non-conformant external standards.  These are provided for when the use of other standards defined outside of NIEM would provide greater interoperability than to create NIEM-conformant components representing those standards.  Properties from external standards are wrapped by NIEM adapter types, which prevent NDR conformance rules from triggering errors on their use.

### 2.1.7 Utility

Utility namespaces in NIEM provide architectures support from the NDR and other NIEM technical specifications.  They provide mechanisms to support such things as ids and references, linked data, IC-ISM and NTK security markup, dynamic code list support and code list support for codes defined in CSVs, Genericode, and other non-schema enumeration formats.

## 2.2 The NIEM architecture

The architecture of the NIEM model is governed by the NDR, which provides:

- general-purpose rules for naming, defining, and modeling components

- special constructs and techniques to represent features including:
  - associations, creating relationships between properties
  - adapters, as the mechanism to support the use of non-conformant external standards within NIEM
  - augmentations, to better support the need for extensions in a multi-domain model
  - roles, linking related but distinct objects in a message back to the same entity
  - representations, conceptually supporting multiple type inheritance
  - references within a message
  - linked data
  - security markup

- language-specific syntax rules

- an RDF interpretation of the underlying data model

- rules for extending the NIEM model to meet local requirements

Initially, NIEM has been limited to XML-based exchanges.  NIEM is working to provide similar levels of support for JSON-LD, and mechanisms to support other languages as well.

Major versions of the NIEM Model correspond to major versions of the NDR.  The architecture of the NIEM Model v6.0 is defined by [NIEM-NDR-v6.0].

-------

# 3 Conformance

This specification normatively defines NIEM Model Version 6.0 with a set of reference XML Schema documents. An implementation uses the model to partly define the messages it produces in terms of model components. In general, a conforming implementation uses all of the model components that satisfy a business need, uses each component according to its definition, does not needlessly duplicate components in the model, and does not add components to the model namespaces.

Specifically, an implementation conforms to this specification if it satisfies all of the following  conditions:

1. Every XML Schema document used in the implementation that has a target namespace equal to the target namespace of a reference schema document MUST be a subset of that document. This means that every possible XML element or attribute which is valid against the implementation's schema document will also be valid against the reference schema document.

2. Every XML Schema document used in the implementation that refers to a schema component with a namespace and local name equal to that of a component in a reference schema document MUST import that reference schema document or a subset of that reference schema document. 

3. In every XML document produced by the implementation, every element and attribute that has a namespace equal to the target namespace of a reference schema document MUST be valid against that reference schema document.

4. In every XML document produced by the implementation, the content of every element and attribute that has a namespace equal to the target namespace of a reference schema document MUST have a meaning consistent with the business semantics defined for that element or attribute in the reference schema document.  

5. Every component from a reference schema document that is used by the implementation MUST be used in a manner consistent with the component's structural definition and business semantics.

6. If a component defined by a reference schema document matches the business semantics required by the implementation, then the implementation MUST use that component, either directly or as the basis for derived components. An implementation MUST NOT needlessly duplicate the business semantics of a component in the NIEM model. (This condition also applies to implementations that do not create XML messages.)

7. An implementation MAY use the structure and business semantics of components defined by a reference schema document in a JSON message (or in any other supported serialization). Every such message component has an XML equivalent, and that equivalent component MUST satisfy conditions #3 and #4 above. (An implementation is not required to actually generate the XML equivalent; the requirement is only that the XML equivalent, if generated, would conform.)

The NIEM Naming and Design Rules [NIEM-NDR-v6.0] defines conformance targets, Schematron and text rules, and guidance for the conformant use of NIEM in messages and message specifications.

-------

# Appendix A. References

## A.1 Normative References

###### [NIEM-NDR-v6.0]

_NIEM Naming and Design Rules (NDR) Version 6.0_.  Edited by Scott Renner. 27 January 2025. OASIS Project Specification Draft 01.  https://docs.oasis-open.org/niemopen/ndr/v6.0/psd01/ndr-v6.0-psd01.html. Latest stage: https://docs.oasis-open.org/niemopen/ndr/v6.0/ndr-v6.0.html.


###### [RFC2119]

Bradner, S., "Key words for use in RFCs to Indicate Requirement Levels", BCP 14, RFC 2119, DOI 10.17487/RFC2119, March 1997, http://www.rfc-editor.org/info/rfc2119.

###### [RFC8174]

Leiba, B., "Ambiguity of Uppercase vs Lowercase in RFC 2119 Key Words", BCP 14, RFC 8174, DOI 10.17487/RFC8174, May 2017, http://www.rfc-editor.org/info/rfc8174.

## A.2 Informative References

-------

# Appendix B. Acknowledgments

## B.1 Special Thanks

Substantial contributions to this document from the following individuals are gratefully acknowledged:

- **Kamran Atri**, NBAC TSC co-chair, Emergency Management Domain Subcommittee
- **Chuck Chipman**, NTAC TSC, MilOps Domain Subcommittee
- **April Mitchell**, NBAC TSC, Justice Domain Subcommittee

Special thanks are given to the following individuals for their assistance in reviewing and resolving harmonization and other content issues affecting the model:

**NBAC Harmonization Subcommittee Members:**

| First Name   | Last Name    | Domain Subcommittee or COI |
| :----------- | :----------- | :------------------------- |
| Kamran       | Atri         | Emergency Management; NBAC co-chair |
| Aubrey       | Beach        | NIEMOpen |
| Chuck        | Chipman      | MilOps |
| Kelly        | Cullinane    | OASIS |
| Chet         | Ensign       | OASIS |
| Katherine    | Escobar      | Joint Staff J6; PGB Chair |
| Vamsi        | Kondannagari | Biometrics |
| Thomas       | Krul         | NBAC co-chair |
| Shunda       | Louis        | NIEMOpen |
| Christina    | Medlin       | NIEMOpen |
| April        | Mitchell     | Justice |
| Ashok        | Singal       | Biometrics |
| Beth         | Smalley      | NIEMOpen |
| Duncan       | Sparrell     | Cyber |
| Satish       | Sripada      | Biometrics |
| Jennifer     | Stathakis    | Biometrics |
| Stephen      | Sullivan     | NIEMOpen |
| Cynthia      | Sun          | International Human Services |
| Josh         | Wilson       | Biometrics |

Special thanks are also given to the following individuals for their guidance and expertise on architectural-related changes to the model:

**NTAC Members:**

| First Name   | Last Name    | Domain Subcommittee or COI |
| :----------- | :----------- | :------------------------- |
| Aubrey       | Beach        | BAH |
| Jim          | Cabral       | InfoTrack US; NTAC Co-Chair |
| Tom          | Carlson      | GTRI |
| Mike         | Douklias     | Joint Staff J6 |
| Katherine    | Escobar      | Joint Staff J6; PGB Chair |
| Mike         | Hulme        | Unisys |
| Eric         | Jahn         | Alexandria Consulting |
| Dave         | Kemp         | NSA |
| Vamsi        | Kondannagari | DHS |
| Peter        | Madruga      | GTRI |
| Christina    | Medlin       | GTRI |
| Scott        | Renner       | MITRE; NTAC Co-Chair |
| Duncan       | Sparrell     | sFractal Consulting |
| Jennifer     | Stathakis    | FBI |
| Stephen      | Sullivan     | BAH; NBAC Secretary |

## B.2 Participants

The following individuals have participated in the creation of this specification and are gratefully acknowledged:

**NBAC Members:**

| First Name   | Last Name  | Company  | Domain Subcommittee or COI |
| :----------- | :--------- | :------- |:-------------------------- |
| Meher        | Alam       | USDOT    | Surface Transportation |
| Kamran       | Atri       | A4SAFE   | Emergency Management; NBAC Co-Chair |
| Aubrey       | Beach      | BAH/Joint Staff J6 | NMO |
| Ernesto      | Broderson  |          | NTAC |
| Jim          | Cabral     | InfoTech | NTAC Co-Chair, PGB |
| Maria        | Cardiellos | IJIS     | PGB |
| Tom          | Carlson    | GTRI/Joint Staff J6 | NTAC |
| Chuck        | Chipman    | GTRI/Joint Staff J6 | NTAC |
| Kelly        | Cullinane  | OASIS    | OASIS |
| Mark         | Dotson     | GTRI/Joint Staff J6 | NMO, PGB alternate |
| Mike         | Douklias   | Joint Staff J6 | NTAC |
| Gary         | Egner      | Equivant | PGB |
| Chet         | Ensign     | OASIS    | OASIS |
| Katherine    | Escobar    | Joint Staff J6 | PGB Chair |
| Taraneh      | Etemadi    | OBIM     | NBAC, Biometrics |
| Lavdjola     | Farrington | Joint Staff J6 | MilOps Co-Chair |
| Bob          | Greeves    | NCJA     | Justice, PGB |
| Dave         | Hardy      | BAH/Joint Staff J6 | NBAC |
| Eric         | Jahn       | Alexandria Consulting | NTAC |
| Ashwini      | Jarral     | IJIS     | NBAC, PGB alternate |
| Luke         | Johnson    | USDOT/National Highway <br />Traffic Safety Administration (NHTSA) | Surface Transportation |
| David        | Kemp       | NSA      | NTAC |
| Vamsi        | Kondannagari |  Integral Consulting/OBIM  | Biometrics |
| Thomas       | Krul       | Public Safety Canada | NBAC Co-Chair |
| Payton       | Lamb       | Commonwealth of Virginia <br /> Office of Data Governance and Analytics (ODGA) | PGB |
| Shunda       | Louis      | BAH/Joint Staff J6 | NMO, Harmonization SC Co-Chair |
| Christina    | Medlin     | GTRI/Joint Staff J6 | Harmonization SC Co-chair |
| April        | Mitchell   | FBI      | Justice Co-Chair; PGB |
| Scott        | Renner     | MITRE/Joint Staff J6 | NTAC Co-Chair |
| Beth         | Smalley    | Joint Staff J6 | MilOps Co-Chair |
| Duncan       | Sparrell   | sFractal | NTAC, PGB |
| Satish       | Sripada    | OBIM     | Biometrics |
| Jennifer     | Stathakis  | FBI CJIS | Biometrics |
| Stephen      | Sullivan   | BAH/Joint Staff J6 | NBAC Secretary |
| Ryan         | Triplett   | Defense Forensic and Biometrics Agency | Biometrics |
| Josh         | Wilson     | FBI CJIS | Biometrics |
| Paul         | Wormeli    | Wormeli Consulting | NMO Communication and Outreach SC |

-------

# Appendix C. Revision History

More detailed change descriptions are included in the README file in this package.

Revision tracking is managed by GitHub.

**Commit history:**

Updates to working drafts are made to the `dev` branch.  The full commit history can be found at https://github.com/niemopen/niem-model/commits/dev.

**6.0 pull requests:**

The following are links to the GitHub pull requests merged into the model for 6.0:

| Milestone   | GitHub link |
|:----------- | ----------- |
| 6.0 PSD 01  | https://github.com/niemopen/niem-model/pulls?q=is%3Apr+milestone%3A6.0-psd01 |

Note that file diffs are available from each pull request.

**6.0 issues:**

The following are links to issues documenting the changes that have been made:

| Milestone | GitHub link |
|:--------- | ----------- |
| 6.0 PSD 01 model issues | `niemopen/niem-model` repo, issues with `milestone:6.0-psd01` <br /> https://github.com/niemopen/niem-model/issues?q=is:issue+milestone:6.0-psd01 |
| 6.0 PSD 01 model-related NDR issues | `niemopen/niem-naming-design-rules` repo, issues with `milestone:6.0-ps02` and `label:model` <br /> https://github.com/niemopen/niem-naming-design-rules/issues?q=is:issue+milestone:6.0-psd01+label:model |
| 6.0 PS 02 model issues | `niemopen/niem-model` repo, issues with `milestone:6.0-ps02` <br /> https://github.com/niemopen/niem-model/issues?q=is:issue+milestone:6.0-ps02 |

-------

# Appendix D. Notices

Copyright &copy; OASIS Open 2023. All Rights Reserved.

All capitalized terms in the following text have the meanings assigned to them in the OASIS Intellectual Property Rights Policy (the "OASIS IPR Policy"). The full [Policy](https://www.oasis-open.org/policies-guidelines/ipr/) may be found at the OASIS website.

This specification is published under [Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/legalcode).
Code associated with this specification is provided under [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).

All contributions made to this project have been made under the [OASIS Contributor License Agreement (CLA)](https://www.oasis-open.org/policies-guidelines/open-projects-process/#individual-cla-exhibit).

For information on whether any patents have been disclosed that may be essential to implementing this specification, and any offers of patent licensing terms, please refer to the [NIEMOpen IPR Statement](https://github.com/niemopen/oasis-open-project/blob/main/IPR-STATEMENT.md) page.

This document and translations of it may be copied and furnished to others, and derivative works that comment on or otherwise explain it or assist in its implementation may be prepared, copied, published, and distributed, in whole or in part, without restriction of any kind, provided that the above copyright notice and this section are included on all such copies and derivative works. However, this document itself may not be modified in any way, including by removing the copyright notice or references to OASIS, except as needed for the purpose of developing any document or deliverable produced by an OASIS Open Project (in which case the rules applicable to copyrights, as set forth in the OASIS IPR Policy, must be followed) or as required to translate it into languages other than English.

The limited permissions granted above are perpetual and will not be revoked by OASIS or its successors or assigns.

This document and the information contained herein is provided on an "AS IS" basis and OASIS DISCLAIMS ALL WARRANTIES, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO ANY WARRANTY THAT THE USE OF THE INFORMATION HEREIN WILL NOT INFRINGE ANY OWNERSHIP RIGHTS OR ANY IMPLIED WARRANTIES OF MERCHANTABILITY OR FITNESS FOR A PARTICULAR PURPOSE. OASIS AND ITS MEMBERS WILL NOT BE LIABLE FOR ANY DIRECT, INDIRECT, SPECIAL OR CONSEQUENTIAL DAMAGES ARISING OUT OF ANY USE OF THIS DOCUMENT OR ANY PART THEREOF.

As stated in the OASIS IPR Policy, the following three paragraphs in brackets apply to OASIS Standards Final Deliverable documents (Project Specifications, OASIS Standards, or Approved Errata).

\[OASIS requests that any OASIS Party or any other party that believes it has patent claims that would necessarily be infringed by implementations of this OASIS Standards Final Deliverable, to notify OASIS TC Administrator and provide an indication of its willingness to grant patent licenses to such patent claims in a manner consistent with the IPR Mode of the OASIS Open Project that produced this deliverable.\]

\[OASIS invites any party to contact the OASIS TC Administrator if it is aware of a claim of ownership of any patent claims that would necessarily be infringed by implementations of this OASIS Standards Final Deliverable by a patent holder that is not willing to provide a license to such patent claims in a manner consistent with the IPR Mode of the OASIS Open Project that produced this OASIS Standards Final Deliverable. OASIS may include such claims on its website, but disclaims any obligation to do so.\]

\[OASIS takes no position regarding the validity or scope of any intellectual property or other rights that might be claimed to pertain to the implementation or use of the technology described in this OASIS Standards Final Deliverable or the extent to which any license under such rights might or might not be available; neither does it represent that it has made any effort to identify any such rights. Information on OASIS' procedures with respect to rights in any document or deliverable produced by an OASIS Open Project can be found on the OASIS website. Copies of claims of rights made available for publication and any assurances of licenses to be made available, or the result of an attempt made to obtain a general license or permission for the use of such proprietary rights by implementers or users of this OASIS Standards Final Deliverable, can be obtained from the OASIS TC Administrator. OASIS makes no representation that any information or list of intellectual property rights will at any time be complete, or that any claims in such list are, in fact, Essential Claims.\]

The name "OASIS" is a trademark of [OASIS](https://www.oasis-open.org/), the owner and developer of this specification, and should be used only to refer to the organization and its official outputs. OASIS welcomes reference to, and implementation and use of, specifications, while reserving the right to enforce its marks against misleading uses. Please see https://www.oasis-open.org/policies-guidelines/trademark/ for above guidance.
