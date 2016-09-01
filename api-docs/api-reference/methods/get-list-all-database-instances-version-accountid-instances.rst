
.. _get-list-all-database-instances-version-accountid-instances:

List all database instances
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /{version}/{accountId}/instances

Lists the status and information for all database instances.

This operation lists the status and information for all database instances.

This operation lists the sources and replicas part for HA database instances.

Refer to :ref:`Database instance status <cdb-dg-generalapi-dbinstance>` for a
list of possible database instance statuses that may be returned.

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

This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|include_replicas          |String *(Optional)*      |When                     |
|                          |                         |``include_replicas`` is  |
|                          |                         |set to ``false``, the    |
|                          |                         |replica instances are    |
|                          |                         |filtered out of the      |
|                          |                         |response.                |
+--------------------------+-------------------------+-------------------------+
|include_ha                |String *(Optional)*      |When ``include_ha`` is   |
|                          |                         |set to ``false``, the HA |
|                          |                         |instances are filtered   |
|                          |                         |out of the response.     |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

**Example List all database instances: JSON request**

The following example shows the List all database instances request:

.. code::

   GET /v1.0/1234/instances HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

**Example List all sources and replicas part of an HA instance request: JSON**

The following example shows the List all sources and replicas part of an HA instance request:

.. code::

   GET /v1.0/1234/instances HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: e3b2c743aebf467fb6b91cbb644c036e
   Accept: application/json
   Content-Type: application/json

**Example List all instances and filter out instances part of an HA setup request: JSON**

The following example shows the List all instances and filter out instances part of an HA setup request:

.. code::

   GET /v1.0/1234/instances?include_ha=false HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

Response
--------

**Example List all database instances: JSON response**

The following example shows the List all database instances response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: 1102
   Date: Thu, 13 Feb 2014 21:47:15 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

   {
       "instances": [
           {
               "datastore": {
                   "type": "mysql",
                   "version": "5.1"
               },
               "flavor": {
                   "id": "1",
                   "links": [
                       {
                           "href": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/flavors/1",
                           "rel": "self"
                       },
                       {
                           "href": "https://ord.databases.api.rackspacecloud.com/flavors/1",
                           "rel": "bookmark"
                       }
                   ]
               },
               "id": "d4603f69-ec7e-4e9b-803f-600b9205576f",
               "links": [
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances/d4603f69-ec7e-4e9b-803f-600b9205576f",
                       "rel": "self"
                   },
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/instances/d4603f69-ec7e-4e9b-803f-600b9205576f",
                       "rel": "bookmark"
                   }
               ],
               "name": "json_rack_instance",
               "status": "ACTIVE",
               "volume": {
                   "size": 2
               }
           },
           {
               "datastore": {
                   "type": "mysql"
               },
               "flavor": {
                   "id": "1",
                   "links": [
                       {
                           "href": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/flavors/1",
                           "rel": "self"
                       },
                       {
                           "href": "https://ord.databases.api.rackspacecloud.com/flavors/1",
                           "rel": "bookmark"
                       }
                   ]
               },
               "id": "dcf2c32b-241d-4c39-af70-1001dfe946d6",
               "links": [
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances/dcf2c32b-241d-4c39-af70-1001dfe946d6",
                       "rel": "self"
                   },
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/instances/dcf2c32b-241d-4c39-af70-1001dfe946d6",
                       "rel": "bookmark"
                   }
               ],
               "name": "xml_rack_instance",
               "status": "ACTIVE",
               "volume": {
                   "size": 2
               }
           }
       ]
   }

**Example List all sources and replicas part of an HA instance response: JSON**

