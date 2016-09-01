
.. _delete-delete-acls-from-an-ha-instance-version-accountid-ha-haid-acls-address:

Delete ACLs from an HA instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    DELETE /{version}/{accountId}/ha/{haId}/acls/{address}

Deletes ACLs from an HA instance.

This operation deletes ACLs from an HA instance.

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
|{haId}                    |String                   |The ID for the specified |
|                          |                         |HA instance.             |
+--------------------------+-------------------------+-------------------------+
|{address}                 |String                   |The CIDR notated IPV4    |
|                          |                         |address. The IPV4        |
|                          |                         |address to use should be |
|                          |                         |CIDR notated.            |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

**Example Delete ACLs from an HA instance: JSON request**

The following example shows the Delete ACLs from an HA instance request:

.. code::

   DELETE /v1.0/1234/ha/e7fdf90b-7140-4edb-b449-e093d55008fb/acls/1.2.3.4%25252F32 HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: f47d99adabe14bc8bd7bccda88292918
   Accept: application/json
   Content-Type: application/json

.. note::
   Note that the string "%25252F" near the end of the IP address in the request
   refers to the special character for the forward slash ('/') that is used
   with the IP address in CIDR format ("1.2.3.4/32").

Response
--------

**Example Delete ACLs from an HA instance: JSON response**

The following example shows the Delete ACLs from an HA instance response:

.. code::

   HTTP/1.1 202 Accepted
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.12)
   Content-Length: 0
   Date: Fri, 08 May 2015 19:36:28 GMT
   Connection: close
   Server: Jetty(8.0.y.z-SNAPSHOT)
