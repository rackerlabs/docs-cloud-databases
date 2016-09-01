
.. _get-list-verbose-default-configuration-parameters-version-accountid-datastore-version-versionid-configuration-flavorid:

List verbose default configuration parameters
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /{version}/{accountId}/datastore/version/{versionId}/configuration/{flavorId}

Lists the default configuration parameters for a datastore version flavor.

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
|{flavorId}                |String                   |The flavor ID for the    |
|                          |                         |specified flavor.        |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

**Example List verbose default configuration parameters: JSON request**

The following example shows the List verbose default configuration parameters
request:

.. code::

   GET /v1.0/1234/datastore/version/c11500fb-a034-4116-9f6b-4e0b32cea39d/configuration/9 HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

Response
--------

**Example List verbose default configuration parameters: JSON response**

The following example shows the List verbose default configuration parameters
response:

.. code::

   {
      "datastore":"mysql",
      "datastore_version":"5.6",
      "flavor":9,
      "configuration":{
         "tmp_table_size":{
            "default":"16M",
            "max":18446744073709551615,
            "restart_required":false,
            "type":"integer",
            "min":1024
         },
         "innodb_log_files_in_group":{
            "default":"2"
         },
         "join_buffer_size":{
            "default":"1M",
            "max":4294967296,
            "restart_required":false,
            "type":"integer",
            "min":0
         },
         "skip-external-locking":{
            "default":"1"
         },
         "innodb_checksum_algorithm":{
            "default":"crc32"
         },
         "read_rnd_buffer_size":{
            "default":"1M",
            "max":2147483647,
            "restart_required":false,
            "type":"integer",
            "min":8200
         },
         "skip_name_resolve":{
            "default":"1"
         },
         "max_heap_table_size":{
            "default":"16M",
            "max":1844674407370954752,
            "restart_required":false,
            "type":"integer",
            "min":16384
         },
         "port":{
            "default":"3306"
         },
         "tmpdir":{
            "default":"/var/tmp"
         },
         "pid_file":{
            "default":"/var/run/mysqld/mysqld.pid"
         },
         "myisam-recover":{
            "default":"BACKUP"
         },
         "server_id":{
            "default":"559004"
         },
         "innodb_buffer_pool_size":{
            "default":"175M",
            "max":68719476736,
            "restart_required":true,
            "type":"integer",
            "min":0
         },
         "basedir":{
            "default":"/usr"
         },
         "max_allowed_packet":{
            "default":"16M",
            "max":1073741824,
            "restart_required":false,
            "type":"integer",
            "min":1024
         },
         "datadir":{
            "default":"/var/lib/mysql"
         },
         "innodb_log_buffer_size":{
            "default":"8M",
            "max":4294967296,
            "restart_required":true,
            "type":"integer",
            "min":1048576
         },
         "max_connections":{
            "default":"40",
            "max":65535,
            "restart_required":false,
            "type":"integer",
            "min":1
         },
         "table_open_cache":{
            "default":"4096",
            "max":524288,
            "restart_required":false,
            "type":"integer",
            "min":1
         },
         "connect_timeout":{
            "default":"15",
            "max":65535,
            "restart_required":false,
            "type":"integer",
            "min":2
         },
         "query_cache_type":{
            "default":"1",
            "max":2,
            "restart_required":false,
            "type":"integer",
            "min":0
         },
         "max_connect_errors":{
            "default":"10000",
            "max":18446744073709547520,
            "restart_required":false,
            "type":"integer",
            "min":1
         },
         "local-infile":{
            "default":"0"
         },
         "innodb_log_file_size":{
            "default":"256M"
         },
         "innodb_thread_concurrency":{
            "default":"0",
            "max":1000,
            "restart_required":false,
            "type":"integer",
            "min":0
         },
         "thread_stack":{
            "default":"192K",
            "max":18446744073709547520,
            "restart_required":false,
            "type":"integer",
            "min":131072
         },
         "query_cache_limit":{
            "default":"1M",
            "max":18446744073709547520,
            "restart_required":false,
            "type":"integer",
            "min":0
         },
         "wait_timeout":{
            "default":"3600",
            "max":31536000,
            "restart_required":false,
            "type":"integer",
            "min":1
         },
         "user":{
            "default":"mysql"
         },
         "query_cache_size":{
            "default":"8M",
            "max":18446744073709547520,
            "restart_required":false,
            "type":"integer",
            "min":0
         },
         "innodb_data_file_path":{
            "default":"ibdata1:10M:autoextend"
         },
         "performance_schema":{
            "default":"off"
         },
         "default_storage_engine":{
            "default":"innodb"
         },
         "log-error":{
            "default":"/var/log/mysql/mysqld.log"
         },
         "sort_buffer_size":{
            "default":"256K",
            "max":18446744073709547520,
            "restart_required":false,
            "type":"integer",
            "min":32768
         },
         "innodb_buffer_pool_instances":{
            "default":"1"
         },
         "read_buffer_size":{
            "default":"256K",
            "max":2147479552,
            "restart_required":false,
            "type":"integer",
            "min":8200
         },
         "open_files_limit":{
            "default":"8192"
         },
         "innodb_io_capacity":{
            "default":"200"
         },
         "innodb_file_per_table":{
            "default":"1",
            "max":1,
            "restart_required":true,
            "type":"integer",
            "min":0
         },
         "innodb_open_files":{
            "default":"8192",
            "max":4294967296,
            "restart_required":true,
            "type":"integer",
            "min":10
         },
         "key_buffer_size":{
            "default":"50M",
            "max":4294967296,
            "restart_required":false,
            "type":"integer",
            "min":0
         },
         "innodb_io_capacity_max":{
            "default":"400               # 2 x innodb_io_capacity"
         }
      }
   }