The following example shows the List all sources and replicas part of an HA instance response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: ‘19877’
   Date: Fri, 08 May 2015 15:56:23 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

   {
      "instances":[
         {
            "status":"ACTIVE",
            "name":"try-1-master_replica2",
            "links":[
               {
                  "href":"https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances/35b88c2c-60ba-4f71-af7a-6dd22047dd73",
                  "rel":"self"
               },
               {
                  "href":"https://ord.databases.api.rackspacecloud.com/instances/35b88c2c-60ba-4f71-af7a-6dd22047dd73",
                  "rel":"bookmark"
               }
            ],
            "hostname":"1a0ddee64a843a8afb875c0799c720d134374452.ord.rackspaceclouddb.com",
            "id":"35b88c2c-60ba-4f71-af7a-6dd22047dd73",
            "volume":{
               "size":1
            },
            "ha_id":"0236f3ee-c1c6-40d1-8388-69da13c09cfe",
            "flavor":{
               "id":"2",
               "links":[
                  {
                     "href":"https://ord.databases.api.rackspacecloud.com/v1.0/1234/flavors/2",
                     "rel":"self"
                  },
                  {
                     "href":"https://ord.databases.api.rackspacecloud.com/flavors/2",
                     "rel":"bookmark"
                  }
               ]
            },
            "datastore":{
               "version":"5.6",
               "type":"mysql"
            },
            "replica_of":{
               "id":"8ae74c7c-b4d2-4461-92ee-41c824a79124",
               "links":[
                  {
                     "href":"https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances/8ae74c7c-b4d2-4461-92ee-41c824a79124",
                     "rel":"self"
                  },
                  {
                     "href":"https://ord.databases.api.rackspacecloud.com/instances/8ae74c7c-b4d2-4461-92ee-41c824a79124",
                     "rel":"bookmark"
                  }
               ]
            }
         },
         {
            "status":"ACTIVE",
            "name":"source",
            "links":[
               {
                  "href":"https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances/82cba72c-26a3-4e61-a4f1-7c65647b1c9f",
                  "rel":"self"
               },
               {
                  "href":"https://ord.databases.api.rackspacecloud.com/instances/82cba72c-26a3-4e61-a4f1-7c65647b1c9f",
                  "rel":"bookmark"
               }
            ],
            "replicas":[
               {
                  "id":"4eeeb7a6-0dee-4e66-b433-f6462d45c580",
                  "links":[
                     {
                        "href":"https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances/4eeeb7a6-0dee-4e66-b433-f6462d45c580",
                        "rel":"self"
                     },
                     {
                        "href":"https://ord.databases.api.rackspacecloud.com/instances/4eeeb7a6-0dee-4e66-b433-f6462d45c580",
                        "rel":"bookmark"
                     }
                  ],
                  "name":"source_replica1"
               }
            ],
            "hostname":"55036bc3d34c36a44911414d0e92bba071f0bfc8.ord.rackspaceclouddb.com",
            "id":"82cba72c-26a3-4e61-a4f1-7c65647b1c9f",
            "volume":{
               "size":1
            },
            "flavor":{
               "id":"2",
               "links":[
                  {
                     "href":"https://ord.databases.api.rackspacecloud.com/v1.0/1234/flavors/2",
                     "rel":"self"
                  },
                  {
                     "href":"https://ord.databases.api.rackspacecloud.com/flavors/2",
                     "rel":"bookmark"
                  }
               ]
            },
            "datastore":{
               "version":"5.6",
               "type":"mysql"
            },
            "ha_id":"e7fdf90b-7140-4edb-b449-e093d55008fb"
         },
         {
            "status":"ACTIVE",
            "name":"source_replica1",
            "links":[
               {
                  "href":"https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances/4eeeb7a6-0dee-4e66-b433-f6462d45c580",
                  "rel":"self"
               },
               {
                  "href":"https://ord.databases.api.rackspacecloud.com/instances/4eeeb7a6-0dee-4e66-b433-f6462d45c580",
                  "rel":"bookmark"
               }
            ],
            "hostname":"7e51adcbf8ded6ed1d41311e2e449d5836914dc2.ord.rackspaceclouddb.com",
            "id":"4eeeb7a6-0dee-4e66-b433-f6462d45c580",
            "volume":{
               "size":1
            },
            "ha_id":"e7fdf90b-7140-4edb-b449-e093d55008fb",
            "flavor":{
               "id":"2",
               "links":[
                  {
                     "href":"https://ord.databases.api.rackspacecloud.com/v1.0/1234/flavors/2",
                     "rel":"self"
                  },
                  {
                     "href":"https://ord.databases.api.rackspacecloud.com/flavors/2",
                     "rel":"bookmark"
                  }
               ]
            },
            "datastore":{
               "version":"5.6",
               "type":"mysql"
            },
            "replica_of":{
               "id":"82cba72c-26a3-4e61-a4f1-7c65647b1c9f",
               "links":[
                  {
                     "href":"https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances/82cba72c-26a3-4e61-a4f1-7c65647b1c9f",
                     "rel":"self"
                  },
                  {
                     "href":"https://ord.databases.api.rackspacecloud.com/instances/82cba72c-26a3-4e61-a4f1-7c65647b1c9f",
                     "rel":"bookmark"
                  }
               ]
            }
         }
      ]
   }

**Example List all instances and filter out instances part of an HA setup response: JSON**

The following example shows the List all instances and filter out instances part of an HA setup response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: 697
   Date: Thu, 13 Feb 2014 21:47:17 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT

   {
      "instances":[
         {
            "status":"ACTIVE",
            "name":"master1",
            "links":[
               {
                  "href":"https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances/df9e5206-cc95-4131-9ea4-f928c99f1aec",
                  "rel":"self"
               },
               {
                  "href":"https://ord.databases.api.rackspacecloud.com/instances/df9e5206-cc95-4131-9ea4-f928c99f1aec",
                  "rel":"bookmark"
               }
            ],
            "replicas":[
               {
                  "id":"1b1fc872-00bb-4fc7-894f-b02e83609ae6",
                  "name":"slave1",
                  "links":[
                     {
                        "href":"https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances/1b1fc872-00bb-4fc7-894f-b02e83609ae6",
                        "rel":"self"
                     },
                     {
                        "href":"https://ord.databases.api.rackspacecloud.com/instances/1b1fc872-00bb-4fc7-894f-b02e83609ae6",
                        "rel":"bookmark"
                     }
                  ]
               },
               {
                  "id":"3ac8641f-293d-4533-ab7a-9be25070b98f",
                  "name":"slave2",
                  "links":[
                     {
                        "href":"https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances/3ac8641f-293d-4533-ab7a-9be25070b98f",
                        "rel":"self"
                     },
                     {
                        "href":"https://ord.databases.api.rackspacecloud.com/instances/3ac8641f-293d-4533-ab7a-9be25070b98f",
                        "rel":"bookmark"
                     }
                  ]
               }
            ],
            "ip":[
               "10.0.0.2"
            ],
            "id":"df9e5206-cc95-4131-9ea4-f928c99f1aec",
            "volume":{
               "size":1
            },
            "flavor":{
               "id":"9",
               "links":[
                  {
                     "href":"https://ord.databases.api.rackspacecloud.com/v1.0/1234/flavors/9",
                     "rel":"self"
                  },
                  {
                     "href":"https://ord.databases.api.rackspacecloud.com/flavors/9",
                     "rel":"bookmark"
                  }
               ]
            },
            "datastore":{
               "version":"5.6",
               "type":"mysql"
            }
         }
      ]
   }
