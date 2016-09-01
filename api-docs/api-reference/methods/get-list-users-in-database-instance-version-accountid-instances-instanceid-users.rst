
.. _get-list-users-in-database-instance-version-accountid-instances-instanceid-users:

List users in database instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /{version}/{accountId}/instances/{instanceId}/users

Lists the users in the specified database instance.

This operation lists the users in the specified database instance, along with
the associated databases for that user.

.. note::
   This operation does not return the system users (database administrators
   that administer the health of the database). Also, this operation returns
   the "root" user only if "root" user has been enabled.

The following notes apply to database users:

*  User names can be up to 16 characters long.
*  When you create accounts with INSERT, you must use FLUSH PRIVILEGES to tell
   the server to reload the grant tables.
*  For additional information, refer to
   `http://dev.mysql.com/doc/refman/5.1/en/user-account-management.html <http://dev.mysql.com/doc/refman/5.1/en/user-account-management.html>`__

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

**Example List users in database instance: JSON request**

The following example shows the List users in database instance request:

.. code::

   GET /v1.0/1234/instances/d4603f69-ec7e-4e9b-803f-600b9205576f/users HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

**Example List users in database instance paged request: JSON**

The following example shows the paginated List users in database instance
requests to return a limit of two users at a time ( ``users?limit=2`` ).

.. code::

   GET /v1.0/1234/instances/d4603f69-ec7e-4e9b-803f-600b9205576f/users?limit=2 HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

Response
--------

**Example List users in database instance response: JSON**

The following example shows the List users in database instance response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: 322
   Date: Thu, 13 Feb 2014 21:47:14 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

   {
       "users": [
           {
               "databases": [
                   {
                       "name": "databaseA"
                   }
               ],
               "host": "%",
               "name": "dbuser1"
           },
           {
               "databases": [
                   {
                       "name": "databaseB"
                   },
                   {
                       "name": "databaseC"
                   }
               ],
               "host": "%",
               "name": "dbuser2"
           },
           {
               "databases": [
                   {
                       "name": "databaseD"
                   }
               ],
               "host": "%",
               "name": "dbuser3"
           },
           {
               "databases": [
                   {
                       "name": "sampledb"
                   }
               ],
               "host": "%",
               "name": "demouser"
           }
       ]
   }

Refer to
:ref:`User access restriction by host <cdb-dg-generalapi-security-restriction>`
for a description of the ``host`` field.

**Example List users in database instance paged response: JSON**

The following example shows the paginated List users in database instance
response.

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: 336
   Date: Thu, 13 Feb 2014 21:47:14 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

   {
       "links": [
           {
               "href": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances/d4603f69-ec7e-4e9b-803f-600b9205576f/users?marker=dbuser2%2540%2525&limit=2",
               "rel": "next"
           }
       ],
       "users": [
           {
               "databases": [
                   {
                       "name": "databaseA"
                   }
               ],
               "host": "%",
               "name": "dbuser1"
           },
           {
               "databases": [
                   {
                       "name": "databaseB"
                   },
                   {
                       "name": "databaseC"
                   }
               ],
               "host": "%",
               "name": "dbuser2"
           }
       ]
   }

Note that the response contains the link ( ``href`` ) to the next set of users
in the list ( ``users?marker=dbuser2%4010.0.0.1 & limit=2`` ), so using that
link for the request will return the next two users in the list after
``dbuser2%4010.0.0.1``.
