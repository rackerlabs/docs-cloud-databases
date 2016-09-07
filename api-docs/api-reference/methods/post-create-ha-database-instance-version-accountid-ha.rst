.. _post-create-ha-database-instance-version-accountid-ha:

Create HA database instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /{version}/{accountId}/ha

This operation creates a new HA instance. The ``name`` of the HA instance is a
required attribute.

The following tables shows the required and optional attributes for the
operation.


.. list-table:: **Required and optional attributes for Create HA instance**
   :widths: 20 20 40
   :header-rows: 1

   * - **Name**
     - **Type**
     - **Description**
   * - name
     - String
     - *(Required)* Specifies the name of the HA instance. The length should be limited to
       255 characters and any characters are permitted.
   * - datastore
     - Object
     - Specifies database version and type for the datastore.
   * - datastore.\ **version**
     - String
     - *(Required)* The database software release for the datastore.
   * - datastore.\ **type**
     - String
     - *(Required)* The database type for the datastore, for example ``MYSQL``.
   * - replica_source
     - Object 
     - Specifies properties for the replica.
   * - replica_source.\ **name**
     - String
     - *(Required)* Specifies the name for the replica. Refer to the request example
       for the required json format.
   * - replica_source.\ **flavor**
     - String
     - *(Required)* The flavor ID that specifies the database hardware
       configuration for the replica. You can find the available flavor IDs
       in the response returned by the
       :ref:`List Flavors <listing flavors>` API operation.
   * - replica_source.\ **volume**
     - String
     - *(Required)* Specifies the volume size in gigabytes (GB) for the replica.
       The value specified must be between 1 and 300.
   * - networks
     - Comma-separated list
     - List of networks to be associated with the HA group. For example:
       ``{“networks”:[“public”,“servicenet”]}``
       If you do not specify any networks, the value defaults to
       ``servicenet`. 
       If you need a public network in addition to servicenet, specify a value.
       For example, ``"networks": ["public”]``. If you want the HA group to
       have options for both a private servicenet and a public network, specify
       ``"networks": ["public", "servicenet"]``.
   * - acls
     - Comma-separated list
     - List of IP based ACLs in the CIDR format. This is required to allow the
       HA group access to the specified IP. By default, the HA group access is
       blocked. For example: 
       ``"acls": [{"address": "10.0.0.0/0"}, {"address": “1.2.3.4/5”}]``.
       Additionally, if it is not specified while creating the HA group, it
       can be added later. For details, see 
       :ref:`Add ACLs to an HA instance <add-acls-to-an-ha-instance>`.
   * - configuration
     - String
     - ID of the configuration group.


The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |Accepted                 |The request has been     |
|                          |                         |accepted for processing. |
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

The following table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{accountId}               |String                   |The account ID of the    |
|                          |                         |owner of the specified   |
|                          |                         |instance.                |
+--------------------------+-------------------------+-------------------------+

**Example Create HA database instance: JSON request**

.. code::

   POST /v1.0/1234/ha HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: e3b2c743aebf467fb6b91cbb644c036e
   Accept: application/json
   Content-Type: application/json
   {
      "ha":{
         "datastore":{
            "version":"5.6",
            "type":"MYSQL"
         },
         "replicas":[
            {
               "volume":{
                  "size":1
               },
               "flavorRef":"2",
               "name":"source_replica1"
            }
         ],
         "name":"ha-1",
         "networks":[
            "servicenet",
            "public"
         ],
         "configuration": "bbbcdf40-e4cc-423d-8e4b-1f0c7190dac4",
         "acls":[
            {
               "address":"10.0.0.0/0"
            },
            {
               "address":"1.2.3.4/5"
            }
         ],
         "replica_source":[
            {
               "volume":{
                  "size":1
               },
               "flavorRef":"2",
               "name":"source"
            }
         ]
      }
   }

Response
--------

**Example Create HA database instance: JSON response**

.. code::

   HTTP/1.1 202 Accepted
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: ‘219’
   Date: Fri, 08 May 2015 13:03:06 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

   {
      "ha_instance":{
         "name":"ha-1",
         "tenant_id":"1234",
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

         ],
         "replica_source":[

         ],
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
         "id":"e7fdf90b-7140-4edb-b449-e093d55008fb",
         "state":"BUILD",
         "acls":[

         ],
         "datastore":{
            "version":"5.6",
            "type":"mysql"
         },
         "networks":[

         ]
      }
   }
