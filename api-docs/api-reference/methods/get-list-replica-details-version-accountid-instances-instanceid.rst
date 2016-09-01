
.. _get-list-replica-details-version-accountid-instances-instanceid:

List replica details
~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /{version}/{accountId}/instances/{instanceId}

Lists status and details for a specified replica.

This operation lists the status and details of the specified replica. The
operation also lists the configuration group id/name if the running instance
has been associated with a configuration group.

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

**Example List replica details: JSON request**

The following example shows the List replica details request:

.. code::

   GET /v1.0/1234/instances/1131f914-571c-4cd1-a5e5-0c2235eaa66f HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

Response
--------

**Example List replica details: JSON response**

The following example shows the List replica details response:

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
       "updated": "2014-10-21T19:54:55",
       "name": "t1s1_ALT_GUEST",
       "links": [
         {
           "href": " https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances /1131f914-571c-4cd1-a5e5-0c2235eaa66f",
           "rel": "self"
         },
         {
           "href": " https://ord.databases.api.rackspacecloud.com/instances /1131f914-571c-4cd1-a5e5-0c2235eaa66f",
           "rel": "bookmark"
         }
       ],
       "created": "2014-10-21T19:54:00",
       "ip": [
         "10.0.0.3"
       ],
       "id": "1131f914-571c-4cd1-a5e5-0c2235eaa66f",
       "volume": {
         "used": 0.06,
         "size": 1
       },
       "flavor": {
         "id": "9",
         "links": [
           {
             "href": " https://ord.databases.api.rackspacecloud.com/v1.0/1234/flavors /9",
             "rel": "self"
           },
           {
             "href": " https://ord.databases.api.rackspacecloud.com/flavors /9",
             "rel": "bookmark"
           }
         ]
       },
       "datastore": {
         "version": "5.6",
         "type": "mysql"
       },
       "replica_of": {
         "id": "8215d522-d66a-479b-83c0-fbacc5dd05fc",
         "links": [
           {
             "href": "https https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances /8215d522-d66a-479b-83c0-fbacc5dd05fc",
             "rel": "self"
           },
           {
             "href": " https://ord.databases.api.rackspacecloud.com/instances /8215d522-d66a-479b-83c0-fbacc5dd05fc",
             "rel": "bookmark"
           }
         ]
       }
     }
   }
