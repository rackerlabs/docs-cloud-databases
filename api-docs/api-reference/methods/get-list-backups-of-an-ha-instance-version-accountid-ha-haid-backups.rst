
.. _get-list-backups-of-an-ha-instance-version-accountid-ha-haid-backups:

List backups of an HA instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /{version}/{accountId}/ha/{haId}/backups

Lists backups for the HA instance specified by ha_id.

This operation lists the backups of the HA instance specified by ha_id.

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
|{haId}                    |String                   |The ID for the specified |
|                          |                         |HA instance.             |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

**Example List backups of an HA instance: JSON request**

The following example shows the List backups of an HA instance request:

.. code::

   GET /v1.0/1234/ha/130922a2-b9ab-4e95-86be-9c5d79171b5e/backups HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

Response
--------

**Example List backups of an HA instance: JSON response**

The following example shows the List backups of an HA instance response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.12)
   Content-Length: 2032
   Date: Tue, 01 Sep 2015 03:47:08 GMT
   Connection: close
   Server: Jetty(8.0.y.z-SNAPSHOT)

      "backups":[
         {
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
         },
         {
            "status":"COMPLETED",
            "updated":"2015-08-31T22:22:52Z",
            "description":"my_ha_backup2",
            "datastore":{
               "version":"5.6",
               "type":"mysql",
               "version_id":"1379cc8b-4bc5-4c4a-9e9d-7a9ad27c0866"
            },
            "id":"c6bbca39-e530-41f3-b073-03144dea04e3",
            "size":0.18,
            "is_automated":0,
            "name":"ha-backup2",
            "parent_id":null,
            "created":"2015-08-31T22:22:46Z",
            "flavor_ram":1024,
            "instance_id":null,
            "source":{
               "type":"ha",
               "id":"130922a2-b9ab-4e95-86be-9c5d79171b5e"
            },
            "locationRef":"https://snet-storage101.dfw1.clouddrive.com/v1/MossoCloudFS_938359/z_CLOUDDB_BACKUPS/c6bbca39-e530-41f3-b073-03144dea04e3.xbstream.gz",
            "type":"InnoBackupEx",
            "volume_size":1
         },
         {
            "status":"COMPLETED",
            "updated":"2015-08-31T22:16:30Z",
            "description":"my_ha_backup1",
            "datastore":{
               "version":"5.6",
               "type":"mysql",
               "version_id":"1379cc8b-4bc5-4c4a-9e9d-7a9ad27c0866"
            },
            "id":"0c1b5616-fdc5-45ae-b2dc-6f1440d55d0e",
            "size":0.18,
            "is_automated":0,
            "name":"ha-backup1",
            "parent_id":null,
            "created":"2015-08-31T22:16:25Z",
            "flavor_ram":1024,
            "instance_id":null,
            "source":{
               "type":"ha",
               "id":"130922a2-b9ab-4e95-86be-9c5d79171b5e"
            },
            "locationRef":"https://snet-storage101.dfw1.clouddrive.com/v1/MossoCloudFS_938359/z_CLOUDDB_BACKUPS/0c1b5616-fdc5-45ae-b2dc-6f1440d55d0e.xbstream.gz",
            "type":"InnoBackupEx",
            "volume_size":1
         }
      ]
   }
