
.. _get-list-flavors-for-datastore-version-version-accountid-datastores-datastoretype-versions-versionid-flavors:

List flavors for datastore version
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /{version}/{accountId}/datastores/{datastoreType}/versions/{versionId}/flavors

Lists flavors for a datastore version.

This operation lists the flavors for a datastore version.

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
|{datastoreType}           |String                   |The datastore type, for  |
|                          |                         |example mysql.           |
+--------------------------+-------------------------+-------------------------+
|{versionId}               |String                   |The version for the      |
|                          |                         |specified datastore.     |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

**Example List flavors for datastore version: JSON request**

The following example shows the Lists flavors for datastore version request:

.. code::

   GET /v1.0/1234/datastores/mysql/versions/c11500fb-a034-4116-9f6b-4e0b32cea39d/flavors HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

Response
--------

**Example List flavors for datastore version: JSON response**

The following example shows the Lists flavors for datastore version response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: 1186
   Date: Thu, 13 Feb 2014 21:47:13 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

   {
       "flavors": [
           {
               "id": 1,
               "links": [
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/flavors/1",
                       "rel": "self"
                   },
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/flavors/1",
                       "rel": "bookmark"
                   }
               ],
               "name": "512MB Instance",
               "ram": 512
           },
           {
               "id": 2,
               "links": [
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/flavors/2",
                       "rel": "self"
                   },
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/flavors/2",
                       "rel": "bookmark"
                   }
               ],
               "name": "1GB Instance",
               "ram": 1024
           },
           {
               "id": 3,
               "links": [
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/flavors/3",
                       "rel": "self"
                   },
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/flavors/3",
                       "rel": "bookmark"
                   }
               ],
               "name": "2GB Instance",
               "ram": 2048
           },
           {
               "id": 4,
               "links": [
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/flavors/4",
                       "rel": "self"
                   },
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/flavors/4",
                       "rel": "bookmark"
                   }
               ],
               "name": "4GB Instance",
               "ram": 4096
           },
           {
               "id": 5,
               "links": [
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/flavors/5",
                       "rel": "self"
                   },
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/flavors/5",
                       "rel": "bookmark"
                   }
               ],
               "name": "8GB Instance",
               "ram": 8192
           },
           {
               "id": 6,
               "links": [
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/flavors/6",
                       "rel": "self"
                   },
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/flavors/6",
                       "rel": "bookmark"
                   }
               ],
               "name": "16GB Instance",
               "ram": 16384
           },
           {
               "id": 7,
               "links": [
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/v1.0/647683/flavors/7",
                       "rel": "self"
                   },
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/flavors/7",
                       "rel": "bookmark"
                   }
               ],
               "name": "32GB Instance",
               "ram": 32768
           },
           {
               "id": 8,
               "links": [
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/v1.0/647683/flavors/8",
                       "rel": "self"
                   },
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/flavors/8",
                       "rel": "bookmark"
                   }
               ],
               "name": "64GB Instance",
               "ram": 65536
           }
       ]
   }
