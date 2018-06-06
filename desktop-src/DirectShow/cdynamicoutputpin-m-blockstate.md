---
Description: Blocking state.
ms.assetid: 55afd314-efd3-47bf-80e3-e17c1332a4cf
title: CDynamicOutputPin::m\_BlockState member
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# CDynamicOutputPin::m\_BlockState member

Blocking state.

## Syntax


```C++
BLOCK_STATE m_BlockState;
```



## Remarks

The following states are defined:

-   NOT\_BLOCKED
-   PENDING
-   BLOCKED

Before accessing this variable, hold the [**CDynamicOutputPin::m\_BlockStateLock**](cdynamicoutputpin-m-blockstatelock.md) critical section.

## Requirements



|                    |                                                                                                                                                                                            |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>Amfilter.h (include Streams.h)</dt> </dl>                                                                                  |
| Library<br/> | <dl> <dt>Strmbase.lib (retail builds); </dt> <dt>Strmbasd.lib (debug builds)</dt> </dl> |



## See also

<dl> <dt>

[**CDynamicOutputPin Class**](cdynamicoutputpin.md)
</dt> </dl>

 

 



