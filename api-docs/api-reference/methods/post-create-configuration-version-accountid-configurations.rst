
.. _post-create-configuration-version-accountid-configurations:

Create configuration
~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /{version}/{accountId}/configurations

Creates a new configuration group based on the parameters supplied in the
request body.

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

This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|\ **datastore**           |Object *(Optional)*      |The datastore for the    |
|                          |                         |configuration. If        |
|                          |                         |omitted, it defaults to  |
|                          |                         |MySQL 5.6.               |
+--------------------------+-------------------------+-------------------------+
|datastore.\ **type**      |String *(Optional)*      |The type of the          |
|                          |                         |datastore for the        |
|                          |                         |configuration. If        |
|                          |                         |omitted, it defaults to  |
|                          |                         |MySQL.                   |
+--------------------------+-------------------------+-------------------------+
|datastore.\ **version**   |String *(Optional)*      |The version of the       |
|                          |                         |datastore for the        |
|                          |                         |configuration. If        |
|                          |                         |omitted, it defaults to  |
|                          |                         |MySQL 5.6.               |
+--------------------------+-------------------------+-------------------------+
|\ **description**         |String *(Optional)*      |The description for the  |
|                          |                         |configuration.           |
+--------------------------+-------------------------+-------------------------+
|\ **name**                |String *(Required)*      |The name for the         |
|                          |                         |configuration.           |
+--------------------------+-------------------------+-------------------------+
|\ **values**              |Object *(Required)*      |The values for the       |
|                          |                         |configuration. The key   |
|                          |                         |value pairs "values"     |
|                          |                         |should be in JSON format |
|                          |                         |with no spaces. The key  |
|                          |                         |and the value are        |
|                          |                         |strings and must be      |
|                          |                         |enclosed in double       |
|                          |                         |quotation marks. For     |
|                          |                         |example:                 |
|                          |                         |"default_time_zone": "-  |
|                          |                         |6:00". Each key value    |
|                          |                         |pair should be separated |
|                          |                         |by a comma.              |
+--------------------------+-------------------------+-------------------------+

**Example Create configuration: JSON request**

The following example shows the Create configuration request:

.. code::

   POST /v1.0/1234/configurations HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

   {
       "configuration": {
           "datastore": {
               "type": "a00000a0-00a0-0a00-00a0-000a000000aa",
               "version": "b00000b0-00b0-0b00-00b0-000b000000bb"
           },
           "description": "example description",
           "name": "example-configuration-name",
           "values": {
               "collation_server": "latin1_swedish_ci",
               "connect_timeout": 120
           }
       }
   }

.. note::
   Each value provided for ``name`` and ``description`` must be a string
   composed of 1 to 255 alphanumeric characters. Both uppercase and lowercase
   alpha characters may be used.

Response
--------

**Example Create configuration: JSON response**

The following example shows the Create configuration response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.12)
   Content-Length: 431
   Date: Thu, 31 Jul 2014 15:07:26 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

   {
       "configuration": {
           "created": "2014-07-31T15:02:52",
           "datastore_name": "mysql",
           "datastore_version_id": "b00000b0-00b0-0b00-00b0-000b000000bb",
           "datastore_version_name": "5.6",
           "description": "example description",
           "id": "005a8bb7-a8df-40ee-b0b7-fc144641abc2",
           "instance_count": 0,
           "name": "example-configuration-name",
           "updated": "2014-07-31T15:02:52",
           "values": {
               "collation_server": "latin1_swedish_ci",
               "connect_timeout": 120
           }
       }
   }
