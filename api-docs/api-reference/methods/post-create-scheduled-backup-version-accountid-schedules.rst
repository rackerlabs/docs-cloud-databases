
.. _post-create-scheduled-backup-version-accountid-schedules:

Create scheduled backup
~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /{version}/{accountId}/schedules

Creates a schedule for running a backup periodically.

This operation asynchronously creates a new schedule for running a backup
periodically. This call requires the user to specify an instance ID to backup
and the date/time when the backup should be made.

The following table lists the required and optional attributes for Create
Backup:

.. table:: Required and optional attributes for Create scheduled backup

    +--------------------------+-------------------------+-------------------------+
    |Name                      |Description              |Required                 |
    +==========================+=========================+=========================+
    |action                    |The scheduled action:    |Yes                      |
    |                          |``backup``.              |                         |
    +--------------------------+-------------------------+-------------------------+
    |day_of_week               |The day of the week.     |Yes                      |
    |                          |0(sun)-6(sat) or 7 for   |                         |
    |                          |full backup every day    |                         |
    +--------------------------+-------------------------+-------------------------+
    |hour                      |The hour of the day.     |Yes                      |
    |                          |Midnight is 0.           |                         |
    +--------------------------+-------------------------+-------------------------+
    |minute                    |The minute of the hour.  |Yes                      |
    +--------------------------+-------------------------+-------------------------+
    |instance_id               |The database instanceId  |Yes                      |
    |                          |to backup.               |                         |
    +--------------------------+-------------------------+-------------------------+
    |source_id                 |The database instanceId  |No                       |
    |                          |or haId to back up.      |                         |
    +--------------------------+-------------------------+-------------------------+
    |source_type               |The type of backup for   |No                       |
    |                          |the given source_id      |                         |
    |                          |('instance' or 'ha',     |                         |
    |                          |defaults to 'instance'). |                         |
    +--------------------------+-------------------------+-------------------------+
    |full_backup_retention     |The number of full       |No                       |
    |                          |automated backups to     |                         |
    |                          |keep.                    |                         |
    +--------------------------+-------------------------+-------------------------+
    |copy_to                   |Copies the completed     |No                       |
    |                          |backup to remote regions.|                         |
    +--------------------------+-------------------------+-------------------------+

The ``day_of_week`` attribute specifies the day in which a full backup will be
made. When ``day_of_week`` is 0-6, after that day, the schedule automatically
runs daily incremental backups until the next full backup.

The ``instance_id`` attribute is present for legacy compatibility and can only
be used to create single instance automated backups. For HA groups, please use
the ``source_id`` attribute, providing the HA group id and with the
``source_type`` set to 'ha'.

By default, the full backup retention policy is set to two full backups. You
can override this setting by providing the ``full_backup_retention`` attribute.

.. note::

   *  During the backup process, database writes on MyISAM Databases are
      disabled. InnoDB Databases will continue to allow all operations.
   *  While the instance is being backed up,  you cannot add or delete
      databases or users, and you cannot delete, stop, or reboot the instance.
   *  Users can only run one backup at a time. Duplicate requests return a 422
      error.
   *  Backups are not deleted when the instance is deleted. You must manually
      remove any backups created using the Backups API. For details, see the
      :rax-devdocs:`Delete backup <cloud-databases/v1/developer-guide/#delete-backup>`
      operation.
   *  During backup, the files are streamed to your Cloud Files account. The
      process creates a container called ``z_CLOUDDB_BACKUPS`` and places all
      the files in it. In order for the restore and deletion of backups to work
      properly, do not move, rename, or delete any of the files from this
      container. You will be charged the normal Cloud Files rate for storage of
      these files. For pricing details, see the
      :rax:`Rackspace Cloud Calculator <calculator>`. No additional Cloud
      Databases fee applies for creating backups. You can delete old backups
      through the API. For details, see the
      :rax-devdocs:`Delete backup <cloud-databases/v1/developer-guide/#delete-backup>`
      operation.
   *  In the unlikely event that the backup fails to perform correctly and is
      in a ``FAILED`` state, there might be some files that were placed in the
      container. Use the API to delete the backup to remove any leftover files.
      For details, see the
      :rax-devdocs:`Delete backup <cloud-databases/v1/developer-guide/#delete-backup>`
      operation.
   *  When a backup is deleted, all incremental backups created from it are
      also be deleted.
   *  You can create an incremental backup from another incremental backup.
      There is no limit to how many nested backups you can create. However, the
      more nested backups you create, the higher the chances of a restore
      failure.
   *  The ``copy_to`` attribute can be DFW, IAD, ORD, HKG, SYD.
      The region of LON is not supported.
   *  In the case of copying an incremental backup, a 400 Bad Request will
      return if the backup's parent is not found in the destination region.

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
-------

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{accountId}               |String                   |The account ID of the    |
|                          |                         |owner of the specified   |
|                          |                         |instance.                |
+--------------------------+-------------------------+-------------------------+

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

**Example Create scheduled backup with copy_to: JSON request**

.. code::

   POST /v1.0/1234/schedules HTTP/1.1
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

   {
       "schedule": {
           "action": "backup",
           "day_of_week": 0,
           "hour": 14,
           "instance_id": "44b277eb-39be-4921-be31-3d61b43651d7",
           "minute": 30,
           "copy_to": ["IAD", "ORD"]
       }
   }

Response
--------

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
        "full_backup_retention": null,
        "hour": 14,
        "id": "88b277eb-39be-4921-be31-3d61b43651d7",
        "instance_id": "44b277eb-39be-4921-be31-3d61b43651d7",
        "last_scheduled": null,
        "minute": 30,
        "month": null,
        "next_run": "2014-10-30T14:30:00",
        "running": false,
        "source": {
            "id": "44b277eb-39be-4921-be31-3d61b43651d7",
            "type": "instance"
        },
        "updated": "2014-10-30T12:30:00"
      }
   }

**Example Create scheduled backup with copy_to: JSON response**

.. code::

   HTTP/1.1 202 Accepted
   Content-Type: application/json
   Content-Length: 490
   Date: Sat, 14 Nov 2020 07:28:17 GMT

   {
     "schedule": {
        "action": "backup",
        "created": "2020-11-14T07:28:17",
        "day_of_month": null,
        "day_of_week": 0,
        "full_backup_retention": 2,
        "hour": 14,
        "id": "88b277eb-39be-4921-be31-3d61b43651d7",
        "instance_id": "44b277eb-39be-4921-be31-3d61b43651d7",
        "last_scheduled": null,
        "minute": 30,
        "month": null,
        "next_run": "2020-11-14T14:30:00",
        "running": 0,
        "source": {
            "id": "44b277eb-39be-4921-be31-3d61b43651d7",
            "type": "instance"
        },
        "updated": "2020-11-14T07:28:17",
        "copy_to": ["ORD", "IAD"]
      }
   }
