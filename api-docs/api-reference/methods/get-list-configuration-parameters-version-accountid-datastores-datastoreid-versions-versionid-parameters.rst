
.. _get-list-configuration-parameters-version-accountid-datastores-datastoreid-versions-versionid-parameters:

List configuration parameters
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /{version}/{accountId}/datastores/{datastoreId}/versions/{versionId}/parameters

Lists configuration parameters that may be configured on the system.

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
|{datastoreId}             |String                   |The ID for the specified |
|                          |                         |datastore.               |
+--------------------------+-------------------------+-------------------------+
|{versionId}               |String                   |The version for the      |
|                          |                         |specified datastore.     |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

**Example List configuration parameters: JSON request**

The following example shows the List configuration parameters request:

.. code::

   GET /v1.0/1234/datastores/a00000a0-00a0-0a00-00a0-000a000000aa/versions/b00000b0-00b0-0b00-00b0-000b000000bb/parameters HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

Response
--------

**Example List configuration parameters: JSON response**

The following example shows the List configuration parameters response:

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
               "max": 4294967296,
               "min": 0,
               "name": "key_buffer_size",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 65535,
               "min": 2,
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
               "name": "character_set_filesystem",
               "restart_required": false,
               "type": "string"
           },
           {
               "name": "character_set_server",
               "restart_required": false,
               "type": "string"
           },
           {
               "name": "collation_server",
               "restart_required": false,
               "type": "string"
           },
           {
               "max": 18446744073709547520,
               "min": 10,
               "name": "ft_max_word_len",
               "restart_required": true,
               "type": "integer"
           },
           {
               "max": 18446744073709547520,
               "min": 1,
               "name": "ft_min_word_len",
               "restart_required": true,
               "type": "integer"
           },
           {
               "max": 16384,
               "min": 0,
               "name": "thread_cache_size",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 18446744073709547520,
               "min": 0,
               "name": "query_cache_size",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 2,
               "min": 0,
               "name": "query_cache_type",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 524288,
               "min": 256,
               "name": "table_definition_cache",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 65535,
               "min": 0,
               "name": "open-files-limit",
               "restart_required": true,
               "type": "integer"
           },
           {
               "max": 524288,
               "min": 1,
               "name": "table_open_cache",
               "restart_required": false,
               "type": "integer"
           },
           {
               "name": "default_time_zone",
               "restart_required": true,
               "type": "string"
           },
           {
               "max": 2,
               "min": 0,
               "name": "completion_type",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 2,
               "min": 0,
               "name": "concurrent_insert",
               "restart_required": false,
               "type": "integer"
           },
           {
               "name": "default-storage-engine",
               "restart_required": false,
               "type": "string"
           },
           {
               "max": 7,
               "min": 0,
               "name": "default_week_format",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 1,
               "min": 0,
               "name": "delay_key_write",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 18446744073709547520,
               "min": 1,
               "name": "delayed_insert_limit",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 31536000,
               "min": 1,
               "name": "delayed_insert_timeout",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 18446744073709547520,
               "min": 1,
               "name": "delayed_queue_size",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 30,
               "min": 0,
               "name": "div_precision_increment",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 1,
               "min": 0,
               "name": "event_scheduler",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 1,
               "min": 0,
               "name": "flush",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 31536000,
               "min": 0,
               "name": "flush_time",
               "restart_required": false,
               "type": "integer"
           },
           {
               "name": "ft_boolean_syntax",
               "restart_required": false,
               "type": "string"
           },
           {
               "max": 1000,
               "min": 0,
               "name": "ft_query_expansion_limit",
               "restart_required": true,
               "type": "integer"
           },
           {
               "max": 1,
               "min": 0,
               "name": "general_log",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 18446744073709547520,
               "min": 4,
               "name": "group_concat_max_len",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 18446744073709547520,
               "min": 100,
               "name": "key_cache_age_threshold",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 100,
               "min": 1,
               "name": "key_cache_division_limit",
               "restart_required": false,
               "type": "integer"
           },
           {
               "name": "log_output",
               "restart_required": false,
               "type": "string"
           },
           {
               "max": 1,
               "min": 0,
               "name": "log_queries_not_using_indexes",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 1,
               "min": 0,
               "name": "log_slow_admin_statements",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 1,
               "min": 0,
               "name": "log_slow_queries",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 31536000,
               "min": 0,
               "name": "long_query_time",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 1,
               "min": 0,
               "name": "low_priority_updates",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 2,
               "min": 0,
               "name": "lower_case_table_names",
               "restart_required": true,
               "type": "integer"
           },
           {
               "max": 16384,
               "min": 0,
               "name": "max_delayed_threads",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 65535,
               "min": 0,
               "name": "max_error_count",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 1844674407370954752,
               "min": 16384,
               "name": "max_heap_table_size",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 4294967295,
               "min": 1,
               "name": "max_join_size",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 8388608,
               "min": 4,
               "name": "max_length_for_sort_data",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 1048576,
               "min": 0,
               "name": "max_prepared_stmt_count",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 18446744073709547520,
               "min": 1,
               "name": "max_seeks_for_key",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 8388608,
               "min": 4,
               "name": "max_sort_length",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 18446744073709547520,
               "min": 1,
               "name": "max_write_lock_count",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 18446744073709547520,
               "min": 0,
               "name": "min_examined_rows_limit",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 9223372036854775807,
               "min": 0,
               "name": "myisam_max_sort_file_size",
               "restart_required": false,
               "type": "integer"
           },
           {
               "name": "myisam_stats_method",
               "restart_required": false,
               "type": "string"
           },
           {
               "max": 31536000,
               "min": 1,
               "name": "net_read_timeout",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 18446744073709547520,
               "min": 1,
               "name": "net_retry_count",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 31536000,
               "min": 1,
               "name": "net_write_timeout",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 1,
               "min": 0,
               "name": "old_alter_table",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 1,
               "min": 0,
               "name": "old_style_user_limits",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 1,
               "min": 0,
               "name": "old_passwords",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 1,
               "min": 0,
               "name": "optimizer_prune_level",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 62,
               "min": 0,
               "name": "optimizer_search_depth",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 1073741824,
               "min": 1024,
               "name": "preload_buffer_size",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 18446744073709547520,
               "min": 0,
               "name": "query_cache_limit",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 1,
               "min": 0,
               "name": "query_cache_wlock_invalidate",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 18446744073709547520,
               "min": 8192,
               "name": "query_prealloc_size",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 18446744073709547520,
               "min": 4096,
               "name": "range_alloc_block_size",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 2147479552,
               "min": 8200,
               "name": "read_buffer_size",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 2147483647,
               "min": 8200,
               "name": "read_rnd_buffer_size",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 1,
               "min": 0,
               "name": "secure_auth",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 31536000,
               "min": 0,
               "name": "slow_launch_time",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 1,
               "min": 0,
               "name": "slow_query_log",
               "restart_required": false,
               "type": "integer"
           },
           {
               "name": "sql_mode",
               "restart_required": false,
               "type": "string"
           },
           {
               "max": 1,
               "min": 0,
               "name": "sync_frm",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 18446744073709547520,
               "min": 131072,
               "name": "thread_stack",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 18446744073709551615,
               "min": 1024,
               "name": "tmp_table_size",
               "restart_required": false,
               "type": "integer"
           },
           {
               "name": "transaction-isolation",
               "restart_required": true,
               "type": "string"
           },
           {
               "max": 1,
               "min": 0,
               "name": "updatable_views_with_limit",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 1,
               "min": 0,
               "name": "innodb_adaptive_hash_index",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 2,
               "min": 0,
               "name": "innodb_autoinc_lock_mode",
               "restart_required": true,
               "type": "integer"
           },
           {
               "max": 1000,
               "min": 0,
               "name": "innodb_commit_concurrency",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 4294967295,
               "min": 1,
               "name": "innodb_concurrency_tickets",
               "restart_required": false,
               "type": "integer"
           },
           {
               "name": "innodb_file_format",
               "restart_required": false,
               "type": "string"
           },
           {
               "max": 1073741824,
               "min": 1,
               "name": "innodb_lock_wait_timeout",
               "restart_required": true,
               "type": "integer"
           },
           {
               "max": 1,
               "min": 0,
               "name": "innodb_locks_unsafe_for_binlog",
               "restart_required": true,
               "type": "integer"
           },
           {
               "max": 100,
               "min": 0,
               "name": "innodb_max_dirty_pages_pct",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 4294967295,
               "min": 0,
               "name": "innodb_max_purge_lag",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 95,
               "min": 5,
               "name": "innodb_old_blocks_pct",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 4294967295,
               "min": 0,
               "name": "innodb_old_blocks_time",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 1,
               "min": 0,
               "name": "innodb_rollback_on_timeout",
               "restart_required": true,
               "type": "integer"
           },
           {
               "name": "innodb_stats_method",
               "restart_required": false,
               "type": "string"
           },
           {
               "max": 1,
               "min": 0,
               "name": "innodb_stats_on_metadata",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 18446744073709551615,
               "min": 1,
               "name": "innodb_stats_sample_pages",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 1,
               "min": 0,
               "name": "innodb_strict_mode",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 4294967295,
               "min": 0,
               "name": "innodb_sync_spin_loops",
               "restart_required": false,
               "type": "integer"
           },
           {
               "max": 18446744073709551615,
               "min": 1,
               "name": "innodb_thread_sleep_delay",
               "restart_required": false,
               "type": "integer"
           }
       ]
   }
