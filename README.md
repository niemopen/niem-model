
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
- `em:NotificationFunctionCategoryCodeSimpleType`
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

### Code set updates

#### Removed fips:County3DigitCode and types ([niemopen/niem-model#59](https://github.com/niemopen/niem-model/issues/59))

- Removed property `fips:County3DigitCode` and types to eliminate many non-unique code values.
  - Note: Use `fips:CountyCode` for unique 5-digit county codes.
- Changed the type from the 3-digit to the 5-digit FIPS county code for the following properties:
  - `hs:FosterCareLiablePlacementCountyCode`
  - `hs:PriorDetentionHoldingForCountyCode`
