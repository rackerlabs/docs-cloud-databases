.. _put-modify-user-attributes-version-accountid-instances-instanceid-users-name:

Modify user attributes
~~~~~~~~~~~~~~~~~~~~~~

.. code::

    PUT /{version}/{accountId}/instances/{instanceId}/users/{name}

Modifies one or more of the following for the specified user: name, password,
and host from which the user is allowed to connect to the database.

This operation modifies one or more of the following for the specified user:
user name, password, and host from which the user is allowed to connect to the
database. User in this case is user or user@host, whichever is appropriate.

Refer to
:rax-devdocs:`Create user <cloud-databases/v1/developer-guide/#create-user>`
for information about the characters that are valid for the user name and
password.

The following table lists attributes for Modify User Attributes. Note that one
or more of the attributes must be specified. Refer to the request examples for
the required json format:

.. table:: Attributes for Modify user attributes

    +------------------------------+-----------------------------------------------+
    |Name                          |Description                                    |
    +==============================+===============================================+
    |name                          |Name of the user for the database.             |
    +------------------------------+-----------------------------------------------+
    |password                      |User password for database access.             |
    +------------------------------+-----------------------------------------------+
    |host                          |Specifies the host from which a user is        |
    |                              |allowed to connect to the database. Possible   |
    |                              |values are a string containing an IPv4 address |
    |                              |or "%" to allow connecting from any host.      |
    |                              |Refer to :ref:`User access restriction by host |
    |                              |<cdb-dg-generalapi-security-restriction>`      |
    |                              |for details. If ``host`` is                    |
    |                              |not specified, it defaults to "%".             |
    +------------------------------+-----------------------------------------------+

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

This operation does not accept a request body.

**Example Modify user attributes: JSON request**

The following example shows the Modify user attributes request:

.. code::

   PUT /v1.0/1234/instances/d4603f69-ec7e-4e9b-803f-600b9205576f/users/dbuser1 HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

   {
       "user": {
           "name": "new_username",
           "password": "new_password"
       }
   }

Response
--------

**Example Modify user attributes: JSON response**

The following example shows the Modify user attributes response:

.. code::

   HTTP/1.1 202 Accepted
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: 0
   Date: Thu, 13 Feb 2014 21:47:14 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)
