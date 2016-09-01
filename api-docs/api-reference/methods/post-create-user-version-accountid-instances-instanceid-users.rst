
.. _post-create-user-version-accountid-instances-instanceid-users:

Create user
~~~~~~~~~~~

.. code::

    POST /{version}/{accountId}/instances/{instanceId}/users

Creates a user for the specified database instance.

This operation asynchronously provisions a new user for the specified database
instance based on the configuration defined in the request object. Once the
request is validated and progress has started on the provisioning process, a
202 Accepted response object is returned.

If the corresponding request cannot be fulfilled due to insufficient or invalid
data, an HTTP 400 "Bad Request" error response is returned with information
regarding the nature of the failure. Failures in the validation process are
non-recoverable and require the caller to correct the cause of the failure and
POST the request again.

The following table lists the required and optional attributes for Create User.
Refer to the request examples for the required json format:

.. table:: Required and optional attributes for Create user

    +------------+-----------------+------------------------------------------------+----------+
    | Applies To | Name            | Description                                    | Required |
    +============+=================+================================================+==========+
    | User       | name            | Name of the user for the database.             | Yes      |
    |            +-----------------+------------------------------------------------+----------+
    |            | password        | User password for database access.             | Yes      |
    |            +-----------------+------------------------------------------------+----------+
    |            | (database) name | Name of the database that the user can access. | No       |
    |            +-----------------+------------------------------------------------+----------+
    |            | host            | Specifies the host from which a user is        | No       |
    |            |                 | allowed to connect to the database. Possible   |          |
    |            |                 | values are a string containing an IPv4         |          |
    |            |                 | address or "%" to allow connecting from any    |          |
    |            |                 | host. Refer to :ref:`User access restriction by|          |
    |            |                 | host <cdb-dg-generalapi-security-restriction>` |          |
    |            |                 | for details. If ``host`` is not specified, it  |          |
    |            |                 | defaults to "%".                               |          |
    +------------+-----------------+------------------------------------------------+----------+


.. note::

   *  A user is granted all privileges on the specified databases.
   *  The following user name is reserved and cannot be used for creating
      users: root.

Refer to the following tables for information about characters that are
valid/invalid for creating database names, user names, and passwords.

.. table:: Valid characters that can be used in a database name, user name, and password

    +------------------------------------------------------------------------------+
    |Character                                                                     |
    +==============================================================================+
    |Letters (upper and lower cases allowed)                                       |
    +------------------------------------------------------------------------------+
    |Numbers                                                                       |
    +------------------------------------------------------------------------------+
    |'@', '?', '#', and spaces are allowed, but not at the beginning and end of    |
    |the database name, user name, and password                                    |
    +------------------------------------------------------------------------------+
    |'.' is allowed, but must be escaped by replacing it with "%2E" before URL     |
    |encoding occurs if it occurs in GET, DELETE, and PUT calls, where such a name |
    |is the last section of the request URL. Please refer to the Warning in        |
    |:ref:`User access restriction by host                                         |
    |<cdb-dg-generalapi-security-restriction>` for details and                     |
    |an example.                                                                   |
    +------------------------------------------------------------------------------+
    |"_" is allowed anywhere in the database name, user name, and password         |
    +------------------------------------------------------------------------------+

.. table:: Length restrictions for database name, user name, and password

    +---------------------------------------+--------------------------------------+
    |Restriction                            |Value                                 |
    +=======================================+======================================+
    |Database name maximum length           |64                                    |
    +---------------------------------------+--------------------------------------+
    |User name maximum length               |16                                    |
    +---------------------------------------+--------------------------------------+
    |Password maximum length                |unlimited (no restrictions)           |
    +---------------------------------------+--------------------------------------+

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

**Example Create user: JSON request**

The following example shows the Create user request:

.. code::

   POST /v1.0/1234/instances/d4603f69-ec7e-4e9b-803f-600b9205576f/users HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

   {
       "users": [
           {
               "databases": [
                   {
                       "name": "databaseA"
                   }
               ],
               "name": "dbuser1",
               "password": "password"
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
               "name": "dbuser2",
               "password": "password"
           },
           {
               "databases": [
                   {
                       "name": "databaseD"
                   }
               ],
               "name": "dbuser3",
               "password": "password"
           }
       ]
   }

Response
--------

**Example Create user: JSON response**

The following example shows the Create user response:

.. code::

   HTTP/1.1 202 Accepted
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: 0
   Date: Thu, 13 Feb 2014 21:47:14 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

This operation does not return a response body.
