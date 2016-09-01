
.. _delete-revoke-user-access-version-accountid-instances-instanceid-users-name-databases-databasename:

Revoke user access
~~~~~~~~~~~~~~~~~~

.. code::

    DELETE /{version}/{accountId}/instances/{instanceId}/users/{name}/databases/{databaseName}

Removes access to the specified database for the specified user.

This operation removes access to the specified database for the specified user.

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

+---------------+--------------+-----------------------------------------------+
|Name           |Type          |Description                                    |
+===============+==============+===============================================+
|{accountId}    |String        |The account ID of the owner of the specified   |
|               |              |instance.                                      |
+---------------+--------------+-----------------------------------------------+
|{instanceId}   |String        |The instance ID for the specified database     |
|               |              |instance.                                      |
+---------------+--------------+-----------------------------------------------+
|{name}         |String        |The name for the specified user. Refer to      |
|               |              |:ref:`User access restriction by host          |
|               |              |<cdb-dg-generalapi-security-restriction>`      |
|               |              |for details about restricting                  |
|               |              |the name to a particular host. Examples:       |
|               |              |testuser, testuser@192.168.1.12 (to restrict   |
|               |              |the user to connecting from a particular host  |
|               |              |IP).                                           |
+---------------+--------------+-----------------------------------------------+
|{databaseName} |String        |The name for the specified database.           |
+---------------+--------------+-----------------------------------------------+

This operation does not accept a request body.

**Example Revoke user access: JSON request**

The following example shows the Revoke user access request:

.. code::

   DELETE /v1.0/1234/instances/dcc5c518-73c7-4471-83e1-15fae67a98eb/users/dbuser1/databases/databaseE HTTP/1.1
   User-Agent: python-reddwarfclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

Response
--------

**Example Revoke user access: JSON response**

The following example shows the Revoke user access response:

.. code::

   HTTP/1.1 202 Accepted
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: 0
   Date: Wed, 08 May 2013 22:43:35 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

This operation does not return a response body.
