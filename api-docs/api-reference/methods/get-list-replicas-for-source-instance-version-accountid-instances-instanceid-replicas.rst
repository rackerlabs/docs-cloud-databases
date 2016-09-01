
.. _get-list-replicas-for-source-instance-version-accountid-instances-instanceid-replicas:

List replicas for source instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /{version}/{accountId}/instances/{instanceId}/replicas

Lists replicas for a specified source instance.

This operation lists replicas for a specified source instance.

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
|{instanceId}              |String                   |The instance ID for the  |
|                          |                         |specified database       |
|                          |                         |instance.                |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

**Example List replicas for source instance: JSON request**

The following example shows the List replicas for source instance request:

.. code::

   GET /v1.0/1234/instances/df9e5206-cc95-4131-9ea4-f928c99f1aec/replicas HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

Response
--------

**Example List replicas for source instance: JSON response**

The following example shows the List replicas for source instance response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: 718
   Date: Thu, 13 Feb 2014 21:47:15 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

   {
      "instances":[
         {
            "status":"ACTIVE",
            "name":"replica1",
            "links":[
               {
                  "href":"https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances/1b1fc872-00bb-4fc7-894f-b02e83609ae6",
                  "rel":"self"
               },
               {
                  "href":"https://ord.databases.api.rackspacecloud.com/instances/1b1fc872-00bb-4fc7-894f-b02e83609ae6",
                  "rel":"bookmark"
               }
            ],
            "ip":[
               "10.0.0.3"
            ],
            "id":"1b1fc872-00bb-4fc7-894f-b02e83609ae6",
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
            },
            "replica_of":{
               "id":"df9e5206-cc95-4131-9ea4-f928c99f1aec",
               "links":[
                  {
                     "href":"https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances/df9e5206-cc95-4131-9ea4-f928c99f1aec",
                     "rel":"self"
                  },
                  {
                     "href":"https://ord.databases.api.rackspacecloud.com/instances/df9e5206-cc95-4131-9ea4-f928c99f1aec",
                     "rel":"bookmark"
                  }
               ]
            }
         },
         {
            "status":"ACTIVE",
            "name":"replica2",
            "links":[
               {
                  "href":"https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances/3ac8641f-293d-4533-ab7a-9be25070b98f",
                  "rel":"self"
               },
               {
                  "href":"https://ord.databases.api.rackspacecloud.com/instances/3ac8641f-293d-4533-ab7a-9be25070b98f",
                  "rel":"bookmark"
               }
            ],
            "ip":[
               "10.0.0.4"
            ],
            "id":"3ac8641f-293d-4533-ab7a-9be25070b98f",
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
            },
            "replica_of":{
               "id":"df9e5206-cc95-4131-9ea4-f928c99f1aec",
               "links":[
                  {
                     "href":"https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances/df9e5206-cc95-4131-9ea4-f928c99f1aec",
                     "rel":"self"
                  },
                  {
                     "href":"https://ord.databases.api.rackspacecloud.com/instances/df9e5206-cc95-4131-9ea4-f928c99f1aec",
                     "rel":"bookmark"
                  }
               ]
            }
         }
      ]
   }
