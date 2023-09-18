
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
