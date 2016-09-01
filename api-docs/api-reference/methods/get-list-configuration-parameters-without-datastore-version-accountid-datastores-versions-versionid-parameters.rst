
.. _get-list-configuration-parameters-without-datastore-version-accountid-datastores-versions-versionid-parameters:

List configuration parameters without datastore
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /{version}/{accountId}/datastores/versions/{versionId}/parameters

Lists the configuration parameters that may be configured on the system
without specifying a datastore.

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
|{versionId}               |String                   |The version for the      |
|                          |                         |specified datastore.     |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

**Example List configuration parameters without datastore: JSON request**

The following example shows the List configuration parameters without datastore
request:

.. code::

   GET /v1.0/1234/datastores/versions/b00000b0-00b0-0b00-00b0-000b000000bb/parameters HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

Response
--------

**Example List configuration parameters without datastore: JSON response**

The following example shows the List configuration parameters without datastore
response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: 3400
   Date: Thu, 13 Feb 2014 21:47:15 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

   {
       "configuration-parameters": [
           {
               "max": 1,
               "min": 0,
               "name": "innodb_file_per_table",
               "restart_required": true,
               "type": "integer"
           },
           {
               "max": 1,
               "min": 0,
               "name": "autocommit",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 1,
               "min": 0,
               "name": "local_infile",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 4294967296,
               "min": 0,
               "name": "key_buffer_size",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 65535,
               "min": 1,
               "name": "connect_timeout",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 4294967296,
               "min": 0,
               "name": "join_buffer_size",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 18446744073709547520,
               "min": 32768,
               "name": "sort_buffer_size",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 68719476736,
               "min": 0,
               "name": "innodb_buffer_pool_size",
               "restart_required": true,
               "type": "integer"
           },
           {
               "max": 2,
               "min": 0,
               "name": "innodb_flush_log_at_trx_commit",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 4294967296,
               "min": 1048576,
               "name": "innodb_log_buffer_size",
               "restart_required": true,
               "type": "integer"
           },
           {
               "max": 4294967296,
               "min": 10,
               "name": "innodb_open_files",
               "restart_required": true,
               "type": "integer"
           },
           {
               "max": 1000,
               "min": 0,
               "name": "innodb_thread_concurrency",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 18446744073709547520,
               "min": 0,
               "name": "sync_binlog",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 65535,
               "min": 1,
               "name": "auto_increment_increment",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 65535,
               "min": 1,
               "name": "auto_increment_offset",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 18446744073709547520,
               "min": 0,
               "name": "bulk_insert_buffer_size",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 65535,
               "min": 1,
               "name": "expire_logs_days",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 65535,
               "min": 1,
               "name": "interactive_timeout",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 1073741824,
               "min": 1024,
               "name": "max_allowed_packet",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 18446744073709547520,
               "min": 1,
               "name": "max_connect_errors",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 65535,
               "min": 1,
               "name": "max_connections",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 18446744073709547520,
               "min": 4,
               "name": "myisam_sort_buffer_size",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 100000,
               "min": 1,
               "name": "max_user_connections",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 100000,
               "min": 1,
               "name": "server_id",
               "restart_required": true,
               "type": "integer"
           },
           {
               "max": 31536000,
               "min": 1,
               "name": "wait_timeout",
               "restart_required": false,
               "type": "integer"
           },
           {
               "name": "character_set_client",
               "restart_required": false,
               "type": "string"
           },
           {
               "name": "character_set_connection",
               "restart_required": false,
               "type": "string"
           },
           {
               "name": "character_set_database",
               "restart_required": false,
               "type": "string"
           },
           {
               "name": "character_set_filesystem",
               "restart_required": false,
               "type": "string"
           },
           {
               "name": "character_set_results",
               "restart_required": false,
               "type": "string"
           },
           {
               "name": "character_set_server",
               "restart_required": false,
               "type": "string"
           },
           {
               "name": "collation_connection",
               "restart_required": false,
               "type": "string"
           },
           {
               "name": "collation_database",
               "restart_required": false,
               "type": "string"
           },
           {
               "name": "collation_server",
               "restart_required": false,
               "type": "string"
           }
       ]
   }
