
.. _post-create-backup-with-copy:

Create backup and make a copy in another region
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /{version}/{accountId}/backups

Creates a new backup for a database instance, and copies it to another region.

This operation creates a new backup for the specified database
instance, and copies the backup to remote regions especially for disaster
recovery purpose.

.. note::


   *  The destination regions for the copying operation can be
      DFW, IAD, ORD, HKG, SYD. The region of LON is not supported.
   *  In the case of copying an incremental backup, a 400 Bad Request will
      return if the backup's parent is not found in the destination region.

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |ACCEPTED                 |Request accepted.        |
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
   Content-Length: 300
   Date: Fri, 13 Nov 2020 21:17:22 GMT

   {
       "backup": {
           "created": "2020-11-13T21:17:24Z",
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
