
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _post-create-backup-for-an-ha-instance-version-accountid-backups:

Create backup for an HA Instance
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /{version}/{accountId}/backups

Creates a new backup for the specified HA instance.

This operation asynchronously creates a new backup for the specified HA instance. This call requires the user to specify an HA ID to backup and a name for the backup. 

The following table lists the required and optional attributes for Create Backup for an HA Instance:

.. table:: Required and optional attributes for Create backup

    
    +--------------------------+-------------------------+-------------------------+
    |Name                      |Description              |Required                 |
    +==========================+=========================+=========================+
    |name                      |Specifies the short name |Yes                      |
    |                          |of the backup.           |                         |
    +--------------------------+-------------------------+-------------------------+
    |instance                  |Specifies the database   |Yes                      |
    |                          |instanceId to backup.    |                         |
    |                          |But since we would need  |                         |
    |                          |to create a backup of    |                         |
    |                          |the entire HA group, the |                         |
    |                          |value of this field      |                         |
    |                          |should be empty.         |                         |
    +--------------------------+-------------------------+-------------------------+
    |description               |Specifies a long         |No                       |
    |                          |description of the       |                         |
    |                          |backup.                  |                         |
    +--------------------------+-------------------------+-------------------------+
    |parent_id                 |Specifies the backupId   |No                       |
    |                          |from which to create an  |                         |
    |                          |incremental backup.      |                         |
    +--------------------------+-------------------------+-------------------------+
    |source                    |Specifies the source     |Yes (to create HA group  |
    |                          |type (instance/ha) and   |backups)                 |
    |                          |source id                |                         |
    |                          |(instanceID/haID).       |                         |
    +--------------------------+-------------------------+-------------------------+
    

.. table:: Length restrictions for backup ``name`` parameter

    
    +---------------------------------------+--------------------------------------+
    |Restriction                            |Value                                 |
    +=======================================+======================================+
    |name maximum length                    |64                                    |
    +---------------------------------------+--------------------------------------+
    

.. note::
   
   
   *  To list, show details of a HA backup, refer to the following: `List backups <http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/GET_getBackups__version___accountId__backups_backups.html>`__ and `List backups by ID <http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/GET_getBackupById__version___accountId__backups__backupId__backups.html>`__.
   *  To list backups for a specified HA instance, refer to `List backups of an HA instance <http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/GET_getBackupsForHaInstance__version___accountId__ha__haId__backups_backups.html>`__.
   *  While creating a backup of a HA Instance, the backup of the latest replica instance (the one closest to the source) is taken.
   *  The HA instance goes into a ``BACKUP`` state if it has a running backup.
   *  Backups are not deleted when the instance is deleted. You must manually remove any backups created using the Backups API. Refer to `Delete backup <http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/DELETE_deleteBackup__version___accountId__backups__backupId__backups.html>`__ for details.
   *  During backup the files will be streamed to your Cloud Files account. The process creates a container called z_CLOUDDB_BACKUPS and places all the files in it. In order for the restore and deletion of backups to work properly, you should not move, rename, or delete any of the files from this container. You will be charged the normal Cloud Files rate for storage of these files. For pricing details, refer to `http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/Pricing_SLA-d1e1362.html <http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/Pricing_SLA-d1e1362.html>`__ No additional Cloud Databases fee applies for creating backups. You can delete old backups through the API. For details see `Delete backup <http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/DELETE_deleteBackup__version___accountId__backups__backupId__backups.html>`__.
   *  In the unlikely event that the backup fails to perform correctly and is in the state ``FAILED``, there may be some files that were placed in the container. You should use the API to delete the backup to remove any leftover files. Refer to `Delete backup <http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/DELETE_deleteBackup__version___accountId__backups__backupId__backups.html>`__ for details.
   *  If a backup is deleted, all incremental backups created from it will also be deleted.
   
   
   



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |You are not authorized   |
|                          |                         |to complete this         |
|                          |                         |operation. This error    |
|                          |                         |can occur if the request |
|                          |                         |is submitted with an     |
|                          |                         |invalid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+
|403                       |Forbidden                |You are denied access to |
|                          |                         |the requested resource.  |
+--------------------------+-------------------------+-------------------------+
|404                       |Not Found                |The requested item was   |
|                          |                         |not found.               |
+--------------------------+-------------------------+-------------------------+
|405                       |badMethod                |The specified method is  |
|                          |                         |not allowed for the      |
|                          |                         |given resource.          |
+--------------------------+-------------------------+-------------------------+
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|422                       |unprocessableEntity      |The item cannot be       |
|                          |                         |processed.               |
+--------------------------+-------------------------+-------------------------+
|500                       |instanceFault            |The instance has         |
|                          |                         |experienced a fault.     |
+--------------------------+-------------------------+-------------------------+
|501                       |notImplemented           |The server does not      |
|                          |                         |support the              |
|                          |                         |functionality required   |
|                          |                         |to fulfill the request.  |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{accountId}               |String                   |The account ID of the    |
|                          |                         |owner of the specified   |
|                          |                         |instance.                |
+--------------------------+-------------------------+-------------------------+








