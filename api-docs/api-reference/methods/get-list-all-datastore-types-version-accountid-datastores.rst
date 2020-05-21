
.. _get-list-all-datastore-types-version-accountid-datastores:

List all datastore types
~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /{version}/{accountId}/datastores

Lists all datastore types.

This operation lists all datastore types.

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

This operation does not accept a request body.

**Example List all datastore types: JSON request**

The following example shows the List all datastore types request:

.. code::

   GET /v1.0/1234/datastores HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

Response
--------

**Example List all datastore types: JSON response**

The following example shows the List all datastore types response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/8.5.0.1)
   Content-Length: 14081
   Date: Thu, 13 Feb 2014 21:47:14 GMT

   {
       "datastores": [
           {
               "default_version": "e3b358bb-9bc0-42a8-be95-6ebd6c437ef7",
               "name": "mariadb",
               "id": "17fe6921-f660-450e-bf90-8a6bd33a0cee",
               "links": [
                   {
                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/datastores/17fe6921-f660-450e-bf90-8a6bd33a0cee",
                       "rel": "self"
                   },
                   {
                       "href": "https://api.staging.ord1.clouddb.rackspace.net/datastores/17fe6921-f660-450e-bf90-8a6bd33a0cee",
                       "rel": "bookmark"
                   }
               ],
               "versions": [
                   {
                       "flavors": [
                           {
                               "ram": 512,
                               "id": 1,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/1",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/1",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "512MB Instance"
                           },
                           {
                               "ram": 1024,
                               "id": 2,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/2",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/2",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "1GB Instance"
                           },
                           {
                               "ram": 2048,
                               "id": 3,
                               "links": [
                                   {
                                      "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/3",
                                      "rel": "self"
                                   },
                                   {
                                      "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/3",
                                      "rel": "bookmark"
                                   }
                               ],
                               "name": "2GB Instance"
                           },
                           {
                               "ram": 4096,
                               "id": 4,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/4",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/4",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "4GB Instance"
                           },
                           {
                               "ram": 8192,
                               "id": 5,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/5",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/5",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "8GB Instance"
                           },
                           {
                               "ram": 16384,
                               "id": 6,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/6",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/6",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "16GB Instance"
                           },
                           {
                               "ram": 32768,
                               "id": 7,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/7",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/7",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "32GB Instance"
                           },
                           {
                               "ram": 65536,
                               "id": 8,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/8",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/8",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "64GB Instance"
                           }
                       ],
                       "scheduled_backup_supported": true,
                       "name": "10.4",
                       "links": [
                           {
                               "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/datastores/versions/e3b358bb-9bc0-42a8-be95-6ebd6c437ef7",
                               "rel": "self"
                           },
                           {
                               "href": "https://api.staging.ord1.clouddb.rackspace.net/datastores/versions/e3b358bb-9bc0-42a8-be95-6ebd6c437ef7",
                               "rel": "bookmark"
                           }
                       ],
                       "deprecated": false,
                       "databases_supported": true,
                       "id": "e3b358bb-9bc0-42a8-be95-6ebd6c437ef7",
                       "replication_supported": true,
                       "users_supported": true,
                       "backup_supported": true,
                       "configurations_supported": true,
                       "ha_supported": true,
                       "volumes_supported": true,
                       "monitoring_supported": true,
                       "at_rest_encryption_supported": false
                   },
                   {
                       "flavors": [
                           {
                               "ram": 512,
                               "id": 1,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/1",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/1",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "512MB Instance"
                           },
                           {
                               "ram": 1024,
                               "id": 2,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/2",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/2",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "1GB Instance"
                           },
                           {
                               "ram": 2048,
                               "id": 3,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/3",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/3",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "2GB Instance"
                           },
                           {
                               "ram": 4096,
                               "id": 4,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/4",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/4",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "4GB Instance"
                           },
                           {
                               "ram": 8192,
                               "id": 5,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/5",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/5",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "8GB Instance"
                           },
                           {
                               "ram": 16384,
                               "id": 6,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/6",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/6",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "16GB Instance"
                           },
                           {
                               "ram": 32768,
                               "id": 7,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/7",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/7",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "32GB Instance"
                           },
                           {
                               "ram": 65536,
                               "id": 8,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/8",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/8",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "64GB Instance"
                           }
                       ],
                       "scheduled_backup_supported": true,
                       "name": "10.4enc",
                       "links": [
                           {
                               "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/datastores/versions/8a63ae1a-7832-499f-9be9-9e95819bf9f0",
                               "rel": "self"
                           },
                           {
                               "href": "https://api.staging.ord1.clouddb.rackspace.net/datastores/versions/8a63ae1a-7832-499f-9be9-9e95819bf9f0",
                               "rel": "bookmark"
                           }
                       ],
                       "deprecated": false,
                       "databases_supported": true,
                       "id": "8a63ae1a-7832-499f-9be9-9e95819bf9f0",
                       "replication_supported": true,
                       "users_supported": true,
                       "backup_supported": true,
                       "configurations_supported": true,
                       "ha_supported": true,
                       "volumes_supported": true,
                       "monitoring_supported": true,
                       "at_rest_encryption_supported": true
                   }
               ]
           },
           {
               "default_version": "0b058cca-ed2b-46e7-8736-abbb4242df83",
               "name": "mysql",
               "id": "749239dc-4805-4d9c-a5c3-3befee6e572f",
               "links": [
                   {
                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/datastores/749239dc-4805-4d9c-a5c3-3befee6e572f",
                       "rel": "self"
                   },
                   {
                       "href": "https://api.staging.ord1.clouddb.rackspace.net/datastores/749239dc-4805-4d9c-a5c3-3befee6e572f",
                       "rel": "bookmark"
                   }
               ],
               "versions": [
                   {
                       "flavors": [
                           {
                               "ram": 1024,
                               "id": 2,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/2",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/2",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "1GB Instance"
                           },
                           {
                               "ram": 2048,
                               "id": 3,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/3",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/3",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "2GB Instance"
                           },
                           {
                               "ram": 4096,
                               "id": 4,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/4",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/4",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "4GB Instance"
                           },
                           {
                               "ram": 8192,
                               "id": 5,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/5",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/5",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "8GB Instance"
                           },
                           {
                               "ram": 16384,
                               "id": 6,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/6",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/6",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "16GB Instance"
                           },
                           {
                               "ram": 32768,
                               "id": 7,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/7",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/7",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "32GB Instance"
                           },
                           {
                               "ram": 65536,
                               "id": 8,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/8",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/8",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "64GB Instance"
                           }
                       ],
                       "scheduled_backup_supported": true,
                       "name": "5.7",
                       "links": [
                           {
                               "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/datastores/versions/564490bd-ddb9-4d84-a714-868370e36f48",
                               "rel": "self"
                           },
                           {
                               "href": "https://api.staging.ord1.clouddb.rackspace.net/datastores/versions/564490bd-ddb9-4d84-a714-868370e36f48",
                               "rel": "bookmark"
                           }
                       ],
                       "deprecated": false,
                       "databases_supported": true,
                       "id": "564490bd-ddb9-4d84-a714-868370e36f48",
                       "replication_supported": true,
                       "users_supported": true,
                       "backup_supported": true,
                       "configurations_supported": true,
                       "ha_supported": true,
                       "volumes_supported": true,
                       "monitoring_supported": true,
                       "at_rest_encryption_supported": false
                   },
                   {
                       "flavors": [
                           {
                               "ram": 1024,
                               "id": 2,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/2",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/2",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "1GB Instance"
                           },
                           {
                               "ram": 2048,
                               "id": 3,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/3",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/3",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "2GB Instance"
                           },
                           {
                               "ram": 4096,
                               "id": 4,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/4",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/4",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "4GB Instance"
                           },
                           {
                               "ram": 8192,
                               "id": 5,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/5",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/5",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "8GB Instance"
                           },
                           {
                               "ram": 16384,
                               "id": 6,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/6",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/6",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "16GB Instance"
                           },
                           {
                               "ram": 32768,
                               "id": 7,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/7",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/7",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "32GB Instance"
                           },
                           {
                               "ram": 65536,
                               "id": 8,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/8",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/8",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "64GB Instance"
                           }
                       ],
                       "scheduled_backup_supported": true,
                       "name": "8.0",
                       "links": [
                           {
                               "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/datastores/versions/0b058cca-ed2b-46e7-8736-abbb4242df83",
                               "rel": "self"
                           },
                           {
                               "href": "https://api.staging.ord1.clouddb.rackspace.net/datastores/versions/0b058cca-ed2b-46e7-8736-abbb4242df83",
                               "rel": "bookmark"
                           }
                       ],
                       "deprecated": false,
                       "databases_supported": true,
                       "id": "0b058cca-ed2b-46e7-8736-abbb4242df83",
                       "replication_supported": true,
                       "users_supported": true,
                       "backup_supported": true,
                       "configurations_supported": true,
                       "ha_supported": true,
                       "volumes_supported": true,
                       "monitoring_supported": true,
                       "at_rest_encryption_supported": false
                   }
               ]
           },
           {
               "default_version": "a831457a-a8fd-4053-b9e8-b90724af78b1",
               "name": "percona",
               "id": "379f9efc-d029-424a-a6b3-d14bda630150",
               "links": [
                   {
                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/datastores/379f9efc-d029-424a-a6b3-d14bda630150",
                       "rel": "self"
                   },
                   {
                       "href": "https://api.staging.ord1.clouddb.rackspace.net/datastores/379f9efc-d029-424a-a6b3-d14bda630150",
                       "rel": "bookmark"
                   }
               ],
               "versions": [
                   {
                       "flavors": [
                           {
                               "ram": 512,
                               "id": 1,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/1",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/1",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "512MB Instance"
                           },
                           {
                               "ram": 1024,
                               "id": 2,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/2",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/2",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "1GB Instance"
                           },
                           {
                               "ram": 2048,
                               "id": 3,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/3",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/3",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "2GB Instance"
                           },
                           {
                               "ram": 4096,
                               "id": 4,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/4",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/4",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "4GB Instance"
                           },
                           {
                               "ram": 8192,
                               "id": 5,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/5",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/5",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "8GB Instance"
                           },
                           {
                               "ram": 16384,
                               "id": 6,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/6",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/6",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "16GB Instance"
                           },
                           {
                               "ram": 32768,
                               "id": 7,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/7",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/7",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "32GB Instance"
                           },
                           {
                               "ram": 65536,
                               "id": 8,
                               "links": [
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/flavors/8",
                                       "rel": "self"
                                   },
                                   {
                                       "href": "https://api.staging.ord1.clouddb.rackspace.net/flavors/8",
                                       "rel": "bookmark"
                                   }
                               ],
                               "name": "64GB Instance"
                           }
                       ],
                       "scheduled_backup_supported": true,
                       "name": "5.7",
                       "links": [
                           {
                               "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/5821443/datastores/versions/a831457a-a8fd-4053-b9e8-b90724af78b1",
                               "rel": "self"
                           },
                           {
                               "href": "https://api.staging.ord1.clouddb.rackspace.net/datastores/versions/a831457a-a8fd-4053-b9e8-b90724af78b1",
                               "rel": "bookmark"
                           }
                       ],
                       "deprecated": false,
                       "databases_supported": true,
                       "id": "a831457a-a8fd-4053-b9e8-b90724af78b1",
                       "replication_supported": true,
                       "users_supported": true,
                       "backup_supported": true,
                       "configurations_supported": true,
                       "ha_supported": true,
                       "volumes_supported": true,
                       "monitoring_supported": true,
                       "at_rest_encryption_supported": false
                   }
               ]
           }
       ]
   }
