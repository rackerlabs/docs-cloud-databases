
.. _patch-attach-configuration-group-to-ha-instance-version-accountid-ha-haid.rst:

Attach configuration group to HA instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    PATCH /{version}/{accountId}/ha/{haId}

Attaches a specified :ref:`configuration group <concepts-configgroup>` to the
HA Instance.

.. note::
   If the configuration group has non-dynamic configuration parameters, the HA
   instance will be put in a ``RESTART_REQUIRED`` state. To enable the
   parameters on all the nodes (source and replicas of the HA group),
   :ref:`restart the HA instance<post-restart-ha-instance-version-accountid-ha-haid-action>`.

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |Success                  |Request succeeded.       |
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

**Example Attach Configuration Group to HA Instance: JSON request**

The following example shows the attach configuration group to HA Instance
request:

.. code::

   PATCH /v1.0/1234/ha/3a493f8c-9b9c-4ca1-845b-e3689abb1f5c HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json
   {      
       "ha_instance":{
          "configuration": "bbbcdf40-e4cc-423d-8e4b-1f0c7190dac4"
       } 
   }

Response
--------

**Example Attach Configuration Group to HA Instance: JSON response**


The following example shows the attach configuration group to HA Instance
response:

.. code::

   HTTP/1.1 202 Accepted
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.12)
   Content-Length: 0
   Date: Tue, 15 Mar 2016 16:13:15 GMT
   Connection: close
   Server: Jetty(8.0.y.z-SNAPSHOT)

**Example List HA database instance details after configuration group attached:
JSON response**

The following example shows the List HA instance status and details response
after configuration group is attached:

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
      "configuration":{
         "id":"bbbcdf40-e4cc-423d-8e4b-1f0c7190dac4",
         "links":[
            {
               "href":"https://ord.databases.api.rackspacecloud.com/v1.0/1234/configurations/bbbcdf40-e4cc-423d-8e4b-1f0c7190dac4",
               "rel":"self"
            },
            {
               "href":"https://ord.databases.api.rackspacecloud.com/configurations/bbbcdf40-e4cc-423d-8e4b-1f0c7190dac4",
               "rel":"bookmark"
            }
         ],
         "name":"database-configuration-1"
      },
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
