---
Description: 'The DeliverEndFlush method requests the connected input pin to end a flush operation.'
ms.assetid: '9f1fd76c-dba7-41c5-b098-9735e4f2571b'
title: 'CBaseOutputPin.DeliverEndFlush method'
---

# CBaseOutputPin.DeliverEndFlush method

The `DeliverEndFlush` method requests the connected input pin to end a flush operation.

## Syntax


```C++
virtual HRESULT DeliverEndFlush();
```



## Parameters

This method has no parameters.

## Return value

Returns an **HRESULT** value. Possible values include those listed in the following table.



| Return code                                                                                           | Description                      |
|-------------------------------------------------------------------------------------------------------|----------------------------------|
| <dl> <dt>**S\_OK**</dt> </dl>                  | Success.<br/>              |
| <dl> <dt>**VFW\_E\_NOT\_CONNECTED**</dt> </dl> | Pin is not connected.<br/> |



�

## Remarks

This method calls the [**IPin::EndFlush**](ipin-endflush.md) method on the input pin.

## Requirements



|                    |                                                                                                                                                                                            |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>Amfilter.h (include Streams.h)</dt> </dl>                                                                                  |
| Library<br/> | <dl> <dt>Strmbase.lib (retail builds); </dt> <dt>Strmbasd.lib (debug builds)</dt> </dl> |



## See also

<dl> <dt>

[**CBaseOutputPin Class**](cbaseoutputpin.md)
</dt> </dl>

�

�



