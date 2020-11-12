
.. _post-create-scheduled-backup-with-copy:

Create scheduled backup
~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /{version}/{accountId}/schedules

Creates a schedule for running a backup periodically, and makes a copy
to other regions for each successful backups.

.. note::


   *  The destination regions for the copying operation can be
      DFW, IAD, ORD, HKG, SYD. The region of LON is not supported.
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
