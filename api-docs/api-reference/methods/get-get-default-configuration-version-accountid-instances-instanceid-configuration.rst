
.. _get-get-default-configuration-version-accountid-instances-instanceid-configuration:

Get default configuration
~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /{version}/{accountId}/instances/{instanceId}/configuration

Lists the default configuration settings from the template that were applied to
the specified instance.

This operation lists the default configuration settings from the template that
were applied to the specified instance.

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

**Example Get default configuration: JSON request**

The following example shows the Get default configuration request:

.. code::

   GET /v1.0/1234/instances/dcc5c518-73c7-4471-83e1-15fae67a98eb/configuration HTTP/1.1
   User-Agent: python-reddwarfclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

Response
--------

**Example Get default configuration: JSON response**

The following example shows the Get default configuration response:

.. code::

   {
       "instance": {
           "configuration": {
               "basedir": "/usr",
               "connect_timeout": "15",
               "datadir": "/var/lib/mysql",
               "default_storage_engine": "innodb",
               "innodb_buffer_pool_instances": "1",
               "innodb_buffer_pool_size": "175M",
               "innodb_checksum_algorithm": "crc32",
               "innodb_data_file_path": "ibdata1:10M:autoextend",
               "innodb_file_per_table": "1",
               "innodb_io_capacity": "200",
               "innodb_io_capacity_max": "400               # 2 x innodb_io_capacity",
               "innodb_log_buffer_size": "8M",
               "innodb_log_file_size": "256M",
               "innodb_log_files_in_group": "2",
               "innodb_open_files": "8192",
               "innodb_thread_concurrency": "0",
               "join_buffer_size": "1M",
               "key_buffer_size": "50M",
               "local-infile": "0",
               "log-error": "/var/log/mysql/mysqld.log",
               "max_allowed_packet": "16M",
               "max_connect_errors": "10000",
               "max_connections": "40",
               "max_heap_table_size": "16M",
               "myisam-recover": "BACKUP",
               "open_files_limit": "8192",
               "performance_schema": "off",
               "pid_file": "/var/run/mysqld/mysqld.pid",
               "port": "3306",
               "query_cache_limit": "1M",
               "query_cache_size": "8M",
               "query_cache_type": "1",
               "read_buffer_size": "256K",
               "read_rnd_buffer_size": "1M",
               "server_id": "1",
               "skip-external-locking": "1",
               "skip_name_resolve": "1",
               "sort_buffer_size": "256K",
               "table_open_cache": "4096",
               "thread_stack": "192K",
               "tmp_table_size": "16M",
               "tmpdir": "/var/tmp",
               "user": "mysql",
               "wait_timeout": "3600"
           }
       }
   }
