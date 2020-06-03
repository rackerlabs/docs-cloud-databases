
.. _post-upgrade-version-accountid-instances-instanceid-action:

Upgrade an instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /{version}/{accountId}/instances/{instanceId}/action

Upgrades a single instance to a later datastore version, or in limited cases,
to a different datastore type.

You can make the following upgrades:

-  MySQL 5.1 to MySQL 5.7

-  MySQL 5.6 to MySQL 5.7 and MariaDB 10.4enc

-  MariaDB 10/10.1 to MariaDB 10.4

-  MariaDB 10.4  to MariaDB 10.4enc

This operation returns a 202 Accepted response.

This table shows the possible response codes for this operation:

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
|415                       |badMediaType             |The entity of the        |
|                          |                         |request is in a format   |
|                          |                         |not supported by the     |
|                          |                         |requested resource for   |
|                          |                         |the requested method.    |
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

**Example Upgrade instance: JSON request**

The following example shows the Upgrade instance request:

.. code::

   POST /v1.0/1234/instances/d4603f69-ec7e-4e9b-803f-600b9205576f/action HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

   {
       "upgrade": {
           "datastore_type": "mysql",
           "datastore_version": "5.7"
       }
   }

Response
--------

**Example Upgrade instance: JSON response**

The following example shows the Upgrade instance response:

.. code::

   HTTP/1.1 202 Accepted
   Content-Type: application/json
   Via: 1.1 Repose (Repose/8.5.0.1)
   Content-Length: 1292
   Date: Thu, 13 Feb 2014 21:47:18 GMT

   {
       "instance": {
           "status": "BUILD",
           "available_upgrades": {
               "current_version": "UNKNOWN",
               "upgrades": []
           },
           "updated": "2020-04-16T19:38:54Z",
           "name": "kea-mysql56_upgrade",
           "links": [
               {
                   "href": "https://dev.databases.api.rackspacecloud.com/v1.0/5821443/instances/daa7586a-e5bf-4028-86a5-055569ab5996",
                   "rel": "self"
               },
               {
                   "href": "https://dev.databases.api.rackspacecloud.com/instances/daa7586a-e5bf-4028-86a5-055569ab5996",
                   "rel": "bookmark"
               }
           ],
           "schedule": {
               "enabled": false
           },
           "hostname": "5a72baf219d347257bba56ec4fe09c14ff25b8b4.staging.rackspaceclouddb.com",
           "created": "2020-04-16T19:38:54Z",
           "volume": {
               "size": 1
           },
           "replica_of": {
               "id": "aa961d20-8ecf-4fb5-b2ce-ec0c539f4563",
               "links": [
                   {
                       "href": "https://dev.databases.api.rackspacecloud.com/v1.0/5821443/instances/aa961d20-8ecf-4fb5-b2ce-ec0c539f4563",
                       "rel": "self"
                   },
                   {
                       "href": "https://dev.databases.api.rackspacecloud.com/instances/aa961d20-8ecf-4fb5-b2ce-ec0c539f4563",
                       "rel": "bookmark"
                   }
               ]
           },
           "flavor": {
               "ram": 2048,
               "id": "3",
               "links": [
                   {
                       "href": "https://dev.databases.api.rackspacecloud.com/v1.0/5821443/flavors/3",
                       "rel": "self"
                   },
                   {
                       "href": "https://dev.databases.api.rackspacecloud.com/flavors/3",
                       "rel": "bookmark"
                   }
               ],
               "name": "2GB Instance"
           },
           "id": "daa7586a-e5bf-4028-86a5-055569ab5996",
           "datastore": {
               "version": "5.7",
               "type": "mysql"
           }
       }
   }
