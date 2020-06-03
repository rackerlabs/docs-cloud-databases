
.. _get-list-datastore-versions-for-datastore-version-accountid-datastores-datastoreid-versions:

List datastore versions for datastore
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /{version}/{accountId}/datastores/{datastoreId}/versions

Lists all datastore versions for the specified datastore.

This operation lists all datastore versions for the specified datastore.

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
|{datastoreId}             |String                   |The ID for the specified |
|                          |                         |datastore.               |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

**Example List datastore versions for datastore: JSON request**

The following example shows the List all datastore versions for datastore
request:

.. code::

   GET /v1.0/1234/datastores/a00000a0-00a0-0a00-00a0-000a000000aa/versions HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

Response
--------

**Example List datastore versions for datastore: JSON response**

The following example shows the List all datastore versions for datastore
response:

.. code::

    HTTP/1.1 200 OK
    Content-Type: application/json
    Via: 1.1 Repose (Repose/8.5.0.1)
    Content-Length: 4952
    Date: Thu, 13 Feb 2014 21:47:14 GMT

    {
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
                "ha_supported": true,
                "users_supported": true,
                "backup_supported": true,
                "configurations_supported": true,
                "datastore": "749239dc-4805-4d9c-a5c3-3befee6e572f",
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
                "ha_supported": true,
                "users_supported": true,
                "backup_supported": true,
                "configurations_supported": true,
                "datastore": "749239dc-4805-4d9c-a5c3-3befee6e572f",
                "volumes_supported": true,
                "monitoring_supported": true,
                "at_rest_encryption_supported": false
            }
        ]
    }
