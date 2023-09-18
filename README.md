
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

## Refactored metadata as regular NIEM components ([niemopen/niem-naming-design-rules#8](https://github.com/niemopen/niem-naming-design-rules/issues/8))

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
