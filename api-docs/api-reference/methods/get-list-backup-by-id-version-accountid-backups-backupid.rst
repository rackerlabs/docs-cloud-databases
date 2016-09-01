
.. _get-list-backup-by-id-version-accountid-backups-backupid:

List backup by ID
~~~~~~~~~~~~~~~~~

.. code::

    GET /{version}/{accountId}/backups/{backupId}

Lists details about a specified backup.

This operation lists the details for a specified backup.

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
|{backupId}                |String                   |The backup ID for the    |
|                          |                         |specified backup.        |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

**Example List backup by ID: JSON request**

The following example shows the List backup by ID request:

.. code::

   GET /v1.0/1234/backups/61f12fef-edb1-4561-8122-e7c00ef26a82 HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

Response
--------

**Example List backup by ID: JSON response**

The following example shows the List backup by ID response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.12)
   Content-Length: 737
   Date: Tue, 01 Sep 2015 03:34:53 GMT
   Connection: close
   Server: Jetty(8.0.y.z-SNAPSHOT)
   {
      "backup":{
         "status":"COMPLETED",
         "updated":"2015-09-01T03:23:36Z",
         "description":"My standalone instance backup1",
         "datastore":{
            "version":"5.6",
            "type":"percona",
            "version_id":"c9760c5b-5675-4482-b097-dffdf50c22ab"
         },
         "id":"61f12fef-edb1-4561-8122-e7c00ef26a82",
         "size":0.18,
         "is_automated":0,
         "name":"test_instance-backup",
         "parent_id":null,
         "created":"2015-09-01T03:23:28Z",
         "flavor_ram":1024,
         "instance_id":"f4aaba46-fb5f-4316-988d-88da77759968",
         "source":{
            "type":"instance",
            "id":"f4aaba46-fb5f-4316-988d-88da77759968"
         },
         "locationRef":"https://snet-storage101.dfw1.clouddrive.com/v1/MossoCloudFS_938359/z_CLOUDDB_BACKUPS/d9f56b04-e17d-41f0-ae92-30a3b47b8d29.xbstream.gz",
         "type":"InnoBackupEx",
         "volume_size":1
      }
   }

**Example List backup by ID: JSON response**

The following example shows the Show details of an HA instance backup by ID response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.12)
   Content-Length: 713
   Date: Tue, 01 Sep 2015 03:39:25 GMT
   Connection: close
   Server: Jetty(8.0.y.z-SNAPSHOT)
   {
      "backup":{
         "status":"COMPLETED",
         "updated":"2015-08-31T22:26:29Z",
         "description":"my_ha_backup2",
         "datastore":{
            "version":"5.6",
            "type":"mysql",
            "version_id":"1379cc8b-4bc5-4c4a-9e9d-7a9ad27c0866"
         },
         "id":"e1cb03fd-c108-4702-a04b-653491e41a91",
         "size":0.18,
         "is_automated":0,
         "name":"ha-backup2",
         "parent_id":"0c1b5616-fdc5-45ae-b2dc-6f1440d55d0e",
         "created":"2015-08-31T22:26:23Z",
         "flavor_ram":1024,
         "instance_id":null,
         "source":{
            "type":"ha",
            "id":"130922a2-b9ab-4e95-86be-9c5d79171b5e"
         },
         "locationRef":"https://snet-storage101.dfw1.clouddrive.com/v1/MossoCloudFS_938359/z_CLOUDDB_BACKUPS/e1cb03fd-c108-4702-a04b-653491e41a91.xbstream.gz",
         "type":"InnoBackupExIncremental",
         "volume_size":1
      }
   }
