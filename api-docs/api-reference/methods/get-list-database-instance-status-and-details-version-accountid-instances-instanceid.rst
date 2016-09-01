
.. _get-list-database-instance-status-and-details-version-accountid-instances-instanceid:

List database instance status and details
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /{version}/{accountId}/instances/{instanceId}

Lists status and details for a specified database instance.

This operation lists the status and details of the specified database instance.
The operation also lists the configuration group id/name if the running
instance has been associated with a configuration group. For HA instances,
lists details for the source instance part or the replica instance part,
depending on the ID specified.

This operation lists the volume size in gigabytes (GB) and the approximate GB
used.

.. note::
   After instance creation, the ``used`` size of your volume will be greater
   than 0. This is expected and due to the automatic creation of non-empty
   transaction logs for database optimization. The ``used`` attribute is not
   returned in the response when the status for the instance is BUILD, REBOOT,
   RESIZE, or ERROR.

Refer to :ref:`Database instance status <cdb-dg-generalapi-dbinstance>` for a
list of possible database instance statuses that may be returned.

The list operations return a DNS-resolvable hostname associated with the
database instance instead of an IP address. Since the hostname always resolves
to the correct IP address of the database instance, this relieves the user
from the task of maintaining the mapping. Note that although the IP address
may likely change on resizing, migrating, and so forth, the hostname always
resolves to the correct database instance.

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

**Example List database instance status and details: JSON request**

The following example shows the List database instance status and details
request:

.. code::

   GET /v1.0/1234/instances/d4603f69-ec7e-4e9b-803f-600b9205576f HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

**Example List database instance status and details with configuration request: JSON**

The following example shows the List database instance status and details with
configuration request:

.. code::

   GET /v1.0/1234/instances/d4603f69-ec7e-4e9b-803f-600b9205576f HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

**Example List details of a source instance in an HA setup request: JSON**


The following example shows the List database instance status and details of a
source instance in an HA setup request:

.. code::

   GET /v1.0/1234/instances/82cba72c-26a3-4e61-a4f1-7c65647b1c9f HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: e3b2c743aebf467fb6b91cbb644c036e
   Accept: application/json
   Content-Type: application/json

**Example List details of a replica instance in an HA setup request: JSON**


The following example shows the List database instance status and details of
a replica instance in an HA setup request:

.. code::

   GET /v1.0/1234/instances/4eeeb7a6-0dee-4e66-b433-f6462d45c580  HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: e3b2c743aebf467fb6b91cbb644c036e
   Accept: application/json
   Content-Type: application/json

Response
--------

**Example List database instance status and details: JSON response**


The following example shows the List database instance status and details
response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: 718
   Date: Thu, 13 Feb 2014 21:47:15 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

   {
       "instance": {
           "created": "2014-02-13T21:47:13",
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
           "hostname": "e09ad9a3f73309469cf1f43d11e79549caf9acf2.rackspaceclouddb.com",
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
           "updated": "2014-02-13T21:47:15",
           "volume": {
               "size": 2,
               "used": 0.16
           }
       }
   }

**Example List database instance status and details with configuration response: JSON**

The following example shows the List database instance status and details with configuration response:

.. code::

   {
    "instance": {
          "created": "2012-01-25T21:53:09Z",
          "flavor": {
              "id": "1",
              "links": [
                  {
                      "href": "https://endpoint/v1.0/1234/flavors/1",
                      "rel": "self"
                  },
                  {
                      "href": "https://endpoint/flavors/1",
                      "rel": "bookmark"
                  }
              ]
          },
          "configuration": {
              "id": "12345678-1111-2222-3333-444444444444",
              "name": "MySQL Tuned Config",
              "links": [
                  {
                      "href": "https://endpoint/v1.0/1234/configurations/12345678-1111-2222-3333-444444444444",
                      "rel": "self"
                  },
                  {
                      "href": "https://endpoint/configurations/12345678-1111-2222-3333-444444444444",
                      "rel": "bookmark"
                  }
              ]
          },
          "hostname": "e09ad9a3f73309469cf1f43d11e79549caf9acf2.hostname",
          "id": "dea5a2f7-3ec7-4496-adab-0abb5a42d635",
          "links": [
              {
                  "href": "https://endpoint/v1.0/1234/instances/dea5a2f7-3ec7-4496-adab-0abb5a42d635",
                  "rel": "self"
              },
              {
                  "href": "https://endpoint/instances/dea5a2f7-3ec7-4496-adab-0abb5a42d635",
                  "rel": "bookmark"
              }
          ],
          "name": "json_rack_instance",
          "status": "BUILD",
          "updated": "2012-01-25T21:53:10Z",
          "volume": {
              "size": 2
          }
      }
   }

Notice in the response example above the configuration named "MySQL Tuned
Config" is returned since the instance is associated with that configuration.

**Example List details of a source instance in an HA setup response: JSON**

The following example shows the List database instance status and details of
a source instance in an HA setup response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: ‘1243’
   Date: Fri, 08 May 2015 15:56:23 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

   {
      "instance":{
         "status":"ACTIVE",
         "updated":"2015-05-08T13:03:43Z",
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
            "used":0.18,
            "size":1
         },
         "created":"2015-05-08T13:03:08Z",
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
      }
   }

**Example List details of a replica instance in an HA setup response: JSON**

The following example shows the List database instance status and details of
a replica instance in an HA setup response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: ‘1225’
   Date: Fri, 08 May 2015 16:32:09 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

   {
      "instance":{
         "status":"ACTIVE",
         "updated":"2015-05-08T13:06:55Z",
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
         "created":"2015-05-08T13:05:41Z",
         "hostname":"7e51adcbf8ded6ed1d41311e2e449d5836914dc2.ord.rackspaceclouddb.com",
         "id":"4eeeb7a6-0dee-4e66-b433-f6462d45c580",
         "volume":{
            "used":0.18,
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
   }
