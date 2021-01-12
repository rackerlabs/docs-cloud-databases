
.. _post-create-backup-version-accountid-backups:

Create backup
~~~~~~~~~~~~~

.. code::

    POST /{version}/{accountId}/backups

Creates a new backup for a database instance.

This operation asynchronously creates a new backup for the specified database
instance. This call requires the user to specify an instance ID to backup and
a name for the backup.

The following table lists the required and optional attributes for Create
Backup:

.. table:: Required and optional attributes for Create backup

    +--------------------------+-------------------------+-------------------------+
    |Name                      |Description              |Required                 |
    +==========================+=========================+=========================+
    |name                      |Specifies the short name |Yes                      |
    |                          |of the backup.           |                         |
    +--------------------------+-------------------------+-------------------------+
    |instance                  |Specifies the database   |Yes                      |
    |                          |instanceId to backup.    |                         |
    +--------------------------+-------------------------+-------------------------+
    |description               |Specifies a long         |No                       |
    |                          |description of the       |                         |
    |                          |backup.                  |                         |
    +--------------------------+-------------------------+-------------------------+
    |parent_id                 |Specifies the backupId   |No                       |
    |                          |from which to create an  |                         |
    |                          |incremental backup.      |                         |
    +--------------------------+-------------------------+-------------------------+
    |copy_to                   |Copies the completed     |No                       |
    |                          |backup to remote regions.|                         |
    +--------------------------+-------------------------+-------------------------+

.. table:: Length restrictions for backup ``name`` parameter

    +---------------------------------------+--------------------------------------+
    |Restriction                            |Value                                 |
    +=======================================+======================================+
    |name maximum length                    |64                                    |
    +---------------------------------------+--------------------------------------+

.. note::


   *  During the backup process, database writes on MyISAM Databases are
      disabled. InnoDB Databases continue to allow all operations.
   *  While the instance is being backed up, you cannot add or delete databases
      or users, and you cannot delete, stop, or reboot the instance.
   *  Users can only run one backup at a time. Duplicate requests return a 422
      error.
   *  Backups are not deleted when the instance is deleted. You must manually
      remove any backups created using the Backups API. For details, see the
      :ref:`delete-delete-backup-version-accountid-backups-backupid` operation.
   *  During backup, the files are streamed to your Cloud Files account. The
      process creates a container called ``z_CLOUDDB_BACKUPS`` and places all
      the files in it. In order for the restore and deletion of backups to work
      properly, do not move, rename, or delete any of the files from this
      container. You will be charged the normal Cloud Files rate for storage of
      these files. For pricing details, see
      :rax:`Rackspace Cloud Calculator <calculator>`. No additional Cloud
      Databases fee applies for creating backups. You can delete old backups
      through the API. See the
      :ref:`delete-delete-backup-version-accountid-backups-backupid` operation.
   *  In the unlikely event that the backup fails to perform correctly and is
      in a ``FAILED`` state, some files might have been placed in the
      container. In these cases, use the API to delete the backup to remove
      any leftover files. For details, see the
      :ref:`delete-delete-backup-version-accountid-backups-backupid` operation.
   *  When a backup is deleted, all incremental backups created from it are
      also be deleted.
   *  You can create an incremental backup from another incremental backup.
      There is no limit to the number of nested backups you can create.
      However, the more nested backups you create, the higher the chances of a
      restore failure.
   *  The ``copy_to`` attribute can be DFW, IAD, ORD, HKG, SYD.
      The region of LON is not supported.
   *  In the case of copying an incremental backup, a 400 Bad Request will
      return if the backup's parent is not found in the destination region.

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
-------

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{accountId}               |String                   |The account ID of the    |
|                          |                         |owner of the specified   |
|                          |                         |instance.                |
+--------------------------+-------------------------+-------------------------+

**Example Create backup: JSON request**

The following example shows the Create backup request:

.. code::

   POST /v1.0/1234/backups HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

   {
       "backup": {
           "description": "My Backup",
           "instance": "d4603f69-ec7e-4e9b-803f-600b9205576f",
           "name": "snapshot"
       }
   }

**Example Create incremental backup request: JSON**

The following example shows the Create incremental backup request:

.. code::

   POST /v1.0/1234/backups HTTP/1.1

   User-Agent: python-troveclient

   Host: troveapi.org

   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7

   Accept: application/json

   Content-Type: application/json

.. code::

   {

       "backup": {

           "description": "My Incremental Backup",

           "instance": "44b277eb-39be-4921-be31-3d61b43651d7",

           "name": "Incremental Snapshot",

           "parent_id": "a9832168-7541-4536-b8d9-a8a9b79cf1b4"

       }

   }

**Example Create backup with copying: JSON request**

The following example shows the Create backup request with copy_to:

.. code::

   POST /v1.0/1234/backups HTTP/1.1
   Host: dfw.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

   {
       "backup": {
           "description": "My Backup",
           "instance": "d4603f69-ec7e-4e9b-803f-600b9205576f",
           "name": "snapshot",
           "copy_to": ["IAD", "ORD"]
       }
   }

Response
--------

**Example Create backup: JSON response**

The following example shows the Create backup response:

.. code::

   HTTP/1.1 202 Accepted
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: 300
   Date: Thu, 13 Feb 2014 21:47:16 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

   {
       "backup": {
           "created": "2014-02-13T21:47:16",
           "description": "My Backup",
           "id": "61f12fef-edb1-4561-8122-e7c00ef26a82",
           "instance_id": "d4603f69-ec7e-4e9b-803f-600b9205576f",
           "locationRef": null,
           "name": "snapshot",
           "parent_id": null,
           "size": null,
           "status": "NEW",
           "updated": "2014-02-13T21:47:16"
       }
   }

**Example Create incremental backup response: JSON**

The following example shows the Create incremental backup response:

.. code::

   HTTP/1.1 202 Accepted

   Content-Type: application/json

   Content-Length: 462

   Date: Mon, 18 Mar 2013 19:09:17 GMT

.. code::

   {
       "backup": {
           "created": "2014-10-30T12:30:00",
           "datastore": {
               "type": "mysql",
               "version": "5.5",
               "version_id": "b00000b0-00b0-0b00-00b0-000b000000bb"
           },
           "description": "My Incremental Backup",
           "id": "2e351a71-dd28-4bcb-a7d6-d36a5b487173",
           "instance_id": "44b277eb-39be-4921-be31-3d61b43651d7",
           "locationRef": null,
           "name": "Incremental Snapshot",
           "parent_id": "a9832168-7541-4536-b8d9-a8a9b79cf1b4",
           "size": null,
           "status": "NEW",
           "updated": "2014-10-30T12:30:00"
       }
   }
