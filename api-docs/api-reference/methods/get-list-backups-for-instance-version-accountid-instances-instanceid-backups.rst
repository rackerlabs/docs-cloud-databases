
.. _get-list-backups-for-instance-version-accountid-instances-instanceid-backups:

List backups for instance
~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /{version}/{accountId}/instances/{instanceId}/backups

Lists all backups for a specified instance.

This operation lists all backups for a specified instance.

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
|{instanceId}              |String                   |The instance ID for the  |
|                          |                         |specified database       |
|                          |                         |instance.                |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

**Example List backups for instance: JSON request**

The following example shows the List backups for instance request:

.. code::

   GET /v1.0/1234/instances/d4603f69-ec7e-4e9b-803f-600b9205576f/backups HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

Response
--------

**Example List backups for instance: JSON response**

The following example shows the List backups for instance response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: 338
   Date: Thu, 13 Feb 2014 21:47:16 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

   {
       "backup": {
           "status": "COMPLETED",
           "updated": "2014-06-19T15:56:58",
           "description": "Backup from Restored Instance",
           "datastore": {
               "version": "5.1",
               "type": "MySQL",
               "version_id": "20000000-0000-0000-0000-000000000002"
           },
           "id": "e2d3dfca-430f-4cd2-bec0-884cd7426f13",
           "size": 0.141026,
           "name": "restored_backup",
           "created": "2014-06-19T15:55:54",
           "instance_id": "34d6c8bf-539e-47d1-8a06-2b7590521309",
           "parent_id": null,
           "locationRef": "http://localhost/path/to/backup"
       }
   }