**Example Create backup for an HA Instance: JSON request**


The following example shows the Create backup of an HA instance request:

.. code::

   POST /v1.0/1234/backups HTTP/1.1
   User-Agent: python-troveclient
   Host: dfw.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json
   {  
      "backup":{  
         "instance":null,
         "description":"my_ha_backup1",
         "name":"ha-backup1",
         "source":{  
            "type":"ha",
            "id":"130922a2-b9ab-4e95-86be-9c5d79171b5e"
         }
      }
   }
   





**Example Create incremental backup request: JSON**


The following example shows the Create incremental backup request:

.. code::

   POST /v1.0/1234/backups HTTP/1.1
   User-Agent: python-troveclient
   Host: dfw.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json
   


.. code::

   {  
      "backup":{  
         "instance":null,
         "description":"my_ha_backup2",
         "name":"ha-backup2",
         "parent_id":"0c1b5616-fdc5-45ae-b2dc-6f1440d55d0e",
         "source":{  
            "type":"ha",
            "id":"130922a2-b9ab-4e95-86be-9c5d79171b5e"
         }
      }
   }
   





Response
""""""""""""""""










**Example Create backup for an HA Instance: JSON response**


The following example shows the Create backup response:

.. code::

   HTTP/1.1 202 Accepted
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.12)
   Content-Length: 535
   Date: Mon, 31 Aug 2015 22:16:25 GMT
   Connection: close
   Server: Jetty(8.0.y.z-SNAPSHOT)
   {  
      "backup":{  
         "status":"NEW",
         "updated":"2015-08-31T22:16:25Z",
         "description":"my_ha_backup1",
         "datastore":{  
            "version":"5.6",
            "type":"mysql",
            "version_id":"1379cc8b-4bc5-4c4a-9e9d-7a9ad27c0866"
         },
         "id":"0c1b5616-fdc5-45ae-b2dc-6f1440d55d0e",
         "size":null,
         "is_automated":false,
         "name":"ha-backup1",
         "parent_id":null,
         "created":"2015-08-31T22:16:25Z",
         "flavor_ram":1024,
         "instance_id":null,
         "source":{  
            "type":"ha",
            "id":"130922a2-b9ab-4e95-86be-9c5d79171b5e"
         },
         "locationRef":null,
         "type":"InnoBackupEx",
         "volume_size":1
      }
   }
   





**Example Create incremental backup response: JSON**


The following example shows the Create incremental backup response:


   


.. code::

   {  
      "backup":{  
         "status":"NEW",
         "updated":"2015-08-31T22:26:23Z",
         "description":"my_ha_backup2",
         "datastore":{  },
         "id":"e1cb03fd-c108-4702-a04b-653491e41a91",
         "size":null,
         "is_automated":false,
         "name":"ha-backup2",
         "parent_id":"0c1b5616-fdc5-45ae-b2dc-6f1440d55d0e",
         "created":"2015-08-31T22:26:23Z",
         "flavor_ram":1024,
         "instance_id":null,
         "source":{  
            "type":"ha",
            "id":"130922a2-b9ab-4e95-86be-9c5d79171b5e"
         },
         "locationRef":null,
         "type":"InnoBackupExIncremental",
         "volume_size":1
      }
   }
   




