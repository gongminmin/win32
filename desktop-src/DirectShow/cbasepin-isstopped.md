---
Description: The IsStopped method determines whether the filter containing this pin is stopped.
ms.assetid: ffeac352-2f9b-44be-a8e8-7e9238d0b18e
title: CBasePin.IsStopped method
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# CBasePin.IsStopped method

The `IsStopped` method determines whether the filter containing this pin is stopped.

## Syntax


```C++
BOOL IsStopped();
```



## Parameters

This method has no parameters.

## Return value

Returns **TRUE** if the filter is stopped. Otherwise, returns **FALSE**.

## Remarks

Do not call this method from within in the **CBasePin** constructor method, because the filter might not be initialized yet.

## Requirements



|                    |                                                                                                                                                                                            |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>Amfilter.h (include Streams.h)</dt> </dl>                                                                                  |
| Library<br/> | <dl> <dt>Strmbase.lib (retail builds); </dt> <dt>Strmbasd.lib (debug builds)</dt> </dl> |



## See also

<dl> <dt>

[**CBasePin Class**](cbasepin.md)
</dt> </dl>

 

 



