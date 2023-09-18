
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

#### Updated CBRN CaseMetadata and DataFileMetadata to have type nc:MetadataType ([niemopen/niem-model#24](https://github.com/niemopen/niem-model/issues/24))

CBRN defines two metadata elements that have type `structures:MetadataType`:

- `cbrn:CaseMetadata`
- `cbrn:DataFileMetadata`, which are both of type structures:MetadataType.

The `structures:MetadataType` does not carry content and is not meant to be used directly as a type of a property.

Updated these two properties to have type `nc:MetadataType`.

#### Refactored cbrn:ReportType into an augmentation of nc:ReportType ([niemopen/niem-model#11](https://github.com/niemopen/niem-model/issues/11))

Refactored the following in `cbrn:ReportType`:

- `cbrn:ReportDateTime`
- `cbrn:CredentialsAuthenticationAbstract`
- `nc:ActivityName`
- `cbrn:ReportAugmentationPoint`

into an augmentation of `nc:ReportType`, making these properties more reusable.

Removed property `cbrn:ReportDateTime` ("A DateTime when a report was created.") as it is no longer needed with `nc:DocumentCreationDate` available through `nc:DocumentType`, the parent type of `nc:ReportType`.
