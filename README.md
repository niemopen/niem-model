
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

### Refactored metadata as regular NIEM components ([niemopen/niem-naming-design-rules#8](https://github.com/niemopen/niem-naming-design-rules/issues/8))

**NDR changes now treat metadata components like regular components:**

- Metadata types can use type extension
- Metadata types must support augmentation
- Metadata properties may be contained in other types

**Leveraged type extension for the following types:**

- `scr:PersonMetadataType` now extends `nc:MetadataType`

**Created augmentation points for the following metadata types:**

- `nc:MetadataType`
- `cbrn:TotalDoseMetadataType`
- `cbrn:TotalExposureMetadataType`
- `cui:DocumentMarkingMetadataType`
- `cui:PortionMarkingMetadataType`
- `mo:ImplementationSpecificSettingMetadataType`
- `mo:MinimumEssentialMetadataType`
- `mo:UncertaintyMetadataType`
- `scr:PersonMetadataType`

**Converted the following metadata types to augmentations of `nc:MetadataType`:**

- `hs:MetadataType`
- `j:MetadataType`

**Added the following metadata properties to types:**

- `cbrn:totalDoseMetadataRef`
  - Added to type `cbrn:TotalDoseuSvType` as a metadata attribute augmentation
- `cbrn:totalExposureMetadataRef`
  - Added to type `cbrn:TotalExposuremRType` as a metadata attribute augmentation
- `cui:DocumentMarkingMetadata`
  - Added to type `cui:DocumentAugmentationType`
  - Added to type `cui:ReportAugmentationType`
  - Added to type `cui:MessageAugmentationType`
- `mo:ImplementationSpecificSettingMetadata`
  - Added to type `mo:SettingType`
- `mo:MinimumEssentialMetadata`
  - Added to type `mo:DocumentAugmentationType`
  - Added to type `mo:ReportAugmentationType`
  - Added to type `mo:MessageAugmentationType`
- `mo:UncertaintyMetadata`
  - Added to type `mo:MeasureAugmentationType`
- `scr:PersonMetadata`
  - Added to type `scr:PersonAugmentationType`

**Changed the default parent type:**

Changed the default parent of metadata types from `structures:MetadataType` to `structures:ObjectType`.

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

### Added attribute augmentations for nc:Metadata and cui:PortionMarkingMetadata ([niemopen/niem-model#46](https://github.com/niemopen/niem-model/issues/46))

The NDR is removing support for the `structures:metadata` and `structures:relationshipMetadata` attributes.  Metadata properties can now be added to class types directly, via augmentation, or via extension.

For data types (representing a value, like a string or a number), element metadata properties cannot be attached directly.  Instead, the NDR will now support attribute augmentations, which allow attributes to be created with representation term `Ref` and type `xs:IDREFS`.  This XML Schema type allows a set of space-delimited xs:IDREF values, or pointers in XML.

Example schema changes from Core:

```diff
+ <xs:attribute name="portionMarkingMetadataRef" type="xs:IDREFS">
+   <xs:annotation>
+     <xs:documentation>An attribute reference to cui:PortionMarkingMetadata.</xs:documentation>
+   </xs:annotation>
+ </xs:attribute>

  <xs:element name="PortionMarkingMetadata" type="cui:PortionMarkingMetadataType" nillable="true">
    <xs:annotation>
      <xs:documentation>Metadata about the Controlled Unclassified Information
       (CUI) portion marking of a document.</xs:documentation>
    </xs:annotation>
  </xs:element>
```

Example usage in a message:

```diff
<my:Message>
  <nc:Person>
    <nc:PersonName>
-     <nc:PersonSurName structures:metadata="P01">Smith</nc:PersonSurName>
+     <nc:PersonSurName cui:portionMarkingMetadataRef="P01">Smith</nc:PersonSurName>
    </nc:PersonName>
  </nc:Person>

  <cui:PortionMarkingMetadata structures:id="M01">
    <!-- ... -->
  </cui:PortionMarkingMetadata>
</my:Message>
```

The `structures` metadata attributes were very generic and did not convey what kind of information should be referenced.  These new attribute augmentations have semantic names, making the requirements of a message specification clearer.

This approach should be used along with the new support for attribute wildcards in the `structures` schema, allowing message designers to attach declared attributes to NIEM-conformant complex types (classes or complex data types).

### Require unique enumerations ([niemopen/niem-naming-design-rules#30](https://github.com/niemopen/niem-naming-design-rules/issues/30))

Merged or resolved definitions for non-unique codes in the following types:

