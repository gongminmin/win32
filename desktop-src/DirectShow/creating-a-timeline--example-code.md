---
Description: 'Creating a Timeline: Example Code'
ms.assetid: 'efe6e8d7-2465-4374-8c99-a410091f8d46'
title: 'Creating a Timeline: Example Code'
---

# Creating a Timeline: Example Code

\[This API is not supported and may be altered or unavailable in the future.\]

The following code example shows how to create and preview a timeline in [DirectShow Editing Services](directshow-editing-services.md).

> [!Note]  
> For the sake of brevity, the sample code performs no error checking. In a real application, you should check the return values of method calls to make sure none has failed.

 


```C++
#include <dshow.h>
#include <qedit.h>

// Preview a timeline.
void PreviewTL(IAMTimeline *pTL, IRenderEngine *pRender) 
{
    IGraphBuilder   *pGraph = NULL;
    IMediaControl   *pControl = NULL;
    IMediaEvent     *pEvent = NULL;

    // Build the graph.
    pRender->SetTimelineObject(pTL);
    pRender->ConnectFrontEnd( );
    pRender->RenderOutputPins( );

    // Run the graph.
    pRender->GetFilterGraph(&amp;pGraph);
    pGraph->QueryInterface(IID_IMediaControl, (void **)&amp;pControl);
    pGraph->QueryInterface(IID_IMediaEvent, (void **)&amp;pEvent);
    pControl->Run();

    long evCode;
    pEvent->WaitForCompletion(INFINITE, &amp;evCode);
    pControl->Stop();

    // Clean up.
    pEvent->Release();
    pControl->Release();
    pGraph->Release();
}

void main( void )
{
    // Start by making an empty timeline.

    IAMTimeline    *pTL = NULL;
    CoInitialize(NULL);
    CoCreateInstance(CLSID_AMTimeline, NULL, CLSCTX_INPROC_SERVER, 
        IID_IAMTimeline, (void**)&amp;pTL);

    // GROUP: Add a video group to the timeline. 

    IAMTimelineGroup    *pGroup = NULL;
    IAMTimelineObj      *pGroupObj = NULL;
    pTL->CreateEmptyNode(&amp;pGroupObj, TIMELINE_MAJOR_TYPE_GROUP);
    pGroupObj->QueryInterface(IID_IAMTimelineGroup, (void **)&amp;pGroup);

    // Set the group media type. This example sets the type to "video" and
    // lets DES pick the default settings. For a more detailed example,
    // see "Setting the Group Media Type."
    AM_MEDIA_TYPE mtGroup;  
    ZeroMemory(&amp;mtGroup, sizeof(AM_MEDIA_TYPE));
    mtGroup.majortype = MEDIATYPE_Video;
    pGroup->SetMediaType(&amp;mtGroup);
    pTL->AddGroup(pGroupObj);
    pGroupObj->Release();

    // TRACK: Add a track to the group. 

    IAMTimelineObj      *pTrackObj;
    IAMTimelineTrack    *pTrack;
    IAMTimelineComp     *pComp = NULL;

    pTL->CreateEmptyNode(&amp;pTrackObj, TIMELINE_MAJOR_TYPE_TRACK);
    pGroup->QueryInterface(IID_IAMTimelineComp, (void **)&amp;pComp);
    pComp->VTrackInsBefore(pTrackObj, 0);
    pTrackObj->QueryInterface(IID_IAMTimelineTrack, (void **)&amp;pTrack);

    pTrackObj->Release();
    pComp->Release();    
    pGroup->Release();

    // SOURCE: Add a source to the track.

    IAMTimelineSrc *pSource = NULL;
    IAMTimelineObj *pSourceObj;
    pTL->CreateEmptyNode(&amp;pSourceObj, TIMELINE_MAJOR_TYPE_SOURCE);
    pSourceObj->QueryInterface(IID_IAMTimelineSrc, (void **)&amp;pSource);

    // Set the times and the file name.
    pSourceObj->SetStartStop(0, 50000000);
    BSTR bstrFile = SysAllocString(OLESTR("C:\\example.avi"));
    pSource->SetMediaName(bstrFile); 
    SysFreeString(bstrFile);
    pSource->SetMediaTimes(40000000, 140000000);
    pTrack->SrcAdd(pSourceObj);

    pSourceObj->Release();
    pSource->Release();
    pTrack->Release();

    // Preview the timeline.
    IRenderEngine *pRenderEngine = NULL;
    CoCreateInstance(CLSID_RenderEngine, NULL, CLSCTX_INPROC_SERVER,
        IID_IRenderEngine, (void**) &amp;pRenderEngine);
    PreviewTL(pTL, pRenderEngine);

    // Clean up.
    pRenderEngine->ScrapIt();
    pRenderEngine->Release();
    pTL->Release();
    CoUninitialize();
}
```



## Related topics

<dl> <dt>

[Constructing a Timeline](constructing-a-timeline.md)
</dt> </dl>

 

 


