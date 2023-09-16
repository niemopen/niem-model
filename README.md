
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

### Support specifying empty value reason on simple values ([niemopen/niem-model#34](https://github.com/niemopen/niem-model/issues/34))

Created the following new attributes and added them to `nc:TextType` and `nc:QuantityType`:

- `nc:valueEmptyReasonCode` of type `nc:EmptyReasonCodeSimpleType`
- `nc:valueEmptyReasonText` of type `xs:string`

*These new attributes can also be used throughout the model with the new support for attribute wildcards in NIEM 6.0.*

Harmonized two domain code sets that represented a ternary choice with "Yes", "No", and "Unknown" code values with new code `nc:YesNoUnknownCodeType`:

- `em:TernaryIndicatorCodeType`
- `hs:JuvenileFamilyFinancialProblemCodeType`

*This new code set can be used in places where a boolean with a null value cannot be used to indicate the value is unknown or not applicable.*