- `can:StreetDirectionCodeSimpleType` - *Merged English and French definitions*
- `cbrncl:FacilityUsageCodeSimpleType`
- `cyber:BreachClassificationCategoryCodeSimpleType`
- `dea:DrugCodeSimpleType`
- `em:BarcodeCodeSimpleType`
- `em:NotificationFunctionCategoryCodeSimpleType`
- `hazmat:HazmatCodeSimpleType`
- `mmucc:DriverLicenseClassCodeSimpleType`
- `mo:RegisteredServiceNameCodeSimpleType`
- `usmtf:AngleUnitCodeSimpleType`
- `usmtf:NauticalMileUnitCodeSimpleType`
- `usmtf:RFPowerUnitDecibelsCodeSimpleType`
- `usps:StreetSuffixCodeSimpleType`

Replaced a code in type `usmtf:RadioactiveHalfLifeCodeSimpleType`:

- Code `1600.00YR` with definition "RA-226+ (Radon)."
  - *Kept as is*
- Code `1600.00YR` with definition "SE-75 (Selenium). None"
  - Changed code to `119.80DA`
  - Removed "None" from the definition

Removed property `fips:County3DigitCode` and related types to eliminate many non-unique code values.

- Use `fips:CountyCode` for unique 5-digit county codes that begin with a 2-digit state code.
- See also issue ([niemopen/niem-model#59](https://github.com/niemopen/niem-model/issues/59)).

### Require definitions for patterns ([niemopen/niem-naming-design-rules#12](https://github.com/niemopen/niem-naming-design-rules/issues/12))

The NDR now requires definitions for patterns, along with enumerations.

Added the following definitions to the following patterns for simple types:

Type | Pattern | Definition
---- | ------- | ----------
`ag_codes:TaxIdentificationIDSimpleType` | `[0-9]{9}` | A 9-digit number
`ag_codes:CropYearSimpleType` | `^([1][9]\d\d\|[2]\d\d\d)$` | A 4-digit year ranging from 1900 to 2999.
`biom:LipPatternSimpleType` | `<>` | Indicator for center of the lip (left < followed by right >)
`mo:MILSTD2525-C-SIDC-SimpleType` | `[A-Z0-9\-]{15}` | A 15-character ID with upper case letters, numbers, and hyphens
`mo:MILSTD2525-B-SIDC-SimpleType` | `[A-Z0-9\-]{15}` | A 15-character ID with upper case letters, numbers, and hyphens

## Key content changes

The following is a summary of the key changes made in this release.  More details are available from the [6.0 issues list](https://github.com/niemopen/niem-model/labels/6.0) in the NIEM Model issue tracker, and the change log spreadsheet in the release package.

### Refactored other role components ([niemopen/niem-model#38](https://github.com/niemopen/niem-model/issues/38))

In addition to removing the `RoleOf` construct from the model due to NDR updates, other properties and types using the `Role` representation term were reviewed and updated as appropriate to improve consistency with the rest of the model.

**Renamed remaining RoleOf properties and types:**

Renamed additional properties and types that were using `RoleOf` as the class term but were not using the `RoleOf` construct as defined by the NDR:

Component | Original name | Updated name
--------- | ------------- | ------------
Property | it:RoleOfCategory | it:PartyIDCategory
Property | it:RoleOfCategoryDescriptionText | it:PartyRoleCategoryDescriptionText
Property | it:RoleOfOrganizationCategoryDescriptionText | it:OrganizationRoleCategoryDescriptionText
Property | it:RoleOfOrganizationCategory | it:OrganizationRoleCategory
Property | it:RoleOfOrganizationCategoryAugmentationPoint | it:OrganizationRoleCategoryAugmentationPoint
Type | it:RoleOfOrganizationCategoryType | it:OrganizationRoleCategoryType

**Removed the Role representation term:**

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

**Refactored im:PersonCountryRoleType:**

Refactored `im:PersonCountryRoleType` to make immigration status more widely available for reuse:

- Moved `im:ImmigrationStatus` from `im:PersonCountryRoleType` to `im:PersonAugmentationType`, making it available wherever `nc:PersonType` is used.
- Updated `im:PersonCountryRoleType` to extend `nc:PersonType`.

**Refactored scr:PersonRole:**

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

### Harmonized StudentType ([niemopen/niem-model#52](https://github.com/niemopen/niem-model/issues/52))

The Human Services domain and the Learning and Development domain both define type `StudentType`.  Created a new `nc:StudentType` in Core and converted the two domain types to augmentations so student properties from either domain can be used together under the same Core object.

Merged and moved the only overlapping property (`hs:StudentIdentification` / `lrn-dev:StudentID`) into Core as `nc:StudentIdentification`.

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

### Renamed Maritime domain's USMTFEnvironmentCategoryCode components ([niemopen/niem-model#23](https://github.com/niemopen/niem-model/issues/23))

The names and definitions of the following components in the Maritime domain have been updated to remove the term "USMTF", as these are no longer defined by that standard:

- `m:USMTFEnvironmentCategoryCode`
- `m:USMTFEnvironmentCategoryCodeType`
- `m:USMTFEnvironmentCategoryCodeSimpleType`

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

### Updated Bureau of Labor Statistics codes ([niemopen/niem-model#74](https://github.com/niemopen/niem-model/issues/74))

BLS occupation codes are current in NIEM as of the latest BLS SOC April 15, 2020 update.

Updated the definitions of BLS education level codes (`bls:EducationLevelCodeSimpleType`).

### Updated Canada Post codes ([niemopen/niem-model#67](https://github.com/niemopen/niem-model/issues/67))

Deleted codes from `can:StreetCategoryCodeSimpleType`:

- `AUT` - Autoroute
- `COURS` - Cours

Updated English definitions and added alternate French definitions where applicable for the following types:

- `can:CanadianProvinceCodeSimpleType`
- `can:StreetCategoryCodeSimpleType`

### Updated DEA Controlled Substance codes ([niemopen/niem-model#60](https://github.com/niemopen/niem-model/issues/60))

- Updated definitions for `dea:DEAClassScheduleCodeCodeSimpleType`
- Updated code set for `dea:DrugCodeSimpleType`
  - Added and removed codes
  - Updated existing code definitions

### Removed fips:County3DigitCode and types ([niemopen/niem-model#59](https://github.com/niemopen/niem-model/issues/59))

- Removed property `fips:County3DigitCode` and types to eliminate many non-unique code values.
  - Note: Use `fips:CountyCode` for unique 5-digit county codes.
- Changed the type from the 3-digit to the 5-digit FIPS county code for the following properties:
  - `hs:FosterCareLiablePlacementCountyCode`
  - `hs:PriorDetentionHoldingForCountyCode`

### Updated FIPS county codes ([niemopen/niem-model#75](https://github.com/niemopen/niem-model/issues/75))

NIEM FIPS state codes (`fips:USStateNumericCodeSimpleType`) are current as of the US Census Bureau's FIPS 2022 Population Estimate FIPS Codes update, Internet Release Date August 2023.

NIEM FIPS county codes (`fips:USCounty5DigitCodeSimpleType`) were updated with the latest revisions.  All changes were for the state of Connecticut.

<details markdown="1">
  <summary>Expand to see FIPS county codes changes</summary>
  <br />

  | Status  | Code  | Definition |
  |:------- |:----- |:---------- |
  removed   | 09001 | Fairfield County
  removed   | 09003 | Hartford County
  removed   | 09005 | Litchfield County
  removed   | 09007 | Middlesex County
  removed   | 09009 | New Haven County
  removed   | 09011 | New London County
  removed   | 09013 | Tolland County
  removed   | 09015 | Windham County
  added     | 09110 | Capitol Planning Region
  added     | 09120 | Greater Bridgeport Planning Region
  added     | 09130 | Lower Connecticut River Valley Planning Region
  added     | 09140 | Naugatuck Valley Planning Region
  added     | 09150 | Northeastern Connecticut Planning Region
  added     | 09160 | Northwest Hills Planning Region
  added     | 09170 | South Central Connecticut Planning Region
  added     | 09180 | Southeastern Connecticut Planning Region
  added     | 09190 | Western Connecticut Planning Region

</details>

### Updated GENC codes to version 3-12 ([niemopen/niem-model#76](https://github.com/niemopen/niem-model/issues/76))

- No changes to the country code sets (3-character, 2-character, numeric) since version 3-11
- Additions, deletions, and definition changes to the administrative subdivision codes (`genc:CountrySubdivisionCodeSimpleType`)
- Updated the GENC code lists CSV files in the `xsd/codes/genc/` subdirectory
- Note: The CSV now includes country names paired with the administrative subdivision codes rather than 3-character country codes, as this is the information that could be obtained from the data source

### Updated Hazardous Material codes ([#niemopen/niem-model#61](https://github.com/niemopen/niem-model/issues/61))

- Updated code set for `hazmat:HazmatCodeSimpleType`

### Updated ISO 639-3 language codes ([niemopen/niem-model#78](https://github.com/niemopen/niem-model/issues/78))

Updated the ISO 639-3 language codes.

### Updated ISO 3166-1:2020 country codes ([niemopen/niem-model#77](https://github.com/niemopen/niem-model/issues/77))

Updated the 3-character, 2-character, and numeric country codes with new definitions:

| 3-Char | 2-Char | Num | Old definition    | New definition |
|:------ |:------ |:--- |:----------------- | -------------- |
NLD      | NL     | 528 | Netherlands (the) | Netherlands (Kingdom of the)
TUR      | TR     | 792 | Turkey            | Türkiye

### Updated ISO 4217 currency codes ([niemopen/niem-model#79](https://github.com/niemopen/niem-model/issues/79))

Updated ISO 4217 currency codes.

### Updated usps:StreetDirectionalCodeSimpleType ([niemopen/niem-model#62](https://github.com/niemopen/niem-model/issues/62))

United States Postal Service street direction codes are the same, but the capitalization of the definitions has changed from uppercase to upper camel case.
