---
Description: 'The fax service calls the FaxDevReportStatus function asynchronously to query a fax service provider (FSP) DLL about status information for an active fax operation, or for status information after a failed fax operation.'
ms.assetid: '04a2154b-cde5-4c37-97a1-44dd4e12f172'
title: Obtaining a Fax Status
---

# Obtaining a Fax Status

The fax service calls the [**FaxDevReportStatus**](-mfax-faxdevreportstatus.md) function asynchronously to query a fax service provider (FSP) DLL about status information for an active fax operation, or for status information after a failed fax operation. The service also calls **FaxDevReportStatus** synchronously at the end of each job. The [**FAX\_DEVICE\_STATUS**](-mfax-fax-device-status-str.md) structure contains a status error code, a Microsoft Win32 error code, and routing information for the fax operation.

The FSP must export the [**FaxDevReportStatus**](-mfax-faxdevreportstatus.md) function.

 

 


