.. _post-action-backup-copy:

Create a copy of an existing backup in another region
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /{version}/{accountId}/backups/{backupId}/action

Creates a copy of the specified backup in another region, especially
for disaster recovery purpose.

.. note::


   *  The source and destination regions for backup copy operation can be
      DFW, IAD, ORD, HKG, SYD. The region of LON is not supported.
   *  In the case of copying an incremental backup, a 400 Bad Request will
      return if the backup's parent is not found in the destination region.


This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |Accepted                 |Request accepted.        |
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
|{backupId}                |String                   |The backup ID.           |
+--------------------------+-------------------------+-------------------------+

**Example Create backup copy: JSON request**

.. code::

   POST /v1.0/1234/backups/ff44da4e-91eb-40ba-aa5b-841e1c308f55/action HTTP/1.1
   Host: dfw.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Content-Type: application/json
   {
      "copy-backup":{
         "target_backup_region": "IAD",
         "description":"a backup copy",
         "name":"dfw-to-iad",
      }
   }

Response
--------

**Example Create backup copy: JSON response**

.. code::

   HTTP/1.1 202 Accepted
   Date: Fri, 13 Nov 2020 17:12:21 GMT
   Content-Type: application/json
   Date: Fri, 13 Nov 2020 17:12:21 GMT
   Content-Length: 0
