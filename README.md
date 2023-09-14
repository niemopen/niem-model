
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

### Updated Minimum Essential Metadata in MilOps ([niemopen/niem-model#40](https://github.com/niemopen/niem-model/issues/40))

The DoD Minimum Essential Metadata were updated by DoD Metadata Guidance issued by the DoD Chief Digital and Artificial Intelligence Officer in March 2023.   The following changes have been made:

- Updated the definitions of property `mo:MinimumEssentialMetadata` and type `mo:MinimumEssentialMetadataType`.
- Renamed property `mo:LegalAuthority` as `mo:AuthorizationReference` and changed its type to `nc:DocumentType`.
- Removed type `mo:LegalAuthorityType`.
- Renamed property `mo:Creator` as `mo:ResourceOriginator` and updated its definition.
- Renamed property `mo:OfficeOfRecord` as `mo:DataResourceCustodian` and updated its definition.
- Added new property `mo:DataItemCreateDateTime` to type `mo:MinimumEssentialMetadataType`.
- Added existing property `nc:DescriptionText` to type `mo:MinimumEssentialMetadataType`.
