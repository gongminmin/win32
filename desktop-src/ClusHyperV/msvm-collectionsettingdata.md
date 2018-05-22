---
title: Msvm\_CollectionSettingData class
description: Represents the configured settings for an Msvm\_VirtualSystemCollection object.
audience: developer
author: REDMOND\\markl
manager: REDMOND\\markl
ms.assetid: '5871b146-b3aa-436a-9872-12c8ebac3940'
ms.prod: 'windows-server-dev'
ms.technology:
- 'failover-cluster-hyperv'
- 'windows-management-instrumentation'
ms.tgt_platform: multiple
keywords: ["Msvm_CollectionSettingData class", "Msvm_CollectionSettingData class, described"]
topic_type:
- apiref
api_name:
- Msvm_CollectionSettingData
- Msvm_CollectionSettingData.Caption
- Msvm_CollectionSettingData.Description
- Msvm_CollectionSettingData.InstanceID
- Msvm_CollectionSettingData.ElementName
api_location:
- VMMS.exe
api_type:
- DllExport
---

# Msvm\_CollectionSettingData class

Represents the configured settings for an [**Msvm\_VirtualSystemCollection**](msvm-virtualsystemcollection.md) object.

The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.

## Syntax

``` syntax
[Abstract, AMENDMENT]
class Msvm_CollectionSettingData : CIM_SettingData
{
  string Caption;
  string Description;
  string InstanceID;
  string ElementName;
};
```

## Members

The **Msvm\_CollectionSettingData** class has these types of members:

-   [Properties](#properties)

### Properties

The **Msvm\_CollectionSettingData** class has these properties.

<dl> <dt>

**Caption**
</dt> <dd> <dl> <dt>

Data type: **string**
</dt> <dt>

Access type: Read-only
</dt> <dt>

Qualifiers: [**MaxLen**](https://msdn.microsoft.com/library/aa393650) (64)
</dt> </dl>

A short textual description of the object.

This property is inherited from [**CIM\_ManagedElement**](cim-managedelement.md).

</dd> <dt>

**Description**
</dt> <dd> <dl> <dt>

Data type: **string**
</dt> <dt>

Access type: Read-only
</dt> </dl>

A textual description of the object.

This property is inherited from [**CIM\_ManagedElement**](cim-managedelement.md).

</dd> <dt>

**ElementName**
</dt> <dd> <dl> <dt>

Data type: **string**
</dt> <dt>

Access type: Read-only
</dt> <dt>

Qualifiers: [**Required**](https://msdn.microsoft.com/library/aa393650)
</dt> </dl>

The user-friendly name for an instance of this class. In addition, the user-friendly name can be used as an index for a search or query. The name does not have to be unique within a namespace.

This property is inherited from [**CIM\_SettingData**](cim-settingdata.md).

</dd> <dt>

**InstanceID**
</dt> <dd> <dl> <dt>

Data type: **string**
</dt> <dt>

Access type: Read-only
</dt> <dt>

Qualifiers: [**Key**](https://msdn.microsoft.com/library/aa392157)
</dt> </dl>

Uniquely identifies an instance of this class within the scope of the containing namespace.

> \[!Important\]
>
> In order to ensure uniqueness within the namespace, the value of the **InstanceID** property should be constructed in the following pattern: *OrgID*:*LocalID*
>
> -   *OrgID* must include a copyrighted, trademarked or otherwise unique name that is owned by the business entity that defines the **InstanceID** property, or be a registered ID that is assigned by a recognized global authority.
> -   *OrgID* must not contain a colon. The first colon in **InstanceID** must be between the *OrgID* and*LocalID*.
> -   *LocalID* is chosen by the business entity and should not be re-used to identify different underlying real-world elements.
> -   If the above pattern is not used, the defining entity must assure that the resultant **InstanceID** value is not re-used across any **InstanceID** properties that are produced by this provider or other providers for this namespace.
> -   For DMTF defined instances, the pattern must be used with the *OrgID* set to "CIM".

�

This property is inherited from [**CIM\_SettingData**](cim-settingdata.md).

</dd> </dl>

## Requirements



|                                     |                                                                                                        |
|-------------------------------------|--------------------------------------------------------------------------------------------------------|
| Minimum supported client<br/> | None supported<br/>                                                                              |
| Minimum supported server<br/> | Windows Server�2016<br/>                                                                         |
| Namespace<br/>                | Root\\HyperVCluster\\v2<br/>                                                                     |
| MOF<br/>                      | <dl> <dt>WindowsHyperVCluster.V2.mof</dt> </dl> |
| DLL<br/>                      | <dl> <dt>VMMS.exe</dt> </dl>                    |



## See also

<dl> <dt>

[**CIM\_SettingData**](cim-settingdata.md)
</dt> </dl>

�

�




