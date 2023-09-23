
# NIEM 6.0

This is the NIEM 6.0 major release.

In a major version, content may be updated in any namespace, including Core. Changes may also be made to the NIEM architecture, which may be reflected in the structure and layout of the NIEM schemas.

## Key updates based on NDR 6.0 changes

The following are the key changes made to the model based on updates to the NDR for version 6.0.

*Note: The example XML schema snippets below have been simplified and shortened for better readability.*

### Updated namespace URIs ([niemopen/niem-model#25](https://github.com/niemopen/niem-model/issues/25))

NIEM is now an OASIS Open Project.  URIs for each namespace have been updated to follow the [OASIS Naming Directives, XML Namespace Identifiers and Namespace Documents](http://docs.oasis-open.org/specGuidelines/ndr/namingDirectives.html#xml-namespaces).

```xml
<!-- URI for NIEM Core from 5.2 -->
<xs:schema targetNamespace="http://release.niem.gov/niem/niem-core/5.0/" ...>

<!-- URI for NIEM Core for 6.0 -->
<xs:schema targetNamespace="https://docs.oasis-open.org/niemopen/ns/model/niem-core/6.0/" ...>
```

### Removed the roles construct ([niemopen/niem-naming-design-rules#6](https://github.com/niemopen/niem-naming-design-rules/issues/6))

NIEM has previously used `RoleOf` properties and role types to be able to relate multiple objects in a message back to the same entity.  NDR 6.0 drops the role construct in favor of using the `structures:uri` attribute instead: objects in a message with the same uri value should be interpreted as different roles of the same entity.  This change was made to make NIEM simpler to learn and use, and to improve consistency for implementers.

#### Updates to simple role types

Simple role types that contained a single `RoleOf` property have been updated to use type extension.

In the following example from the Learning and Development domain, `lrn-dev:StudentType` has been updated to remove the `nc:RoleOfPerson` property and to extend `nc:PersonType`:

```diff
  <xs:complexType name="StudentType">
    <xs:complexContent>
-     <xs:extension base="structures:ObjectType">
+     <xs:extension base="nc:PersonType">
        <xs:sequence>
-         <xs:element ref="nc:RoleOfPerson" minOccurs="0" maxOccurs="unbounded"/>
          <xs:element ref="lrn-dev:StudentID" minOccurs="0" maxOccurs="unbounded"/>
          <!-- ... -->
        </xs:sequence>
      </xs:extension>
    </xs:complexContent>
  </xs:complexType>
```

<details markdown="1">
  <summary>Expand to view the list of former simple role types and their new parent types in 6.0</summary>
  <br />

| Type | New parent type |
|:---- |:--------------- |
| cyber:UserType | nc:PersonType |
| em:FirstResponderType | nc:PersonType |
| em:PatientType | nc:PersonType |
| em:ResponderType | nc:PersonType |
| em:ServiceCallOriginatorType | nc:PersonType |
| hs:CaseParticipantType | nc:PersonType |
| hs:CaseworkerType | nc:PersonType |
| hs:ChildType | nc:PersonType |
| hs:ChildVictimType | nc:PersonType |
| hs:CourtEventAttendeeType | nc:PersonType |
| hs:JuvenileType | nc:PersonType |
| hs:MissingChildRelatedPersonType | nc:PersonType |
| hs:PatientType | nc:PersonType |
| hs:PetitionerType | nc:PersonType |
| hs:PharmacistType | nc:PersonType |
| hs:RequiredPartyType | nc:PersonType |
| hs:SeriousHabitualOffenderType | nc:PersonType |
| hs:StudentType | nc:PersonType |
| im:ICEEmployeeType | nc:PersonType |
| im:ICEOfficerType | nc:PersonType |
| it:AgentType | it:PartyType |
| it:BrokerType | it:PartyType |
| it:BuyerType | it:PartyType |
| it:CarrierType | it:PartyType |
| it:ConsigneeType | it:PartyType |
| it:ConsignorType | it:PartyType |
| it:ConsolidatorType | it:PartyType |
| it:ConsortiumCarrierType | it:PartyType |
| it:ContainerTerminalOperatorType | it:PartyType |
| it:DeconsolidatorType | it:PartyType |
| it:ExporterType | it:PartyType |
| it:ImporterType | it:PartyType |
| it:IntermediateCarrierType | it:PartyType |
| it:IntermediateConsigneeType | it:PartyType |
| it:ManufacturerType | it:PartyType |
| it:MasterType | it:PartyType |
| it:NonVesselOperatingCarrierType | it:PartyType |
| it:NotifyPartyType | it:PartyType |
| it:ProcessingEstablishmentType | it:PartyType |
| it:SellerType | it:PartyType |
| it:StevedoreType | it:PartyType |
| it:StuffingEstablishmentType | it:PartyType |
| it:UNDGContactType | it:PartyType |
| j:CrashDriverType | nc:PersonType |
| j:CrashNonMotoristType | nc:PersonType |
| j:CrashPassengerType | nc:PersonType |
| j:CrashPersonType | nc:PersonType |
| j:CrashVehicleOccupantType | nc:PersonType |
| j:CrashVehicleType | nc:VehicleType |
| j:CriminalOrganizationType | nc:OrganizationType |
| j:DeporteeType | nc:PersonType |
| j:EnforcementOfficialType | nc:PersonType |
| j:HearingInvestigatorType | nc:PersonType |
| j:JudicialOfficialType | nc:PersonType |
| j:JurorType | nc:PersonType |
| j:MissingPersonType | nc:PersonType |
| j:OtherInvolvedPersonType | nc:PersonType |
| j:PanelMemberType | nc:PersonType |
| j:ParticipantType | nc:PersonType |
| j:RegisteredOffenderType | nc:PersonType |
| j:StaffMemberType | nc:PersonType |
| j:ToolType | nc:ItemType |
| j:VehicleBranderType | nc:OrganizationType |
| j:WitnessType | nc:PersonType |
| lrn-dev:StudentType | nc:PersonType |
| nc:EquipmentType | nc:ItemType |
| nc:PublicationType | nc:DocumentType |
| nc:ReportType | nc:DocumentType |
| nc:WeaponType | nc:ItemType |
| scr:ScreenedAlienType | im:AlienRoleType |
| scr:ScreeningPersonType | nc:PersonType |

</details>

#### Updates to multi-option role types for persons, organizations, and items

Role types that contained `nc:RoleOfPerson` and `nc:RoleOfOrganization` properties, and optionally `nc:RoleOfItem`, have been updated to extend `nc:EntityType`.

This example from the Justice domain shows multiple `RoleOf` properties replaced by extension from `nc:EntityType`.

```diff
  <xs:complexType name="SubjectType">
    <xs:complexContent>
-     <xs:extension base="structures:ObjectType">
+     <xs:extension base="nc:EntityType">
        <xs:sequence>
-         <xs:element ref="nc:RoleOfPerson" minOccurs="0" maxOccurs="unbounded"/>
-         <xs:element ref="nc:RoleOfOrganization" minOccurs="0" maxOccurs="unbounded"/>
          <!-- ... -->
        </xs:sequence>
      </xs:extension>
    </xs:complexContent>
  </xs:complexType>
```

<details markdown="1">
  <summary>Expand to view the list of former role types that now extend `nc:EntityType`</summary>

  <br />

- j:LesseeType
- j:LessorType
- j:LienHolderType
- j:PawnBrokerType
- j:SubjectType
- j:VictimType

</details>

#### Updates to other multi-option role types

Other non-entity multi-option role types have been updated to use the NDR Representation pattern.  Since a type in XML cannot extend multiple parent types, a substitution group is used instead:

- An abstract property ending with the representation term `Representation` is added to the type.
- The former `RoleOf` properties are converted to substitutions for the new abstract `Representation` property.

*Note that this solution is similar to the one above that leverages `nc:EntityType`, which uses the representation pattern to represent an object that could be a person, organization, or item.  In this case, the combination of `RoleOf` properties are unique, so new representation properties have to be created.*

This example from the Justice domain shows multiple `RoleOf` properties replaced by the representation pattern.

```diff
  <xs:complexType name="EvidenceType">
    <xs:complexContent>
      <xs:extension base="structures:ObjectType">
        <xs:sequence>
-         <xs:element ref="nc:RoleOfItem" minOccurs="0" maxOccurs="unbounded"/>
-         <xs:element ref="j:RoleOfBinary" minOccurs="0" maxOccurs="unbounded"/>
-         <xs:element ref="j:RoleOfBiometric" minOccurs="0" maxOccurs="unbounded"/>
+         <xs:element ref="j:EvidenceRepresentation" minOccurs="0" maxOccurs="unbounded"/>
          <xs:element ref="j:EvidenceAmount" minOccurs="0" maxOccurs="unbounded"/>
          <!-- ... -->
        </xs:sequence>
      </xs:extension>
    </xs:complexContent>
  </xs:complexType>

+ <xs:element name="EvidenceBinary" type="nc:BinaryType" substitutionGroup="j:EvidenceRepresentation" />
+ <xs:element name="EvidenceBiometric" type="biom:BiometricDataType" substitutionGroup="j:EvidenceRepresentation" />
+ <xs:element name="EvidenceItem" type="nc:ItemType" substitutionGroup="j:EvidenceRepresentation" />
+ <xs:element name="EvidenceRepresentation" abstract="true" />

- <xs:element name="RoleOfBinary" type="nc:BinaryType" />
- <xs:element name="RoleOfBiometric" type="biom:BiometricDataType" />
  <!-- RoleOfItem is not defined in the Justice domain but is also being removed from Core -->
```

<details markdown="1">
  <summary>Expand to view the list of former role types that now employ the representation pattern</summary>

  <br />

- j:EvidenceType
  - *Previously contained:*
  - nc:RoleOfItem
  - j:RoleOfBinary
  - j:RoleOfBiometric
- mo:TargetType
  - *Previously contained:*
  - nc:RoleOfPerson
  - mo:RoleOfUnit
  - mo:RoleOfFacility

</details>

## Key content changes

The following is a summary of the key changes made in this release.  More details are available from the [6.0 issues list](https://github.com/niemopen/niem-model/labels/6.0) in the NIEM Model issue tracker, and the change log spreadsheet in the release package.

### Refactored other role components ([niemopen/niem-model#38](https://github.com/niemopen/niem-model/issues/38))

In addition to removing the `RoleOf` construct from the model due to NDR updates, other properties and types using the `Role` representation term were reviewed and updated as appropriate to improve consistency with the rest of the model.

**Renamed remaining RoleOf properties and types**

Renamed additional properties and types that were using `RoleOf` as the class term but were not using the `RoleOf` construct as defined by the NDR:

Component | Original name | Updated name
--------- | ------------- | ------------
Property | it:RoleOfCategory | it:PartyIDCategory
Property | it:RoleOfCategoryDescriptionText | it:PartyRoleCategoryDescriptionText
Property | it:RoleOfOrganizationCategoryDescriptionText | it:OrganizationRoleCategoryDescriptionText
Property | it:RoleOfOrganizationCategory | it:OrganizationRoleCategory
Property | it:RoleOfOrganizationCategoryAugmentationPoint | it:OrganizationRoleCategoryAugmentationPoint
Type | it:RoleOfOrganizationCategoryType | it:OrganizationRoleCategoryType

**Removed the Role representation term**

Removed extraneous `Role` representation terms from a list of properties and their corresponding types and augmentation point properties.  For example, `im:AlienRole` has been renamed `im:Alien`.

The following properties have been renamed:

- im:AlienExchangeVisitorRole
- im:AlienRole
- im:AlienStudentRole
- im:CitizenRole
- im:ForeignBornChildOfCitizenRole
- im:ImmigrantRole
- im:LawfulPermanentResidentRole
- im:NationalRole
- im:NaturalizedCitizenRole
- im:NonImmigrantRole
- im:PersonCountryRole
- im:OtherAlienRole
- im:ResidentRole

**Refactored im:PersonCountryRoleType**

Refactored `im:PersonCountryRoleType` to make immigration status more widely available for reuse:

- Moved `im:ImmigrationStatus` from `im:PersonCountryRoleType` to `im:PersonAugmentationType`, making it available wherever `nc:PersonType` is used.
- Updated `im:PersonCountryRoleType` to extend `nc:PersonType`.

**Refactored scr:PersonRole**

- Added a new Screening augmentation for `nc:PersonType`.
- Moved `scr:PersonRole` from `scr:ScreeningPersonType` to the new augmentation.
- Removed properties `scr:AgentPersonRole`, `scr:AgentAssociation`, and type `scr:AgentAssociationType` as they are no longer needed to relate an agent to a role.

### Refactored nc:EmployeeAssignmentAssociation ([niemopen/niem-model#14](https://github.com/niemopen/niem-model/issues/14))

Moved `nc:nc:EmployeeRegistrationAbstract` and `nc:EmployeeSupervisorIndicator` elements to from type `nc:EmployeeAssignmentAssociationType` to its parent type `nc:EmploymentAssociationType`.  This allows those properties to be used in any employment association, not just assignments.

The child type `nc:EmployeeAssignmentAssociationType` was no longer needed and was removed.  Property `nc:EmployeeAssignmentAssociation` was updated to be of type `nc:EmploymentAssociationType`.

### Support specifying empty value reason on simple values ([niemopen/niem-model#34](https://github.com/niemopen/niem-model/issues/34))

Created the following new attributes and added them to `nc:TextType` and `nc:QuantityType`:

- `nc:valueEmptyReasonCode` of type `nc:EmptyReasonCodeSimpleType`
- `nc:valueEmptyReasonText` of type `xs:string`

*These new attributes can also be used throughout the model with the new support for attribute wildcards in NIEM 6.0.*

Harmonized two domain code sets that represented a ternary choice with "Yes", "No", and "Unknown" code values with new code `nc:YesNoUnknownCodeType`:

- `em:TernaryIndicatorCodeType`
- `hs:JuvenileFamilyFinancialProblemCodeType`

*This new code set can be used in places where a boolean with a null value cannot be used to indicate the value is unknown or not applicable.*

### Add pronouns to nc:PersonType ([niemopen/niem-model#15](https://github.com/niemopen/niem-model/issues/15))

Add a substitution group with code and text substitutions for personal pronouns to `nc:PersonType`.

Code set:

- she/her
- he/him
- they/them
- other
- prefer not to share
- unknown

### Updated CBRN CaseMetadata and DataFileMetadata to have type nc:MetadataType ([niemopen/niem-model#24](https://github.com/niemopen/niem-model/issues/24))

CBRN defines two metadata elements that have type `structures:MetadataType`:

- `cbrn:CaseMetadata`
- `cbrn:DataFileMetadata`, which are both of type structures:MetadataType.

The `structures:MetadataType` does not carry content and is not meant to be used directly as a type of a property.

Updated these two properties to have type `nc:MetadataType`.

### Refactored cbrn:ReportType into an augmentation of nc:ReportType ([niemopen/niem-model#11](https://github.com/niemopen/niem-model/issues/11))

Refactored the following in `cbrn:ReportType`:

- `cbrn:ReportDateTime`
- `cbrn:CredentialsAuthenticationAbstract`
- `nc:ActivityName`
- `cbrn:ReportAugmentationPoint`

into an augmentation of `nc:ReportType`, making these properties more reusable.

Removed property `cbrn:ReportDateTime` ("A DateTime when a report was created.") as it is no longer needed with `nc:DocumentCreationDate` available through `nc:DocumentType`, the parent type of `nc:ReportType`.

### Add hs:Wages ([niemopen/niem-model#13](https://github.com/niemopen/niem-model/issues/13))

Created a new property `hs:Wages` for the existing type `hs:WagesType`.  Added the new property to `hs:PersonAugmentationType`.

### Updated Minimum Essential Metadata in MilOps ([niemopen/niem-model#40](https://github.com/niemopen/niem-model/issues/40))

The DoD Minimum Essential Metadata were updated by DoD Metadata Guidance issued by the DoD Chief Digital and Artificial Intelligence Officer in March 2023.   The following changes have been made:

- Updated the definitions of property `mo:MinimumEssentialMetadata` and type `mo:MinimumEssentialMetadataType`.
- Renamed property `mo:LegalAuthority` as `mo:AuthorizationReference` and changed its type to `nc:DocumentType`.
- Removed type `mo:LegalAuthorityType`.
- Renamed property `mo:Creator` as `mo:ResourceOriginator` and updated its definition.
- Renamed property `mo:OfficeOfRecord` as `mo:DataResourceCustodian` and updated its definition.
- Added new property `mo:DataItemCreateDateTime` to type `mo:MinimumEssentialMetadataType`.
- Added existing property `nc:DescriptionText` to type `mo:MinimumEssentialMetadataType`.
- Added existing properties to type `mo:ResourceFormatType`:
  - `nc:DocumentMediaCategoryText`
  - `nc:BinarySizeValue`
- Added existing properties to type `mo:ClassificationReferenceDocumentType`:
  - `nc:DocumentTitleText`
  - `nc:DocumentEffectiveDate`
  - `nc:DocumentAuthor`.
- Added existing properties to type `mo:HandlingRestrictionsCUIType`:
  - `cui:SpecifiedCategoryMarkingCode`
  - `cui:BasicCategoryMarkingCode`
  - `cui:DocumentMarkingLDC`

### Harmonized MilOps MILSTD2525 Components (niemopen/niem-model#58)

- Harmonized duplicate MILSTD2525-B and MILSTD2525-C types:
  - Refactored `mo:MILSTD2525-B-SIDC-Type` and `mo:MILSTD2525-C-SIDC-Type` into a single `mo:MILSTD2525-SIDC-Type`
  - Refactored `mo:MILSTD2525-B-SIDC-SimpleType` and `mo:MILSTD2525-C-SIDC-SimpleType` into a single `mo:MILSTD2525-SIDC-SimpleType`
- Updated property `mo:MILSTD2525-B-SIDC-Code` to have the new harmonized type `mo:MILSTD2525-SIDC-Type` and to make the definition unique.
- Updated property `mo:MILSTD2525-C-SIDC-Code` to have the new harmonized type `mo:MILSTD2525-SIDC-Type` and to make the definition unique.

### Added nc:Person to scr:PhysicalEncounterAgentAssociationType ([niemopen/niem-model#41](https://github.com/niemopen/niem-model/issues/41))

scr:PhysicalEncounterAgentAssociationType is defined as a relationship between a DHS agent and a person. The association was updated to add the missing `nc:Person` property.

### Updated scr:ChargeCategoryCodeSimpleType code definitions ([niemopen/niem-model#16](https://github.com/niemopen/niem-model/issues/16))

Removed a invalid section character from four code definitions in type scr:ChargeCategoryCodeSimpleType.

## Code set updates

### Updated FBI's National Crime Information Center (NCIC) codes

**Changes from 5.2 as of the April 2023 quarterly update:**

Added codes to the following types:

| Code set | General description |
|:-------- |:------------------- |
| ncic:CALCodeSimpleType | Gun caliber |
| ncic:MAKCodeSimpleType | Gun make |
| ncic:MotorcycleCodeSimpleType | Vehicle Make/Brand Name for Motorcycles and Parts |
| ncic:TrailersCodeSimpleType | Vehicle Make/Brand Name for Trailer Make |
| ncic:TrucksCodeSimpleType | Vehicle Make/Brand Name for Trucks and Parts |
| ncic:VMACodeSimpleType | Vehicle Make |
| ncic:VMOCodeSimpleType | Vehicle Model for Automobiles, Light-Duty Vans, Light-Duty Trucks, and Parts |

Modified definitions of codes in the following types:

| Code set | General description |
|:-------- |:------------------- |
| ncic:FarmCodeSimpleType | Vehicle Make/Brand Name for Farm and Garden Equipment and Parts |
| ncic:MAKCodeSimpleType | Gun make |
| ncic:MotorcycleCodeSimpleType | Vehicle Make/Brand Name for Motorcycles and Parts |
| ncic:SnowmobileCodeSimpleType | Vehicle Make/Brand Name for Snowmobiles and Parts |
| ncic:TrailersCodeSimpleType | Vehicle Make/Brand Name for Trailer Make |
| ncic:TrucksCodeSimpleType | Vehicle Make/Brand Name for Trucks and Parts |
| ncic:VMACodeSimpleType | Vehicle Make |

Removed codes from the following types:

| Code set | General description |
|:-------- |:------------------- |
| ncic:IndianCodeSimpleType | Indian Nations |

**Changes from the July 2023 quarterly update:**

Added codes to the following types:

| Code set | General description |
|:-------- |:------------------- |
| ncic:IndianCodeSimpleType | Indian Nations |
| ncic:MAKCodeSimpleType | Gun make |
| ncic:TrailersCodeSimpleType | Vehicle Make/Brand Name for Trailer Make |
| ncic:TYPCodeSimpleType | Article Type |
| ncic:VMACodeSimpleType | Vehicle Make |
| ncic:VMOCodeSimpleType | Vehicle Model for Automobiles, Light-Duty Vans, Light-Duty Trucks, and Parts |

Modified definitions of codes in the following types:

| Code set | General description |
|:-------- |:------------------- |
| ncic:MAKCodeSimpleType | Gun make |
| ncic:TrailersCodeSimpleType | Vehicle Make/Brand Name for Trailer Make |
| ncic:VMACodeSimpleType | Vehicle Make |
| ncic:VMOCodeSimpleType | Vehicle Model for Automobiles, Light-Duty Vans, Light-Duty Trucks, and Parts |
