---
title: OLE DB Objects Used by Indexing Service
description: OLE DB Objects Used by Indexing Service
ms.assetid: 'b8af20ec-9409-4d70-ba27-8d6348bc3346'
---

# OLE DB Objects Used by Indexing Service

> [!Note]  
> Indexing Service is no longer supported as of Windows XP and is unavailable for use as of Windows 8. Instead, use [Windows Search](https://msdn.microsoft.com/library/windows/desktop/aa965362) for client side search and [Microsoft Search Server Express]( http://go.microsoft.com/fwlink/p/?linkid=258445) for server side search.

 

The OLE DB Provider for Indexing Service uses the following OLE DB objects.

-   **Data Source Object (DSO)**

    DSOs connect to Indexing Service as a data source and allow the creation of [**Session objects**](64c01b74-d11a-4330-bd64-df0b355365aa).

-   **Session Object**

    [**Session**](64c01b74-d11a-4330-bd64-df0b355365aa) objects establish the context for sessions and allows the creation of [**Command objects**](c72d0308-7e30-4250-b85e-557b8c399a3c) and [**Rowset objects**](3d41e965-292d-405d-a67c-9278f64f97aa).

-   **Command Object**

    [**Command**](c72d0308-7e30-4250-b85e-557b8c399a3c) objects represent commands given to the data source to allow execution of a text command. The result of executing a text command for Indexing Service is a [**Rowset**](3d41e965-292d-405d-a67c-9278f64f97aa) object. For a list of interfaces implemented for **Command** objects, refer to the [Interfaces](interfaces.md) section. Note that the [**ICommandTree**](icommandtree.md) interface, unique to this OLE DB provider, allows you to express queries in a hierarchical fashion similar to the [**ICommandText**](089427ad-5ba3-4613-b89e-8e86420ccc30) features.

-   **Rowset Object**

    [**Rowset**](3d41e965-292d-405d-a67c-9278f64f97aa) objects represent data in a table. For a list of interfaces implemented for **Rowset** objects, refer to the [Interfaces](interfaces.md) section.

-   **Error Object**

    [**Error objects**](bd679a0f-cc4c-477b-88ef-609592dba7b4) represent errors that occur during an operation on any of the other objects.

Simply put, Indexing Service uses the OLE DB object model to manipulate the indexes as a data source. The query string is similar to command text in a hierarchical form to facilitate matching hits against the index. The resulting hits are displayed as rows in a table that can support a variety of navigation movements, including scrolling forward and backward, and direct positioning with bookmarks. The [**IAccessor**](a39058b6-ecfa-418b-80a3-66eea4a7bf89) interface on the [**Rowset**](3d41e965-292d-405d-a67c-9278f64f97aa) object allows you to map command text variables to the resulting **Rowset** columns.

 

 



