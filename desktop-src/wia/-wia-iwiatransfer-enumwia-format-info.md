﻿---
Description: 'Creates an enumerator for the transfer formats that the Windows Image Acquisition (WIA) 2.0 device supports.'
ms.assetid: '70fffc7b-b500-4404-9d94-76d1828ddc8c'
title: 'IWiaTransfer::EnumWIA\_FORMAT\_INFO method'
---

# IWiaTransfer::EnumWIA\_FORMAT\_INFO method

Creates an enumerator for the transfer formats that the Windows Image Acquisition (WIA) 2.0 device supports.

## Syntax


```C++
HRESULT EnumWIA_FORMAT_INFO(
  [out] IEnumWIA_FORMAT_INFO **ppIEnum
);
```



## Parameters

<dl> <dt>

*ppIEnum* \[out\]
</dt> <dd>

Type: **[**IEnumWIA\_FORMAT\_INFO**](-wia-ienumwia-format-info.md)\*\***

The address of the pointer to the [**IEnumWIA\_FORMAT\_INFO**](-wia-ienumwia-format-info.md) interface for the enumerator.

</dd> </dl>

## Return value

Type: **HRESULT**

If this method succeeds, it returns **S\_OK**. Otherwise, it returns an **HRESULT** error code.

## Remarks

Applications must call the [IUnknown::Release](com.iunknown_release) method on the interface pointer received through the *ppIEnum* parameter.

## Requirements



|                                     |                                                                                        |
|-------------------------------------|----------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows Vista \[desktop apps only\]<br/>                                         |
| Minimum supported server<br/> | Windows Server 2008 \[desktop apps only\]<br/>                                   |
| Header<br/>                   | <dl> <dt>Wia.h</dt> </dl>       |
| IDL<br/>                      | <dl> <dt>Wia.idl</dt> </dl>     |
| Library<br/>                  | <dl> <dt>Wiaguid.lib</dt> </dl> |



 

 



