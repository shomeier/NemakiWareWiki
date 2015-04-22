---
##What is an object type?
CMIS object type is to a CMIS object what "class" is to an "instance" in the object-oriented language.  
Object type has:
- a set of properties(metadata) definitions
- attributes of the type itself

CMIS server predefines some basic types such as `cmis:document` and `cmis:folder`.
You can add your own customized object types extending these basic types, adding custom property fields and overriding attributes.

###Property definitions
ex. cmis:name, cmis:description, cmis:creationDate etc.

###Attributes
ex. type ID, queryable, contentStreamAllowed, versionable etc.

##Type inheritance
Customized object type has to be defined as a child of a basic type or another customized type which is already defined.  

##How to create a new customized type?
If you are an administrator, object type administration button should be showed on the top header in the interface.  
You can upload a definition file(JSON) to create a new type.

Don't fear for writing a definition file from scratch!  
Definition files can be downloaded from object type administration UI, and you can edit them.

###Existing type definition file (ex.`cmis:document`)
```
{
    "id": "cmis:document",
    "localName": "cmis:document",
    "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
    "displayName": "cmis:document",
    "queryName": "cmis:document",
    "description": "cmis:document",
    "baseId": "cmis:document",
    "creatable": true,
    "fileable": true,
    "queryable": true,
    "fulltextIndexed": true,
    "includedInSupertypeQuery": true,
    "controllablePolicy": false,
    "controllableACL": true,
    "typeMutability": {
        "create": true,
        "update": false,
        "delete": false
    },
    "versionable": true,
    "contentStreamAllowed": "required",
    "propertyDefinitions": {
        "cmis:name": {
            "id": "cmis:name",
            "localName": "cmis:name",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:name",
            "queryName": "cmis:name",
            "description": "cmis:name",
            "propertyType": "string",
            "cardinality": "single",
            "updatability": "readwrite",
            "inherited": false,
            "required": true,
            "queryable": true,
            "orderable": true,
            "openChoice": false
        },
        "cmis:description": {
            "id": "cmis:description",
            "localName": "cmis:description",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:description",
            "queryName": "cmis:description",
            "description": "cmis:description",
            "propertyType": "string",
            "cardinality": "single",
            "updatability": "readwrite",
            "inherited": false,
            "required": false,
            "queryable": true,
            "orderable": true,
            "openChoice": false
        },
        "cmis:objectId": {
            "id": "cmis:objectId",
            "localName": "cmis:objectId",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:objectId",
            "queryName": "cmis:objectId",
            "description": "cmis:objectId",
            "propertyType": "id",
            "cardinality": "single",
            "updatability": "readonly",
            "inherited": false,
            "required": false,
            "queryable": true,
            "orderable": true,
            "openChoice": false
        },
        "cmis:baseTypeId": {
            "id": "cmis:baseTypeId",
            "localName": "cmis:baseTypeId",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:baseTypeId",
            "queryName": "cmis:baseTypeId",
            "description": "cmis:baseTypeId",
            "propertyType": "id",
            "cardinality": "single",
            "updatability": "readonly",
            "inherited": false,
            "required": false,
            "queryable": true,
            "orderable": true,
            "openChoice": false
        },
        "cmis:objectTypeId": {
            "id": "cmis:objectTypeId",
            "localName": "cmis:objectTypeId",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:objectTypeId",
            "queryName": "cmis:objectTypeId",
            "description": "cmis:objectTypeId",
            "propertyType": "id",
            "cardinality": "single",
            "updatability": "oncreate",
            "inherited": false,
            "required": true,
            "queryable": true,
            "orderable": true,
            "openChoice": false
        },
        "cmis:secondaryObjectTypeIds": {
            "id": "cmis:secondaryObjectTypeIds",
            "localName": "cmis:secondaryObjectTypeIds",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:secondaryObjectTypeIds",
            "queryName": "cmis:secondaryObjectTypeIds",
            "description": "cmis:secondaryObjectTypeIds",
            "propertyType": "id",
            "cardinality": "multi",
            "updatability": "readwrite",
            "inherited": false,
            "required": false,
            "queryable": true,
            "orderable": false,
            "openChoice": false
        },
        "cmis:createdBy": {
            "id": "cmis:createdBy",
            "localName": "cmis:createdBy",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:createdBy",
            "queryName": "cmis:createdBy",
            "description": "cmis:createdBy",
            "propertyType": "string",
            "cardinality": "single",
            "updatability": "readonly",
            "inherited": false,
            "required": false,
            "queryable": true,
            "orderable": true,
            "openChoice": false
        },
        "cmis:creationDate": {
            "id": "cmis:creationDate",
            "localName": "cmis:creationDate",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:creationDate",
            "queryName": "cmis:creationDate",
            "description": "cmis:creationDate",
            "propertyType": "datetime",
            "cardinality": "single",
            "updatability": "readonly",
            "inherited": false,
            "required": false,
            "queryable": true,
            "orderable": true,
            "openChoice": false
        },
        "cmis:lastModifiedBy": {
            "id": "cmis:lastModifiedBy",
            "localName": "cmis:lastModifiedBy",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:lastModifiedBy",
            "queryName": "cmis:lastModifiedBy",
            "description": "cmis:lastModifiedBy",
            "propertyType": "string",
            "cardinality": "single",
            "updatability": "readonly",
            "inherited": false,
            "required": false,
            "queryable": true,
            "orderable": true,
            "openChoice": false
        },
        "cmis:lastModificationDate": {
            "id": "cmis:lastModificationDate",
            "localName": "cmis:lastModificationDate",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:lastModificationDate",
            "queryName": "cmis:lastModificationDate",
            "description": "cmis:lastModificationDate",
            "propertyType": "datetime",
            "cardinality": "single",
            "updatability": "readonly",
            "inherited": false,
            "required": false,
            "queryable": true,
            "orderable": true,
            "openChoice": false
        },
        "cmis:changeToken": {
            "id": "cmis:changeToken",
            "localName": "cmis:changeToken",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:changeToken",
            "queryName": "cmis:changeToken",
            "description": "cmis:changeToken",
            "propertyType": "string",
            "cardinality": "single",
            "updatability": "readonly",
            "inherited": false,
            "required": false,
            "queryable": false,
            "orderable": false,
            "openChoice": false
        },
        "cmis:isImmutable": {
            "id": "cmis:isImmutable",
            "localName": "cmis:isImmutable",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:isImmutable",
            "queryName": "cmis:isImmutable",
            "description": "cmis:isImmutable",
            "propertyType": "boolean",
            "cardinality": "single",
            "updatability": "readonly",
            "inherited": false,
            "required": false,
            "queryable": false,
            "orderable": true,
            "openChoice": false
        },
        "cmis:isLatestVersion": {
            "id": "cmis:isLatestVersion",
            "localName": "cmis:isLatestVersion",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:isLatestVersion",
            "queryName": "cmis:isLatestVersion",
            "description": "cmis:isLatestVersion",
            "propertyType": "boolean",
            "cardinality": "single",
            "updatability": "readonly",
            "inherited": false,
            "required": false,
            "queryable": false,
            "orderable": true,
            "openChoice": false
        },
        "cmis:isMajorVersion": {
            "id": "cmis:isMajorVersion",
            "localName": "cmis:isMajorVersion",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:isMajorVersion",
            "queryName": "cmis:isMajorVersion",
            "description": "cmis:isMajorVersion",
            "propertyType": "boolean",
            "cardinality": "single",
            "updatability": "readonly",
            "inherited": false,
            "required": false,
            "queryable": true,
            "orderable": true,
            "openChoice": false
        },
        "cmis:isLatestMajorVersion": {
            "id": "cmis:isLatestMajorVersion",
            "localName": "cmis:isLatestMajorVersion",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:isLatestMajorVersion",
            "queryName": "cmis:isLatestMajorVersion",
            "description": "cmis:isLatestMajorVersion",
            "propertyType": "boolean",
            "cardinality": "single",
            "updatability": "readonly",
            "inherited": false,
            "required": false,
            "queryable": true,
            "orderable": true,
            "openChoice": false
        },
        "cmis:isPrivateWorkingCopy": {
            "id": "cmis:isPrivateWorkingCopy",
            "localName": "cmis:isPrivateWorkingCopy",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:isPrivateWorkingCopy",
            "queryName": "cmis:isPrivateWorkingCopy",
            "description": "cmis:isPrivateWorkingCopy",
            "propertyType": "boolean",
            "cardinality": "single",
            "updatability": "readonly",
            "inherited": false,
            "required": false,
            "queryable": true,
            "orderable": true,
            "openChoice": false
        },
        "cmis:versionLabel": {
            "id": "cmis:versionLabel",
            "localName": "cmis:versionLabel",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:versionLabel",
            "queryName": "cmis:versionLabel",
            "description": "cmis:versionLabel",
            "propertyType": "string",
            "cardinality": "single",
            "updatability": "readonly",
            "inherited": false,
            "required": false,
            "queryable": true,
            "orderable": true,
            "openChoice": false
        },
        "cmis:versionSeriesId": {
            "id": "cmis:versionSeriesId",
            "localName": "cmis:versionSeriesId",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:versionSeriesId",
            "queryName": "cmis:versionSeriesId",
            "description": "cmis:versionSeriesId",
            "propertyType": "id",
            "cardinality": "single",
            "updatability": "readonly",
            "inherited": false,
            "required": false,
            "queryable": true,
            "orderable": true,
            "openChoice": false
        },
        "cmis:isVersionSeriesCheckedOut": {
            "id": "cmis:isVersionSeriesCheckedOut",
            "localName": "cmis:isVersionSeriesCheckedOut",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:isVersionSeriesCheckedOut",
            "queryName": "cmis:isVersionSeriesCheckedOut",
            "description": "cmis:isVersionSeriesCheckedOut",
            "propertyType": "boolean",
            "cardinality": "single",
            "updatability": "readonly",
            "inherited": false,
            "required": false,
            "queryable": true,
            "orderable": true,
            "openChoice": false
        },
        "cmis:versionSeriesCheckedOutBy": {
            "id": "cmis:versionSeriesCheckedOutBy",
            "localName": "cmis:versionSeriesCheckedOutBy",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:versionSeriesCheckedOutBy",
            "queryName": "cmis:versionSeriesCheckedOutBy",
            "description": "cmis:versionSeriesCheckedOutBy",
            "propertyType": "string",
            "cardinality": "single",
            "updatability": "readonly",
            "inherited": false,
            "required": false,
            "queryable": true,
            "orderable": true,
            "openChoice": false
        },
        "cmis:versionSeriesCheckedOutId": {
            "id": "cmis:versionSeriesCheckedOutId",
            "localName": "cmis:versionSeriesCheckedOutId",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:versionSeriesCheckedOutId",
            "queryName": "cmis:versionSeriesCheckedOutId",
            "description": "cmis:versionSeriesCheckedOutId",
            "propertyType": "id",
            "cardinality": "single",
            "updatability": "readonly",
            "inherited": false,
            "required": false,
            "queryable": true,
            "orderable": true,
            "openChoice": false
        },
        "cmis:checkinComment": {
            "id": "cmis:checkinComment",
            "localName": "cmis:checkinComment",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:checkinComment",
            "queryName": "cmis:checkinComment",
            "description": "cmis:checkinComment",
            "propertyType": "string",
            "cardinality": "single",
            "updatability": "readonly",
            "inherited": false,
            "required": false,
            "queryable": true,
            "orderable": true,
            "openChoice": false
        },
        "cmis:contentStreamLength": {
            "id": "cmis:contentStreamLength",
            "localName": "cmis:contentStreamLength",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:contentStreamLength",
            "queryName": "cmis:contentStreamLength",
            "description": "cmis:contentStreamLength",
            "propertyType": "integer",
            "cardinality": "single",
            "updatability": "readonly",
            "inherited": false,
            "required": false,
            "queryable": true,
            "orderable": true,
            "openChoice": false
        },
        "cmis:contentStreamMimeType": {
            "id": "cmis:contentStreamMimeType",
            "localName": "cmis:contentStreamMimeType",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:contentStreamMimeType",
            "queryName": "cmis:contentStreamMimeType",
            "description": "cmis:contentStreamMimeType",
            "propertyType": "string",
            "cardinality": "single",
            "updatability": "readonly",
            "inherited": false,
            "required": false,
            "queryable": true,
            "orderable": true,
            "openChoice": false
        },
        "cmis:contentStreamFileName": {
            "id": "cmis:contentStreamFileName",
            "localName": "cmis:contentStreamFileName",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:contentStreamFileName",
            "queryName": "cmis:contentStreamFileName",
            "description": "cmis:contentStreamFileName",
            "propertyType": "string",
            "cardinality": "single",
            "updatability": "readonly",
            "inherited": false,
            "required": false,
            "queryable": true,
            "orderable": true,
            "openChoice": false
        },
        "cmis:contentStreamId": {
            "id": "cmis:contentStreamId",
            "localName": "cmis:contentStreamId",
            "localNamespace": "http:\\/\\/www.aegif.jp\\/NemakiWare\\/",
            "displayName": "cmis:contentStreamId",
            "queryName": "cmis:contentStreamId",
            "description": "cmis:contentStreamId",
            "propertyType": "id",
            "cardinality": "single",
            "updatability": "readonly",
            "inherited": false,
            "required": false,
            "queryable": true,
            "orderable": true,
            "openChoice": false
        }
    }
}
```

