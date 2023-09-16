
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

## Key content changes

The following is a summary of the key changes made in this release.  More details are available from the [6.0 issues list](https://github.com/niemopen/niem-model/labels/6.0) in the NIEM Model issue tracker, and the change log spreadsheet in the release package.

### Harmonized AAMVA country code sets supporting the DHS Western Hemisphere Travel Initiative (WHTI) for the Enhanced Driver License (EDL)

Harmonized duplicate code sets into a single `aamva_d20:CountryWHTICodeType`:

- `aamva_d20:CountryCodeType`
- `aamva_d20:DHSDriverLicenseIssuingCountryCodeType`

Updated type of property `j:CountryWHTICode` to the new type.

Removed property `j:DriverLicenseIssuingCountryCode` since it will no longer be necessary with the full set of NIEM country representations available via `nc:CountryType`. See [niemopen/niem-model#22](https://github.com/niemopen/niem-model/issues/22) for more.

### Refactored abstract country properties to be of type nc:CountryType ([#niemopen/niem-model#22](https://github.com/niemopen/niem-model/issues/22))

Updated the following properties to no longer be abstract and to have type `nc:CountryType`, permitting any country representations in NIEM to be used:

- intel:IdentificationIssuingCountryAbstract
- j:DriverLicenseIssuingCountryAbstract
- mo:ObservedObjectAllegianceCountryAbstract
