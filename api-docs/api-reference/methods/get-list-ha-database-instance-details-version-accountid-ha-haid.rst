
.. _get-list-ha-database-instance-details-version-accountid-ha-haid:

List HA database instance details
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /{version}/{accountId}/ha/{haId}

Lists details for a specified HA instance.

This operation lists the details of the specified HA instance.

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

**Example List HA database instance details: JSON request**

The following example shows the List HA instance status and details request:

.. code::

   GET /v1.0/1234/ha/e7fdf90b-7140-4edb-b449-e093d55008fb HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: e3b2c743aebf467fb6b91cbb644c036e
   Accept: application/json
   Content-Type: application/json

Response
--------

**Example List HA database instance details: JSON response**

The following example shows the List HA instance status and details response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: ‘1885’
   Date: Fri, 08 May 2015 13:25:30 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

   {
     "ha_instance":{
      "name":"ha-1",
      "tenant_id":"5919009",
      "volume":{
         "size":1
      },
      "flavor":{
         "id":9,
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
      "replicas":[
         {
            "status":"ACTIVE",
            "name":"source_replica1",
            "links":{

            },
            "hostname":"7e51adcbf8ded6ed1d41311e2e449d5836914dc2.ord.rackspaceclouddb.com",
            "id":"4eeeb7a6-0dee-4e66-b433-f6462d45c580",
            "volume":{
               "size":1
            },
            "ha_id":"e7fdf90b-7140-4edb-b449-e093d55008fb",
            "flavor":{
               "id":"2",
               "links":{

               }
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
      ],
      "replica_source":[
         {
            "status":"ACTIVE",
            "name":"source",
            "links":{

            },
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
               "links":{

               }
            },
            "datastore":{
               "version":"5.6",
               "type":"mysql"
            },
            "ha_id":"e7fdf90b-7140-4edb-b449-e093d55008fb"
         }
      ],
      "id":"e7fdf90b-7140-4edb-b449-e093d55008fb",
      "state":"ACTIVE",
      "acls":[

      ],
      "datastore":{
         "version":"5.6",
         "type":"mysql"
      },
      "configuration": null,
      "networks":[
         {
            "access":"read",
            "network":"servicenet",
            "port":3307,
            "address":"cdd9187448314cc0b2d33052686ba2c4.publb.ord.rackspaceclouddb.com"
         },
         {
            "access":"write",
            "network":"servicenet",
            "port":3306,
            "address":"cdd9187448314cc0b2d33052686ba2c4.publb.ord.rackspaceclouddb.com"
         }
      ]
    }
  }