###New type definition file(sample)
Thanks to type inheritance, most of attributes and all property definitions can be left out.  
You must write them explicitly only when you want to override or add some parameter.

```
{
    "id": "nemaki:document",
    "localName": "nemaki:document",
    "localNamespace":,
    "displayName": "nemaki customized document",
    "queryName": "nemaki:document",
    "description": "nemaki document's description",
    "baseId": "cmis:document",
    "contentStreamAllowed": "allowed",
    "propertyDefinitions": {
        "nemaki:tag": {
            "id": "nemaki:tag",
            "localName": "nemaki:tag",
            "localNamespace": ,
            "displayName": "nemaki:tag",
            "queryName": "nemaki:tag",
            "description": "nemaki:tag",
            "propertyType": "string",
            "cardinality": "multi",
            "updatability": "readwrite",
            "inherited": false,
            "required": false,
            "queryable": true,
            "orderable": false,
            "openChoice": false
        }
    }
}
```

##Primary object type / Secondary object type
Object type such as cmis::document and cmis:folder is basically primary type, but there are special types called "secondary" object types.  
Secondary type corresponds to "aspect". It can be taken on/off to an object with its complementary property definitions. 

Every secondary type is defined as what inherits `cmis:secondary` type.  
A secondary type can be defined by a json file above mentioned.  
To apply a secondary type to an object, update property `cmis:scondaryObjectTypesIds` of the object with the secondary type's ID.