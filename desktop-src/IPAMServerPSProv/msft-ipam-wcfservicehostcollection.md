---
Description: 'Represents a collection of Windows Communication Foundation (WCF) service hosts.'
audience: developer
author: 'REDMOND\\markl'
manager: 'REDMOND\\markl'
ms.assetid: '08c88e6f-be34-4754-8ec5-ef79cfc9cd3d'
ms.prod: 'windows-server-dev'
ms.technology:
- 'internet-protocol-address-management'
- 'windows-management-instrumentation'
ms.tgt_platform: multiple
title: 'MSFT\_IPAM\_WCFServiceHostCollection class'
---

# MSFT\_IPAM\_WCFServiceHostCollection class

Represents a collection of Windows Communication Foundation (WCF) service hosts.

The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.

## Syntax

``` syntax
[UMLPackagePath("CIM::Core::Collection"), ClassVersion("1.0.0"), dynamic, provider("IPAMServerPSProvider"), AMENDMENT]
class MSFT_IPAM_WCFServiceHostCollection : CIM_Collection
{
  string InstanceID;
  string Caption;
  string Description;
  string ElementName;
};
```

## Members

The **MSFT\_IPAM\_WCFServiceHostCollection** class has these types of members:

-   [Methods](#methods)
-   [Properties](#properties)

### Methods

The **MSFT\_IPAM\_WCFServiceHostCollection** class has these methods.



| Method                                                                              | Description                                                                        |
|:------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------|
| [**SetHostIdleTimeout**](sethostidletimeout-msft-ipam-wcfservicehostcollection.md) | Updates the timeout duration of a WCF service host.<br/>                     |
| [**StartAllHosts**](startallhosts-msft-ipam-wcfservicehostcollection.md)           | Creates WCF service host endpoints, and opens them for communication.<br/>   |
| [**StopAllHosts**](stopallhosts-msft-ipam-wcfservicehostcollection.md)             | Closes all of the WCF service host endpoints in IPAM, and deletes them.<br/> |



�

### Properties

The **MSFT\_IPAM\_WCFServiceHostCollection** class has these properties.

<dl> <dt>

**Caption**
</dt> <dd> <dl> <dt>

Data type: **string**
</dt> <dt>

Access type: Read-only
</dt> <dt>

Qualifiers: [**MaxLen**](https://msdn.microsoft.com/library/aa393650) (64)
</dt> </dl>

The Caption property is a short textual description (one- line string) of the object.

This property is inherited from [**CIM\_ManagedElement**](cim-managedelement.md).

</dd> <dt>

**Description**
</dt> <dd> <dl> <dt>

Data type: **string**
</dt> <dt>

Access type: Read-only
</dt> </dl>

The Description property provides a textual description of the object.

This property is inherited from [**CIM\_ManagedElement**](cim-managedelement.md).

</dd> <dt>

**ElementName**
</dt> <dd> <dl> <dt>

Data type: **string**
</dt> <dt>

Access type: Read-only
</dt> </dl>

A user-friendly name for the object. This property allows each instance to define a user-friendly name in addition to its key properties, identity data, and description information.

This property is inherited from [**CIM\_ManagedElement**](cim-managedelement.md).

</dd> <dt>

**InstanceID**
</dt> <dd> <dl> <dt>

Data type: **string**
</dt> <dt>

Access type: Read-only
</dt> </dl>

An optional property that may be used to opaquely and uniquely identify an instance of this class within the scope of the instantiating Namespace. Various subclasses of this class may override this property to make it required, or a key. Such subclasses may also modify the preferred algorithms for ensuring uniqueness that are defined below.

To ensure uniqueness within the namespace, the value of *InstanceID* should be constructed using the following "preferred" algorithm:

&lt;OrgID&gt;:&lt;LocalID&gt;

Where &lt;OrgID&gt; and &lt;LocalID&gt; are separated by a colon (:), and where &lt;OrgID&gt; must include a copyrighted, trademarked, or otherwise unique name that is owned by the business entity that is creating or defining the InstanceID or that is a registered ID assigned to the business entity by a recognized global authority. (This requirement is similar to the &lt;Schema Name&gt;\_&lt;Class Name&gt; structure of schema class names.) In addition, to ensure uniqueness, &lt;OrgID&gt; must not contain a colon (:). When using this algorithm, the first colon to appear in *InstanceID* must appear between &lt;OrgID&gt; and &lt;LocalID&gt;.

&lt;LocalID&gt; is chosen by the business entity and should not be reused to identify different underlying (real-world) elements. If not null and the above "preferred" algorithm is not used, the defining entity must assure that the resulting *InstanceID* is not reused across any *InstanceID*s produced by this or other providers for the namespace of this instance.

If not set to null for DMTF-defined instances, the "preferred" algorithm must be used with the &lt;OrgID&gt; set to CIM.

This property is inherited from [**CIM\_ManagedElement**](cim-managedelement.md).

</dd> </dl>

## Requirements



|                                     |                                                                                                     |
|-------------------------------------|-----------------------------------------------------------------------------------------------------|
| Minimum supported client<br/> | None supported<br/>                                                                           |
| Minimum supported server<br/> | Windows Server�2012�R2<br/>                                                                   |
| Namespace<br/>                | Root\\Microsoft\\IPAM<br/>                                                                    |
| MOF<br/>                      | <dl> <dt>IPAMServerPSProvider.mof</dt> </dl> |
| DLL<br/>                      | <dl> <dt>IPAMServerPSProvider.dll</dt> </dl> |



�

�



