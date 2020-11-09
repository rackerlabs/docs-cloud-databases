
.. _post-upgrade-ha-instance-version-accountid-ha-haid-action:

Upgrade an HA instance
~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /{version}/{accountId}/ha/{haId}/action

Upgrades an HA instance to a later datastore version, or in limited cases,
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
|202                       |Success                  |Request succeeded.       |
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

**Example Upgrade HA Instance: JSON request**

The following example shows the upgrade HA instance request:

.. code::

   POST /v1.0/1234/ha/67a59adb-d678-4092-b9a9-8cbe4ca39b4b/action HTTP/1.1
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

**Example Upgrade HA Instance: JSON response**

The following example shows the upgrade HA instance response:

.. code::

   HTTP/1.1 202 Accepted
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.12)
   Content-Length: 192
   Date: Tue, 15 Mar 2016 16:36:48 GMT
   Connection: close

   {
       "ha_instance": {
           "tenant_id": "1234",
           "state": "UPGRADING",
           "id": "67a59adb-d678-4092-b9a9-8cbe4ca39b4b",
           "datastore": {
               "version": "5.6",
               "type": "mysql"
           },
           "name": "test-upgrade-ha-mysql56"
       }
   }
