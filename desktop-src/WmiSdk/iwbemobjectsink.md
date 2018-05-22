---
Description: 'The IWbemObjectSink interface creates a sink interface that can receive all types of notifications within the WMI programming model.'
audience: developer
author: 'REDMOND\\markl'
manager: 'REDMOND\\markl'
ms.assetid: '987aea1d-912a-4691-987f-181c1ef1a8a9'
ms.prod: 'windows-server-dev'
ms.technology: 'windows-management-instrumentation'
ms.tgt_platform: multiple
title: IWbemObjectSink interface
---

# IWbemObjectSink interface

The **IWbemObjectSink** interface creates a sink interface that can receive all types of notifications within the WMI programming model. Clients must implement this interface to receive both the results of the [asynchronous methods](making-an-asynchronous-call-with-c--.md) of [**IWbemServices**](iwbemservices.md), and specific types of event notifications. Providers use, but do not implement this interface to provide events and objects to WMI.

Typically, providers call an implementation provided to them by WMI. In these cases, call [**Indicate**](iwbemobjectsink-indicate.md) to provide objects to the WMI service. After that, call [**SetStatus**](iwbemobjectsink-setstatus.md) to indicate the end of the notification sequence. You can also call **SetStatus** to indicate errors when the sink does not have any objects.

When programming asynchronous clients of WMI, the user provides the implementation. WMI calls the methods to deliver objects and set the status of the result.

> [!Note]  
> If a client application passes the same sink interface in two different overlapping asynchronous calls, WMI does not guarantee the order of the callback. Client applications that make overlapping asynchronous calls should either pass different sink objects, or serialize their calls.

�

> [!Note]  
> Because the call-back to the sink might not be returned at the same authentication level as the client requires, it is recommended that you use semisynchronous instead of asynchronous communication. For more information, see [Calling a Method](calling-a-method.md).

�

## Members

The **IWbemObjectSink** interface has these types of members:

-   [Methods](#methods)

### Methods

The **IWbemObjectSink** interface has these methods.



| Method                                         | Description                                                                                                             |
|:-----------------------------------------------|:------------------------------------------------------------------------------------------------------------------------|
| [**Indicate**](iwbemobjectsink-indicate.md)   | Receives notification objects.<br/>                                                                               |
| [**SetStatus**](iwbemobjectsink-setstatus.md) | Called by sources to indicate the end of a notification sequence, or to send other status codes to the sink.<br/> |



�

## Remarks

When implementing an event subscription sink (**IWbemObjectSink** or [**IWbemEventSink**](iwbemeventsink.md)), do not call into WMI from within the [**Indicate**](iwbemobjectsink-indicate.md) or [**SetStatus**](iwbemobjectsink-setstatus.md) methods on the sink object. For example, calling [**IWbemServices::CancelAsyncCall**](iwbemservices-cancelasynccall.md) to cancel the sink from within an implementation of [**Indicate**](iwbemobjectsink-indicate.md) can interfere with the WMI state. To cancel an event subscription, set a flag and call **IWbemServices::CancelAsyncCall** from another thread or object. For implementations that are not related to an event sink, such as object, enum, and query retrievals, you can call back into WMI.

Sink implementations should process the event notification within 100 MSEC because the WMI thread that delivers the event notification cannot do other work until the sink object has completed processing. If the notification requires a large amount of processing, the sink can use an internal queue for another thread to handle the processing.

## Examples

The following code example is a simple implementation of an object sink. This sample can be used with [**IWbemServices::ExecQueryAsync**](iwbemservices-execqueryasync.md) or [**IWbemServices::CreateInstanceEnumAsync**](iwbemservices-createinstanceenumasync.md) to receive the returned instances:


```C++
#include <iostream>
#include <wbemidl.h>
#pragma comment(lib, "wbemuuid.lib")

class QuerySink : public IWbemObjectSink
{
    LONG m_lRef;
    bool bDone; 

public:
    QuerySink() { m_lRef = 0; }
   ~QuerySink() { bDone = TRUE; }

    virtual ULONG STDMETHODCALLTYPE AddRef();
    virtual ULONG STDMETHODCALLTYPE Release();        
    virtual HRESULT STDMETHODCALLTYPE 
        QueryInterface(REFIID riid, void** ppv);

    virtual HRESULT STDMETHODCALLTYPE Indicate( 
            /* [in] */
            LONG lObjectCount,
            /* [size_is][in] */
            IWbemClassObject __RPC_FAR *__RPC_FAR *apObjArray
            );
        
    virtual HRESULT STDMETHODCALLTYPE SetStatus( 
            /* [in] */ LONG lFlags,
            /* [in] */ HRESULT hResult,
            /* [in] */ BSTR strParam,
            /* [in] */ IWbemClassObject __RPC_FAR *pObjParam
            );
};


ULONG QuerySink::AddRef()
{
    return InterlockedIncrement(&amp;m_lRef);
}

ULONG QuerySink::Release()
{
    LONG lRef = InterlockedDecrement(&amp;m_lRef);
    if(lRef == 0)
        delete this;
    return lRef;
}

HRESULT QuerySink::QueryInterface(REFIID riid, void** ppv)
{
    if (riid == IID_IUnknown || riid == IID_IWbemObjectSink)
    {
        *ppv = (IWbemObjectSink *) this;
        AddRef();
        return WBEM_S_NO_ERROR;
    }
    else return E_NOINTERFACE;
}


HRESULT QuerySink::Indicate(long lObjCount, IWbemClassObject **pArray)
{
    for (long i = 0; i < lObjCount; i++)
    {
        IWbemClassObject *pObj = pArray[i];

        // ... use the object.

        // AddRef() is only required if the object will be held after
        // the return to the caller.
    }

    return WBEM_S_NO_ERROR;
}

HRESULT QuerySink::SetStatus(
            /* [in] */ LONG lFlags,
            /* [in] */ HRESULT hResult,
            /* [in] */ BSTR strParam,
            /* [in] */ IWbemClassObject __RPC_FAR *pObjParam
        )
{
    printf("QuerySink::SetStatus hResult = 0x%X\n", hResult);
    return WBEM_S_NO_ERROR;
}
```



## Requirements



|                                     |                                                                                                          |
|-------------------------------------|----------------------------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows�Vista<br/>                                                                                 |
| Minimum supported server<br/> | Windows Server�2008<br/>                                                                           |
| Header<br/>                   | <dl> <dt>Wbemcli.h (include Wbemidl.h)</dt> </dl> |
| Library<br/>                  | <dl> <dt>Wbemuuid.lib</dt> </dl>                  |
| DLL<br/>                      | <dl> <dt>Fastprox.dll</dt> </dl>                  |



## See also

<dl> <dt>

[COM API for WMI](com-api-for-wmi.md)
</dt> <dt>

[Making an Asynchronous Call with C++](making-an-asynchronous-call-with-c--.md)
</dt> <dt>

[Setting Security on an Asynchronous Call](setting-security-on-an-asynchronous-call.md)
</dt> <dt>

[Receiving Events for the Duration of your Application](receiving-events-for-the-duration-of-your-application.md)
</dt> </dl>

�

�



