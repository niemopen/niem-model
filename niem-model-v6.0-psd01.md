
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

## Project Specification Draft 01

## 23 September 2023

&nbsp;

#### This stage:

https://docs.oasis-open.org/niemopen/niem-model/v6.0/psd01/niem-model-v6.0-psd01.html (Authoritative) \
https://docs.oasis-open.org/niemopen/niem-model/v6.0/psd01/niem-model-v6.0-psd01.pdf

#### Previous stage:

N/A

#### Latest stage:

https://docs.oasis-open.org/niemopen/niem-model/v6.0/niem-model-v6.0.html (Authoritative) \
https://docs.oasis-open.org/niemopen/niem-model/v6.0/niem-model-v6.0.pdf

#### Open Project:

[NIEMOpen Business Architecture Committee (NBAC) of the OASIS NIEMOpen OP](http://www.niemopen.org/)

#### Project Chair:

Katherine Escobar (katherine.b.escobar.civ@mail.mil), [Joint Staff J6](https://www.jcs.mil/Directorates/J6-C4-Cyber/)

#### NBAC Technical Steering Committee Chairs:

Kamran Atri (katri@a4safe.com), [A4SAFE](https://a4safe.com/) \
Thomas Krul (thomas.krul@ecn.forces.gc.ca), [Public Safety Canada](https://www.publicsafety.gc.ca)

#### Editor:

Christina Medlin (christina.medlin@gtri.gatech.edu), [Georgia Tech Research Institute](https://gtri.gatech.edu/)

#### Additional artifacts:

This prose specification is one component of a Work Product that also includes:

<!-- TODO: Additional artifacts - add descriptions -->

- NIEM Documentation files, including:

  - NIEM CSV files: https://docs.oasis-open.org/niemopen/niem-model/v6.0/psd01/csv/
  - NIEM JSON-LD files: https://docs.oasis-open.org/niemopen/niem-model/v6.0/psd01/json-ld/
  - NIEM XLSX files: https://docs.oasis-open.org/niemopen/niem-model/v6.0/psd01/xlsx/

- Complete Schema list: https://docs.oasis-open.org/niemopen/niem-model/v6.0/psd01/schemas.html

  - NIEM Core Schema: https://docs.oasis-open.org/niemopen/niem-model/v6.0/psd01/xsd/niem-core.xsd
  - NIEM Domain Schemas: https://docs.oasis-open.org/niemopen/niem-model/v6.0/psd01/xsd/domains/
  - NIEM Auxiliary Schemas: https://docs.oasis-open.org/niemopen/niem-model/v6.0/psd01/xsd/auxiliary/
  - NIEM Code List Schemas: https://docs.oasis-open.org/niemopen/niem-model/v6.0/psd01/xsd/codes/
  - NIEM Adapter Schemas: https://docs.oasis-open.org/niemopen/niem-model/v6.0/psd01/xsd/external/
  - Special NIEM Schemas: https://docs.oasis-open.org/niemopen/niem-model/v6.0/psd01/xsd/utility/

<!-- TODO: Additional artifacts - Other parts -->
- Other parts (list titles and/or file names)

#### Related work:

This specification replaces or supersedes:

<!-- TODO: Replaces 5.2 URL - Use GitHub instead? -->
- _NIEM 5.2_. https://release.niem.gov/niem/5.2/.

This specification is related to:

<!-- TODO: Related work section - Old 5.0 legacy specs vs not yet available 6.0 OASIS specs -->
- _National Information Exchange Model Naming and Design Rules_. Version 5.0 December 18, 2020. NIEM Technical Architecture Committee (NTAC). https://reference.niem.gov/niem/specification/naming-and-design-rules/5.0/niem-ndr-5.0.html.  (likely update to 6.0)
- Related specifications (include hyperlink, preferably to HTML format) \

#### Abstract:

<!-- TODO: Abstract -->
The National Information Exchange Model (NIEM) is a common vocabulary that enables efficient information exchange across diverse public and private organizations.

#### Status:

This document was last revised or approved by the Project Governing Board of the OASIS NIEMOpen OP on the above date. The level of approval is also listed above. Check the "Latest stage" location noted above for possible later revisions of this document. Any other numbered Versions and other technical work produced by the Open Project (OP) are listed at http://www.niemopen.org/.

Comments on this work can be provided by opening issues in the project repository or by sending email to the project's public comment list: niemopen@lists.oasis-open-projects.org. List information is available at https://lists.oasis-open-projects.org/g/niemopen.

Note that any machine-readable content ([Computer Language Definitions](https://www.oasis-open.org/policies-guidelines/tc-process-2017-05-26/#wpComponentsCompLang)) declared Normative for this Work Product is provided in separate plain text files. In the event of a discrepancy between any such plain text file and display content in the Work Product's prose narrative document(s), the content in the separate plain text file prevails.

#### Key words:

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in BCP 14 [[RFC2119](#rfc2119)] and [[RFC8174](#rfc8174)] when, and only when, they appear in all capitals, as shown here.

#### Citation format:

When referencing this specification the following citation format should be used:

**[NIEM-Model-v6.0]**

_NIEM Model Version 6.0_. Edited by Christina Medlin. 23 September 2023. OASIS Project Specification Draft 01. https://docs.oasis-open.org/niemopen/niem-model/v6.0/psd01/niem-model-v6.0-psd01.html. Latest stage: https://docs.oasis-open.org/niemopen/niem-model/v6.0/niem-model-v6.0.html.

-------

## Notices

Copyright &copy; OASIS Open 2023. All Rights Reserved.

Distributed under the terms of the OASIS [IPR Policy](https://www.oasis-open.org/policies-guidelines/ipr/).

For complete copyright information please see the Notices section in the Appendix.

-------

# Table of Contents

<!-- TODO: TOC -->
[[TOC will be inserted here]]

-------

# 1 Introduction

<!-- TODO: Label sections that are not normative -->

## 1.1 Changes from earlier Versions

<!-- TODO: Changes from earlier versions -->
This optional section provides a description of significant differences from previously published, differently numbered Versions of this specification, if any. (Detailed revision history of this numbered Version should be tracked in an Appendix.)

## 1.2 Glossary

### 1.2.1 Definitions of terms

| Term | Definition |
|:---- | ----------- |
NDR    | The NIEM Naming and Design Rules is a technical specification managed by the NTAC which governs the architecture of the model.

### 1.2.2 Acronyms and abbreviations

| Term | Literal |
|:---- | ------- |
NBAC   | NIEM Business Architectures Committee TSC
NDR    | NIEM Naming and Design Rules Specification
NIEM   | NIEMOpen, the NIEM Open Project under OASIS
NMO    | NIEM Management Office TSC
NTAC   | NIEM Technical Architecture Committee TSC
PGB    | NIEM Project Governing Board
SC     | Sub-Committee
TSC    | Technical Steering Committee

-------

# 3 Conformance

<!-- TODO: Conformance -->
(Note: The [OASIS TC Process](https://www.oasis-open.org/policies-guidelines/tc-process-2017-05-26/#wpComponentsConfClause) requires that a specification approved by the OP for public review, or for publication at the Project Specification or OASIS Standard level must include a separate section, listing a set of numbered conformance clauses, to which any implementation of the specification must adhere in order to claim conformance to the specification (or any optional portion thereof). This is done by listing the conformance clauses here.

For the definition of "conformance clause," see [OASIS Defined Terms](https://www.oasis-open.org/policies-guidelines/oasis-defined-terms-2018-05-22/#dConformanceClause).

See "Guidelines to Writing Conformance Clauses":
http://docs.oasis-open.org/templates/TCHandbook/ConformanceGuidelines.html.

Remove this note before submitting for publication.)

-------

# Appendix A. References

<!-- TODO: References -->

This appendix contains the normative and informative references that are used in this document. Any normative work cited in the body of the text as needed to implement the work product must be listed in the Normative References section below. Each reference to a separate document or artifact in this work must be listed here and must be identified as either a Normative or an Informative Reference. Normative references are specific (identified by date of publication and/or edition number or version number) and Informative references are either specific or non-specific.

While any hyperlinks included in this appendix were valid at the time of publication, OASIS cannot guarantee their long-term validity.

(Note - Reference sources:

For references to IETF RFCs, use the approved citation formats at:
http://docs.oasis-open.org/templates/ietf-rfc-list/ietf-rfc-list.html.

For references to W3C Recommendations, use the approved citation formats at:
http://docs.oasis-open.org/templates/w3c-recommendations-list/w3c-recommendations-list.html.

Remove this note before submitting for publication.)

## A.1 Normative References

<!-- TODO: Normative References -->

The following documents are referenced in such a way that some or all of their content constitutes requirements of this document.

###### [RFC2119]

Bradner, S., "Key words for use in RFCs to Indicate Requirement Levels", BCP 14, RFC 2119, DOI 10.17487/RFC2119, March 1997, http://www.rfc-editor.org/info/rfc2119.

###### [RFC8174]

Leiba, B., "Ambiguity of Uppercase vs Lowercase in RFC 2119 Key Words", BCP 14, RFC 8174, DOI 10.17487/RFC8174, May 2017, http://www.rfc-editor.org/info/rfc8174.

## A.2 Informative References

<!-- TODO: Informative References -->

###### [RFC3552]

Rescorla, E. and B. Korver, "Guidelines for Writing RFC Text on Security Considerations", BCP 72, RFC 3552, DOI 10.17487/RFC3552, July 2003, https://www.rfc-editor.org/info/rfc3552.

-------

# Appendix B. Safety, Security and Privacy Considerations

<!-- TODO: Safety, Security and Privacy Considerations -->

(Note: OASIS strongly recommends that Open Projects consider issues that might affect safety, security, privacy, and/or data protection in implementations of their specification and document them for implementers and adopters. For some purposes, you may find it required, e.g. if you apply for IANA registration.

While it may not be immediately obvious how your specification might make systems vulnerable to attack, most specifications, because they involve communications between systems, message formats, or system settings, open potential channels for exploit. For example, IETF [[RFC3552](#rfc3552)] lists “eavesdropping, replay, message insertion, deletion, modification, and man-in-the-middle” as well as potential denial of service attacks as threats that must be considered and, if appropriate, addressed in IETF RFCs.

In addition to considering and describing foreseeable risks, this section should include guidance on how implementers and adopters can protect against these risks.

We encourage editors and OP members concerned with this subject to read _Guidelines for Writing RFC Text on Security Considerations_, IETF [[RFC3552](#rfc3552)], for more information.

Remove this note before submitting for publication.)

-------

# Appendix C. Acknowledgments

<!-- TODO: Acknowledgements -->
`(Note: A Work Product approved by the OP should include a list of people who participated in the development of the Work Product. This is generally done by collecting the list of names in this appendix. This list should be initially compiled by the Chair, and any Member of the OP may add or remove their names from the list by request. Remove this note before submitting for publication.)`

## C.1 Special Thanks

Substantial contributions to this document from the following individuals are gratefully acknowledged:

- **Kamran Atri**, NBAC TSC
- **Chuck Chipman**, MilOps Domain Subcommittee
- **April Mitchell**, NBAC TSC

<!-- TODO: Review HSC list -->
Special thanks are given to the following individuals for their assistance in reviewing and resolving harmonization and other content issues affecting the model:

**NIEMOpen NBAC TSC Harmonization Subcommittee Members:**

| First Name | Last Name    | Domain Subcommittee or COI |
| :--------- | :----------- | :------------------------- |
Kamran       | Atri         | Emergency Management; NBAC co-chair
Aubrey       | Beach        | NIEMOpen
Chuck        | Chipman      | MilOps
Kelly        | Cullinane    | OASIS
Chet         | Ensign       | OASIS
Katherine    | Escobar      | Joint Staff J6; PGB Chair
Vamsi        | Kondannagari | Biometrics
Thomas       | Krul         | NBAC co-chair
Shunda       | Louis        | NIEMOpen
Christina    | Medlin       | NIEMOpen
April        | Mitchell     | Justice
Ashok        | Singal       | Biometrics
Beth         | Smalley      | NIEMOpen
Duncan       | Sparrell     | Cyber
Satish       | Sripada      | Biometrics
Jennifer     | Stathakis    | Biometrics
Stephen      | Sullivan     | NIEMOpen
Cynthia      | Sun          | International Human Services
Josh         | Wilson       | Biometrics

<!-- TODO: Review NTAC list -->
Special thanks are also given to the following individuals for their guidance and expertise on architectural-related changes to the model:

**NIEMOpen NTAC TSC Members:**

| First Name | Last Name    | Domain Subcommittee or COI |
| :--------- | :----------- | :------------------------- |
Aubrey       | Beach        | BAH
Jim          | Cabral       | InfoTrack US; NTAC Co-Chair
Tom          | Carlson      | GTRI
Mike         | Douklias     | Joint Staff J6
Katherine    | Escobar      | Joint Staff J6; PGB Chair
Mike         | Hulme        | Unisys
Eric         | Jahn         | Alexandria Consulting
Dave         | Kemp         | NSA
Vamsi        | Kondannagari | DHS
Christina    | Medlin       | GTRI
Scott        | Renner       | MITRE; NTAC Co-Chair
Duncan       | Sparrell     | sFractal Consulting
Jennifer     | Stathakis    | FBI
Stephen      | Sullivan     | BAH; NBAC Secretary

## C.2 Participants

<!-- TODO: Review NBAC list -->
The following individuals have participated in the creation of this specification and are gratefully acknowledged:

**NIEMOpen NBAC TSC Members:**

| First Name | Last Name  | Company  | Domain Subcommittee or COI
| :--------- | :--------- | :------- |:--------------------------
Meher        | Alam       | USDOT    | Surface Transportation
Kamran       | Atri       | A4SAFE   | Emergency Management; NBAC Co-Chair
Aubrey       | Beach      | BAH/Joint Staff J6 | NMO
Ernesto      | Broderson  |          | NTAC
Jim          | Cabral     | InfoTech | NTAC Co-Chair, PGB
Maria        | Cardiellos | IJIS     | PGB
Tom          | Carlson    | GTRI/Joint Staff J6 | NTAC
Chuck        | Chipman    | GTRI/Joint Staff J6 | NTAC
Kelly        | Cullinane  | OASIS    | OASIS
Mark         | Dotson     | GTRI/Joint Staff J6 | NMO, PGB alternate
Mike         | Douklias   | Joint Staff J6 | NTAC
Gary         | Egner      | Equivant | PGB
Chet         | Ensign     | OASIS    | OASIS
Katherine    | Escobar    | Joint Staff J6 | PGB Chair
Taraneh      | Etemadi    | OBIM     | NBAC, Biometrics
Lavdjola     | Farrington | Joint Staff J6 | MilOps Co-Chair
Bob          | Greeves    | NCJA     | Justice, PGB
Dave         | Hardy      | BAH/Joint Staff J6 | NBAC
Eric         | Jahn       | Alexandria Consulting | NTAC
Ashwini      | Jarral     | IJIS     | NBAC, PGB alternate
Luke         | Johnson    | USDOT/National Highway <br />Traffic Safety Administration (NHTSA) | Surface Transportation
David        | Kemp       | NSA      | NTAC
Vamsi        | Kondannagari |  Integral Consulting/OBIM  | Biometrics
Thomas       | Krul       | Public Safety Canada | NBAC Co-Chair
Payton       | Lamb       | Commonwealth of Virginia <br /> Office of Data Governance and Analytics (ODGA) | PGB
Shunda       | Louis      | BAH/Joint Staff J6 | NMO, Harmonization SC Co-Chair
Christina    | Medlin     | GTRI/Joint Staff J6 | Harmonization SC Co-chair
April        | Mitchell   | FBI      | Justice Co-Chair
Scott        | Renner     | MITRE/Joint Staff J6 | NTAC Co-Chair
Beth         | Smalley    | Joint Staff J6 | MilOps Co-Chair
Duncan       | Sparrell   | sFractal | NTAC, PGB
Satish       | Sripada    | OBIM     | Biometrics
Jennifer     | Stathakis  | FBI CJIS | Biometrics
Stephen      | Sullivan   | BAH/Joint Staff J6 | NBAC Secretary
Ryan         | Triplett   | Defense Forensic and Biometrics Agency | Biometrics
Josh         | Wilson     | FBI CJIS | Biometrics
Paul         | Wormeli    | Wormeli Consulting | NMO Communication and Outreach SC

-------

# Appendix D. Revision History

Revision tracking is managed by GitHub.

**Commit history:**

Updates to working drafts are made to the `dev` branch.  The full commit history can be found at https://github.com/niemopen/niem-model/commits/dev.

**6.0 pull requests:**

The following are links to the GitHub pull requests merged into the model for 6.0:

| Milestone | GitHub link |
|:--------- | ----------- |
6.0 PSD 01  | https://github.com/niemopen/niem-model/pulls?q=is%3Apr+milestone%3A6.0-psd01

Note that file diffs are available from each pull request.

**6.0 issues:**

The following are links to issues documenting the changes that have been made:

| Milestone | GitHub link |
|:--------- | ----------- |
6.0 PSD 01 model issues | `niemopen/niem-model` repo, issues with `milestone:6.0-psd01` <br /> https://github.com/niemopen/niem-model/issues?q=is%3Aissue+milestone%3A6.0-psd01
6.0 PSD 01 NDR-related issues | `niemopen/niem-naming-design-rules` repo, issues with `milestone:6.0-psd01` and `label:model` <br /> https://github.com/niemopen/niem-naming-design-rules/issues?q=is%3Aissue+milestone%3A6.0-psd01+label%3Amodel

-------

# Appendix E. Notices

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
