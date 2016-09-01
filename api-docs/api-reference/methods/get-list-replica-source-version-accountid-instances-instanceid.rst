
.. _get-list-replica-source-version-accountid-instances-instanceid:

List replica source
~~~~~~~~~~~~~~~~~~~

.. code::

    GET /{version}/{accountId}/instances/{instanceId}

Lists status and details for a specified replica source instance.

This operation lists the status and details of the specified replica source
instance. The operation also lists the configuration group id/name if the
running instance has been associated with a configuration group.

This operation lists the volume size in gigabytes (GB) and the approximate
GB used.

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

**Example List replica source: JSON request**

The following example shows the List replica source request:

.. code::

   GET /v1.0/1234/instances/8b499b45-52d6-402d-b398-f9d8f279c69a HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

Response
--------

**Example List replica source: JSON response**

The following example shows the List replica source response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: 718
   Date: Thu, 13 Feb 2014 21:47:15 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

   {
     "instance": {
       "status": "ACTIVE",
       "updated": "2014-09-26T19:15:57",
       "name": "t1_ALT_GUEST",
       "links": [
         {
           "href": " https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances/8b499b45-52d6-402d-b398-f9d8f279c69a",
           "rel": "self"
         },
         {
           "href": " https://ord.databases.api.rackspacecloud.com/instances /8b499b45-52d6-402d-b398-f9d8f279c69a",
           "rel": "bookmark"
         }
       ],
       "created": "2014-09-26T19:15:50",
       "ip": [
         "10.0.0.2"
       ],
       "replicas": [
         {
           "id": "3c691f06-bf9a-4618-b7ec-2817ce0cf254",
           "links": [
             {
               "href": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances /3c691f06-bf9a-4618-b7ec-2817ce0cf254",
               "rel": "self"
             },
             {
               "href": " https://ord.databases.api.rackspacecloud.com/instances /3c691f06-bf9a-4618-b7ec-2817ce0cf254",
               "rel": "bookmark"
             }
           ]
         }
       ],
       "id": "8b499b45-52d6-402d-b398-f9d8f279c69a",
       "volume": {
         "used": 0.54,
         "size": 1
       },
       "flavor": {
         "id": "9",
         "links": [
           {
             "href": “https://ord.databases.api.rackspacecloud.com/v1.0/1234/flavors/9",
             "rel": "self"
           },
           {
             "href": " https://ord.databases.api.rackspacecloud.com/flavors/9",
             "rel": "bookmark"
           }
         ]
       },
       "datastore": {
         "version": "5.6",
         "type": "mysql"
       }
     }
   }
