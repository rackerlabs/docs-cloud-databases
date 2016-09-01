
.. _get-list-configurations-version-accountid-configurations:

List configurations
~~~~~~~~~~~~~~~~~~~

.. code::

    GET /{version}/{accountId}/configurations

Lists all defined configuration group s for the tenant.

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

**Example List configurations: JSON request**

The following example shows the List configurations request:

.. code::

   GET /v1.0/1234/configurations HTTP/1.1
   Host: ord.databases.api.rackspacecloud.com
   User-Agent: python-troveclient
   Accept: application/json
   X-Auth-Token: 26640a608aa9482b888a1664376b8113

Response
--------

**Example List configurations: JSON response**

The following example shows the List configurations response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.12)
   Content-Length: 336
   Date: Thu, 31 Jul 2014 19:00:54 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

   {
       "configurations": [
           {
               "created": "2014-07-31T18:56:09",
               "datastore_name": "mysql",
               "datastore_version_id": "b00000b0-00b0-0b00-00b0-000b000000bb",
               "datastore_version_name": "5.6",
               "description": "example description",
               "id": "005a8bb7-a8df-40ee-b0b7-fc144641abc2",
               "name": "example-configuration-name",
               "updated": "2014-07-31T18:56:09"
           }
       ]
   }
