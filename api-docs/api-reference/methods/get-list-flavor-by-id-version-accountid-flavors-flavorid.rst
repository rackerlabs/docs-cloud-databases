
.. _get-list-flavor-by-id-version-accountid-flavors-flavorid:

List flavor by ID
~~~~~~~~~~~~~~~~~

.. code::

    GET /{version}/{accountId}/flavors/{flavorId}

Lists all flavor information about the specified flavor ID.

This operation lists all information for the specified flavor ID with details
of the RAM.

This resource is identical to the flavors found in the OpenStack Nova API, but
without the disk property.

.. note::
   The flavorId parameter should be an integer. If a floating point value is
   used for the flavorId parameter, the decimal portion is truncated and the
   integer portion is used as the value of the flavorId.

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
|{flavorId}                |String                   |The flavor ID for the    |
|                          |                         |specified flavor.        |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

**Example List flavor by ID: JSON request**

The following example shows the List flavor by ID request:

.. code::

   GET /v1.0/1234/flavors/1 HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

Response
--------

**Example List flavor by ID: JSON response**


The following example shows the List flavor by ID response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: 206
   Date: Thu, 13 Feb 2014 21:47:13 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

   {
       "flavor": {
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
       }
   }
