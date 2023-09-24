
# NIEM 6.0

This is the NIEM 6.0 major release.

In a major version, content may be updated in any namespace, including Core. Changes may also be made to the NIEM architecture, which may be reflected in the structure and layout of the NIEM schemas.

## Key changes

The following is a summary of the key changes made in this release.  More details are available from the [6.0 issues list](https://github.com/niemopen/niem-model/labels/6.0) in the NIEM Model issue tracker, and the change log spreadsheet in the release package.

### Naming and Design Rules (NDR) 6.0 updates

The following are the key changes made to the model based on updates to the NDR.

#### Updated namespace URIs ([niemopen/niem-model#25](https://github.com/niemopen/niem-model/issues/25))

NIEM is now an OASIS Open Project.  URIs for each namespace have been updated to follow the [OASIS Naming Directives, XML Namespace Identifiers and Namespace Documents](http://docs.oasis-open.org/specGuidelines/ndr/namingDirectives.html#xml-namespaces).

```xml
<!-- URI for NIEM Core from 5.2 -->
<xs:schema targetNamespace="http://release.niem.gov/niem/niem-core/5.0/" ...>

<!-- URI for NIEM Core for 6.0 -->
<xs:schema targetNamespace="https://docs.oasis-open.org/niemopen/ns/model/niem-core/6.0/" ...>
```

#### Require unique enumerations ([niemopen/niem-naming-design-rules#30](https://github.com/niemopen/niem-naming-design-rules/issues/30))

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

#### Require definitions for patterns ([niemopen/niem-naming-design-rules#12](https://github.com/niemopen/niem-naming-design-rules/issues/12))

The NDR now requires definitions for patterns, along with enumerations.

Added the following definitions to the following patterns for simple types:

Type | Pattern | Definition
---- | ------- | ----------
`ag_codes:TaxIdentificationIDSimpleType` | `[0-9]{9}` | A 9-digit number
`ag_codes:CropYearSimpleType` | `^([1][9]\d\d\|[2]\d\d\d)$` | A 4-digit year ranging from 1900 to 2999.
`biom:LipPatternSimpleType` | `<>` | Indicator for center of the lip (left < followed by right >)
`mo:MILSTD2525-C-SIDC-SimpleType` | `[A-Z0-9\-]{15}` | A 15-character ID with upper case letters, numbers, and hyphens
`mo:MILSTD2525-B-SIDC-SimpleType` | `[A-Z0-9\-]{15}` | A 15-character ID with upper case letters, numbers, and hyphens

### Code set updates

### Updated Bureau of Labor Statistics codes ([niemopen/niem-model#74](https://github.com/niemopen/niem-model/issues/74))

BLS occupation codes are current in NIEM as of the latest BLS SOC April 15, 2020 update.

Updated the definitions of BLS education level codes (`bls:EducationLevelCodeSimpleType`).

#### Updated Canada Post codes ([niemopen/niem-model#67](https://github.com/niemopen/niem-model/issues/67))

Deleted codes from `can:StreetCategoryCodeSimpleType`:

- `AUT` - Autoroute
- `COURS` - Cours

Updated English definitions and added alternate French definitions where applicable for the following types:

- `can:CanadianProvinceCodeSimpleType`
- `can:StreetCategoryCodeSimpleType`

#### Updated DEA Controlled Substance codes ([niemopen/niem-model#60](https://github.com/niemopen/niem-model/issues/60))

- Updated definitions for `dea:DEAClassScheduleCodeCodeSimpleType`
- Updated code set for `dea:DrugCodeSimpleType`
  - Added and removed codes
  - Updated existing code definitions

#### Removed fips:County3DigitCode and types ([niemopen/niem-model#59](https://github.com/niemopen/niem-model/issues/59))

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

#### Updated GENC codes to version 3-12 ([niemopen/niem-model#76](https://github.com/niemopen/niem-model/issues/76))

- No changes to the country code sets (3-character, 2-character, numeric) since version 3-11
- Additions, deletions, and definition changes to the administrative subdivision codes (`genc:CountrySubdivisionCodeSimpleType`)
- Updated the GENC code lists CSV files in the `xsd/codes/genc/` subdirectory
- Note: The CSV now includes country names paired with the administrative subdivision codes rather than 3-character country codes, as this is the information that could be obtained from the data source

#### Updated Hazardous Material codes ([#niemopen/niem-model#61](https://github.com/niemopen/niem-model/issues/61))

- Updated code set for `hazmat:HazmatCodeSimpleType`

#### Updated ISO 3166-1:2020 country codes ([niemopen/niem-model#77](https://github.com/niemopen/niem-model/issues/77))

Updated the 3-character, 2-character, and numeric country codes with new definitions:

| 3-Char | 2-Char | Num | Old definition    | New definition |
|:------ |:------ |:--- |:----------------- | -------------- |
NLD      | NL     | 528 | Netherlands (the) | Netherlands (Kingdom of the)
TUR      | TR     | 792 | Turkey            | Türkiye

#### Updated usps:StreetDirectionalCodeSimpleType ([niemopen/niem-model#62](https://github.com/niemopen/niem-model/issues/62))

United States Postal Service street direction codes are the same, but the capitalization of the definitions has changed from uppercase to upper camel case.
