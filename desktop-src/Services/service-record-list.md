---
Description: 'As each service entry is read from the database of installed services, the SCM creates a service record for the service.'
ms.assetid: 'c0ee43e2-af9b-4578-9017-46a5ed50b938'
title: Service Record List
---

# Service Record List

As each service entry is read from the database of installed services, the SCM creates a service record for the service. A service record includes:

-   Service name
-   Start type (auto-start or demand-start)
-   Service status (see the [**SERVICE\_STATUS**](service-status-str.md) structure) <dl> Type  
    Current state  
    Acceptable control codes  
    Exit code  
    Wait hint  
    </dl>
-   Pointer to dependency list

The user name and password of an account are specified at the time the service is installed. The SCM stores the user name in the registry and the password in a secure portion of the Local Security Authority (LSA). The system administrator can create accounts with passwords that never expire. Alternatively, the system administrator can create accounts with passwords that expire and manage the accounts by changing the passwords periodically.

The SCM keeps two copies of a user account's password, a current password and a backup password. The password specified the first time the service is installed is stored as the current password and the backup password is not initialized. When the SCM attempts to run the service in the security context of the user account, it uses the current password. If the current password is used successfully, it is also saved as the backup password. If the password is modified with the [**ChangeServiceConfig**](changeserviceconfig.md) function, or the Services control panel utility, the new password is stored as the current password and the previous password is stored as the backup password. If the SCM attempts to start the service and the current password fails, then it uses the backup password. If the backup password is used successfully, it is saved as the current password.

The SCM updates the service status when a service sends it status notifications using the [**SetServiceStatus**](setservicestatus.md) function. The SCM maintains the status of a driver service by querying the I/O system, instead of receiving status notifications, as it does from a service.

A service can register additional type information by calling the [**SetServiceBits**](setservicebits.md) function. The [**NetServerGetInfo**](https://msdn.microsoft.com/library/windows/desktop/aa370624) and [**NetServerEnum**](https://msdn.microsoft.com/library/windows/desktop/aa370623) functions obtain the supported service types.

 

 


