
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

List backups
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /{version}/{accountId}/backups

Lists all backups for all database instances.

This operation returns a list of all backups for all database instances.

You can filter by datastore type using the datastore query parameter.



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
|404                       |Not Found                |The requested item was   |
|                          |                         |not found.               |
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



This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|datastore                 |String *(Optional)*      |The type of the          |
|                          |                         |datastore by which to    |
|                          |                         |filter.                  |
+--------------------------+-------------------------+-------------------------+




This operation does not accept a request body.




**Example List backups: JSON request**


.. code::

    GET /v1.0/1234/backups HTTP/1.1
    User-Agent: python-troveclient
    Host: ord.databases.api.rackspacecloud.com
    X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
    Accept: application/json
    Content-Type: application/json
    
    
    


**Example List backups query request: JSON**


.. code::

    GET /v1.0/1234/backups?datastore=mysql HTTP/1.1
    User-Agent: python-troveclient
    Host: ord.databases.api.rackspacecloud.com
    X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
    Accept: application/json
    Content-Type: application/json
    
    
    


Response
""""""""""""""""







**Example List backups: JSON response**


.. code::

    HTTP/1.1 200 OK
    Content-Type: application/json
    Via: 1.1 Repose (Repose/2.6.7)
    Content-Length: 663
    Date: Thu, 13 Feb 2014 21:47:16 GMT
    Server: Jetty(8.0.y.z-SNAPSHOT)
    
    
    
    {
      "backups": [
        {
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
        },
        {
          "status": "COMPLETED",
          "updated": "2014-06-19T15:26:10",
          "description": "Backup from Restored Instance",
          "datastore": {
            "version": "5.1",
            "type": "MySQL",
            "version_id": "20000000-0000-0000-0000-000000000002"
          },
          "id": "5890e1cc-c5ad-460c-baec-cfdaf2ccf796",
          "size": 0.141026,
          "name": "restored_backup",
          "created": "2014-06-19T15:25:06",
          "instance_id": "c7855b60-2a50-4ed9-8de3-f35f2067fb2a",
          "parent_id": null,
          "locationRef": "http://localhost/path/to/backup"
        },
        {
          "status": "COMPLETED",
          "updated": "2014-06-19T15:20:04",
          "description": "Backup from Restored Instance",
          "datastore": {
            "version": "5.1",
            "type": "MySQL",
            "version_id": "20000000-0000-0000-0000-000000000002"
          },
          "id": "6fdbf0cc-8950-481b-995f-1f041abda2b6",
          "size": 0.141026,
          "name": "restored_backup",
          "created": "2014-06-19T15:19:00",
          "instance_id": "e84b5d1c-97c9-4aa1-9f0a-dbf867f1087c",
          "parent_id": null,
          "locationRef": "http://localhost/path/to/backup"
        },
        {
          "status": "COMPLETED",
          "updated": "2014-06-19T15:05:23",
          "description": "Backup from Restored Instance",
          "datastore": {
            "version": "5.1",
            "type": "MySQL",
            "version_id": "20000000-0000-0000-0000-000000000002"
          },
          "id": "b3b8ef8b-36a6-4043-9997-701b34a2b805",
          "size": 0.141026,
          "name": "restored_backup",
          "created": "2014-06-19T15:04:19",
          "instance_id": "3120d7eb-42fe-4d63-b8f6-98396f4c8590",
          "parent_id": null,
          "locationRef": "http://localhost/path/to/backup"
        },
        {
          "status": "COMPLETED",
          "updated": "2014-06-18T21:24:39",
          "description": "Backup from Restored Instance",
          "datastore": {
            "version": "5.1",
            "type": "MySQL",
            "version_id": "20000000-0000-0000-0000-000000000002"
          },
          "id": "87972694-4be2-40f5-83f8-501656e0032a",
          "size": 0.141026,
          "name": "restored_backup",
          "created": "2014-06-18T21:23:35",
          "instance_id": "29af2cd9-0674-48ab-b87a-b160f00208e6",
          "parent_id": null,
          "locationRef": "http://localhost/path/to/backup"
        },
        {
          "instance_id": "8814db50-da7d-4151-b271-6b3a64215b8e",
          "status": "NEW",
          "updated": "2014-06-06T17:44:56",
          "locationRef": null,
          "name": "main_backup_test",
          "parent_id": null,
          "created": "2014-06-06T17:44:56",
          "size": null,
          "id": "36d274f5-dfa9-42fc-afee-5f5117a16746",
          "description": "this is the main backup created at the start"
        }
      ]
    }
    
    
    


**Example List backups query response: JSON**


.. code::

    HTTP/1.1 200 OK
    Content-Type: application/json
    Via: 1.1 Repose (Repose/2.6.7)
    Content-Length: 663
    Date: Thu, 13 Feb 2014 21:47:16 GMT
    Server: Jetty(8.0.y.z-SNAPSHOT)
    
    
    {
        "backups": [
            {
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
            },
            {
                "status": "COMPLETED",
                "updated": "2014-06-19T15:26:10",
                "description": "Backup from Restored Instance",
                "datastore": {
                    "version": "5.1",
                    "type": "MySQL",
                    "version_id": "20000000-0000-0000-0000-000000000002"
                },
                "id": "5890e1cc-c5ad-460c-baec-cfdaf2ccf796",
                "size": 0.141026,
                "name": "restored_backup",
                "created": "2014-06-19T15:25:06",
                "instance_id": "c7855b60-2a50-4ed9-8de3-f35f2067fb2a",
                "parent_id": null,
                "locationRef": "http://localhost/path/to/backup"
            },
            {
                "status": "COMPLETED",
                "updated": "2014-06-19T15:20:04",
                "description": "Backup from Restored Instance",
                "datastore": {
                    "version": "5.1",
                    "type": "MySQL",
                    "version_id": "20000000-0000-0000-0000-000000000002"
                },
                "id": "6fdbf0cc-8950-481b-995f-1f041abda2b6",
                "size": 0.141026,
                "name": "restored_backup",
                "created": "2014-06-19T15:19:00",
                "instance_id": "e84b5d1c-97c9-4aa1-9f0a-dbf867f1087c",
                "parent_id": null,
                "locationRef": "http://localhost/path/to/backup"
            },
            {
                "status": "COMPLETED",
                "updated": "2014-06-19T15:05:23",
                "description": "Backup from Restored Instance",
                "datastore": {
                    "version": "5.1",
                    "type": "MySQL",
                    "version_id": "20000000-0000-0000-0000-000000000002"
                },
                "id": "b3b8ef8b-36a6-4043-9997-701b34a2b805",
                "size": 0.141026,
                "name": "restored_backup",
                "created": "2014-06-19T15:04:19",
                "instance_id": "3120d7eb-42fe-4d63-b8f6-98396f4c8590",
                "parent_id": null,
                "locationRef": "http://localhost/path/to/backup"
            },
            {
                "status": "COMPLETED",
                "updated": "2014-06-18T21:24:39",
                "description": "Backup from Restored Instance",
                "datastore": {
                    "version": "5.1",
                    "type": "MySQL",
                    "version_id": "20000000-0000-0000-0000-000000000002"
                },
                "id": "87972694-4be2-40f5-83f8-501656e0032a",
                "size": 0.141026,
                "name": "restored_backup",
                "created": "2014-06-18T21:23:35",
                "instance_id": "29af2cd9-0674-48ab-b87a-b160f00208e6",
                "parent_id": null,
                "locationRef": "http://localhost/path/to/backup"
            }
        ]
    }
    
    
    
    
    
    


