.. _cdb-dg-generalapi-dbinstance:

========================
Database instance status
========================

When making an API call to create, list, or delete database instance(s), the following database instance status values are possible:

-  BUILD – The database instance is being provisioned.

-  REBOOT – The database instance is rebooting.

-  ACTIVE – The database instance is online and available to take requests.

-  FAILED – The database instance was created, but failed to set up the datastore. If a database instance is in the FAILED state, you should delete it and create a new instance.

-  BACKUP – The database instance is currently running a backup process.

-  BLOCKED – The database instance is unresponsive at the moment.

-  RESIZE – The database instance is being resized at the moment.

-  DETACH\_REPLICA – The database instance, which was a replica, is being detached from the source.

-  RESTART\_REQUIRED – A change has occurred to the configuration of an instance that requires the instance to be restarted at the user’s convenience.

-  SHUTDOWN – The database instance is terminating services. Also, SHUTDOWN is returned if for any reason the database instance is shut down but not the actual server.

    ..  note:: 
        If the database engine has crashed (causing the SHUTDOWN status), please call support for assistance.

-  ERROR – The last operation for the database instance failed due to an error.
