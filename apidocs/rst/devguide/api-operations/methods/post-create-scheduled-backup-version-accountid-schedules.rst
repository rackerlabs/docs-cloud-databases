
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _post-create-scheduled-backup-version-accountid-schedules:

Create scheduled backup
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /{version}/{accountId}/schedules

Creates a schedule for running a backup periodically.

This operation asynchronously creates a new schedule for running a backup periodically. This call requires the user to specify an instance ID to backup and the date/time when the backup should be made. 

The following table lists the required and optional attributes for Create Backup:

.. table:: Required and optional attributes for Create scheduled backup

    
    +--------------------------+-------------------------+-------------------------+
    |Name                      |Description              |Required                 |
    +==========================+=========================+=========================+
    |action                    |The scheduled action:    |Yes                      |
    |                          |``backup``.              |                         |
    +--------------------------+-------------------------+-------------------------+
    |day_of_week               |The day of the week.     |Yes                      |
    |                          |Sunday is ``0``.         |                         |
    +--------------------------+-------------------------+-------------------------+
    |hour                      |The hour of the day.     |Yes                      |
    |                          |Midnight is 0.           |                         |
    +--------------------------+-------------------------+-------------------------+
    |minute                    |The minute of the hour.  |Yes                      |
    +--------------------------+-------------------------+-------------------------+
    |instance                  |The database instanceId  |Yes                      |
    |                          |to backup.               |                         |
    +--------------------------+-------------------------+-------------------------+
    

The ``day_of_week`` attribute specifies the day in which a full backup will be made. After that day, the schedule will automatically run daily incremental backups until the next full backup.

.. note::
   
   
   *  During the backup process, database writes on MyISAM Databases will be disabled. InnoDB Databases will continue to allow all operations.
   *  While the instance is being backed up you will not be able to add/delete databases, add/delete users, or delete/stop/reboot the instance.
   *  Users can only run one backup at a time. Duplicate requests will receive a 422 error.
   *  Backups are not deleted when the instance is deleted. You must manually remove any backups created using the Backups API. Refer to `Delete backup <http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/DELETE_deleteBackup__version___accountId__backups__backupId__backups.html>`__ for details.
   *  During backup the files will be streamed to your Cloud Files account. The process creates a container called ``z_CLOUDDB_BACKUPS`` and places all the files in it. In order for the restore and deletion of backups to work properly, you should not move, rename, or delete any of the files from this container. You will be charged the normal Cloud Files rate for storage of these files. For pricing details, refer to `http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/Pricing_SLA-d1e1362.html <http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/Pricing_SLA-d1e1362.html>`__ No additional Cloud Databases fee applies for creating backups. You can delete old backups through the API. Refer to `Delete backup <http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/DELETE_deleteBackup__version___accountId__backups__backupId__backups.html>`__ for details.
   *  In the unlikely event that the backup fails to perform correctly and is in the state ``FAILED``, there may be some files that were placed in the container. You should use the API to delete the backup to remove any leftover files. Refer to `Delete backup <http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/DELETE_deleteBackup__version___accountId__backups__backupId__backups.html>`__ for details.
   *  If a backup is deleted, all incremental backups created from it will also be deleted.
   *  You can create an incremental backup from another incremental backup. There is no limit to how many nested backups you can create, however the chances of a restore failure increase with the number of nested backups you create.
   
   
   



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |Accepted                 |The request has been     |
|                          |                         |accepted for processing. |
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





This operation does not accept a request body.




**Example Create scheduled backup: JSON request**


The following example shows the Create scheduled backup request:

.. code::

   POST /v1.0/1234/schedules HTTP/1.1
   User-Agent: python-troveclient
   Host: troveapi.org
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json
   
   {
       "schedule": {
           "action": "backup",
           "day_of_week": 0,
           "hour": 14,
           "instance_id": "44b277eb-39be-4921-be31-3d61b43651d7",
           "minute": 30
       }
   }
   





Response
""""""""""""""""










**Example Create scheduled backup: JSON response**


The following example shows the Create scheduled backup response:

.. code::

   HTTP/1.1 202 Accepted
   Content-Type: application/json
   Content-Length: 343
   Date: Mon, 18 Mar 2013 19:09:17 GMT
   
   {
       "schedule": {
           "action": "backup",
           "created": "2014-10-30T12:30:00",
           "day_of_month": null,
           "day_of_week": 0,
           "hour": 14,
           "id": "2e351a71-dd28-4bcb-a7d6-d36a5b487173",
           "instance_id": "44b277eb-39be-4921-be31-3d61b43651d7",
           "last_scheduled": null,
           "minute": 30,
           "month": null,
           "next_run": "2014-11-02T14:30:00",
           "updated": "2014-10-30T12:30:00"
       }
   }
   




