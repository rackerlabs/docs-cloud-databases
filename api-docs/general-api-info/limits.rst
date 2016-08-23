.. _cdb-dg-generalapi-limits:

======
Limits
======

All accounts, by default, have a preconfigured set of thresholds (or limits)
to manage capacity and prevent abuse of the system. The system recognizes two
kinds of limits: *rate limits* and *absolute limits*. Rate limits are
thresholds that are reset after a certain amount of time passes. Absolute
limits are fixed.

.. _cdb-dg-generalapi-limits-rate:

Rate limits
~~~~~~~~~~~

The following table specifies the default rate limits for all Rackspace Cloud
Databases API operations:

+---------------------------------+----------------------------------------------------------------------+------------+
|          API Operation          |                              API Action                              | Rate Limit |
+=================================+======================================================================+============+
| List Versions                   | GET /                                                                | 100/minute |
+---------------------------------+----------------------------------------------------------------------+------------+
| List Version Details            | GET /{version}                                                       | 100/minute |
+---------------------------------+----------------------------------------------------------------------+------------+
| Create Database Instance        | POST /instances                                                      | 20/minute  |
+---------------------------------+----------------------------------------------------------------------+------------+
| List All Database Instances     | GET /instances                                                       | 100/minute |
+---------------------------------+----------------------------------------------------------------------+------------+
| List Database Instance          | GET /instances/{instanceId}                                          | 100/minute |
| Status and Details              |                                                                      |            |
+---------------------------------+----------------------------------------------------------------------+------------+
| Delete Database Instance        | DELETE /instances/{instanceId}                                       | 20/minute  |
+---------------------------------+----------------------------------------------------------------------+------------+
| Enable Root User                | POST /instances/{instanceId}/root                                    | 20/minute  |
+---------------------------------+----------------------------------------------------------------------+------------+
| List Root-Enabled Status        | GET /instances/{instanceId}/root                                     | 100/minute |
+---------------------------------+----------------------------------------------------------------------+------------+
| Restart Instance                | POST /instances/{instanceId}/action                                  | 5/minute   |
+---------------------------------+----------------------------------------------------------------------+------------+
| Resize the Instance             | POST /instances/{instanceId}/action                                  | 5/minute   |
+---------------------------------+----------------------------------------------------------------------+------------+
| Resize the Instance Volume      | POST /instances/{instanceId}/action                                  | 5/minute   |
+---------------------------------+----------------------------------------------------------------------+------------+
| Create Database                 | POST /instances/{instanceId}/databases                               | 20/minute  |
+---------------------------------+----------------------------------------------------------------------+------------+
| List Databases                  | GET /instances/{instanceId}/databases                                | 100/minute |
| for an Instance                 |                                                                      |            |
+---------------------------------+----------------------------------------------------------------------+------------+
| Delete Database                 | DELETE /instances/{instanceId}/databases/{databaseName}              | 20/minute  |
+---------------------------------+----------------------------------------------------------------------+------------+
| Create User                     | POST /instances/{instanceId}/users                                   | 50/minute  |
+---------------------------------+----------------------------------------------------------------------+------------+
| List Users in Database Instance | GET /instances/{instanceId}/users                                    | 100/minute |
+---------------------------------+----------------------------------------------------------------------+------------+
| Change User Password            | PUT /instances/{instanceId}/users                                    | 50/minute  |
+---------------------------------+----------------------------------------------------------------------+------------+
| Modify User Attributes          | PUT /instances/{instance\_Id}/users/{userid}                         | 50/minute  |
+---------------------------------+----------------------------------------------------------------------+------------+
| List User                       | GET /instances/{instanceId}/users/{name}                             | 100/minute |
+---------------------------------+----------------------------------------------------------------------+------------+
| Delete User                     | DELETE /instances/{instanceId}/users/{name}                          | 50/minute  |
+---------------------------------+----------------------------------------------------------------------+------------+
| List User Access                | GET /instances/{instanceId}/users/{name}/databases                   | 100/minute |
+---------------------------------+----------------------------------------------------------------------+------------+
| Grant User Access               | PUT /instances/{instanceId}/users/{name}/databases                   | 50/minute  |
+---------------------------------+----------------------------------------------------------------------+------------+
| Revoke User Access              | DELETE /instances/{instanceId}/users/{name}/databases/{databaseName} | 50/minute  |
+---------------------------------+----------------------------------------------------------------------+------------+
| List Flavors                    | GET /flavors                                                         | 100/minute |
+---------------------------------+----------------------------------------------------------------------+------------+
| List Flavors by ID              | GET /flavors/{flavorId}                                              | 100/minute |
+---------------------------------+----------------------------------------------------------------------+------------+
| Create Backup                   | POST /backups                                                        | 100/minute |
+---------------------------------+----------------------------------------------------------------------+------------+
| List Backups                    | GET /backups                                                         | 100/minute |
+---------------------------------+----------------------------------------------------------------------+------------+
| List Backup by ID               | GET /backups/{backupId}                                              | 100/minute |
+---------------------------------+----------------------------------------------------------------------+------------+
| Delete Backup                   | DELETE /backups/{backupId}                                           | 20/minute  |
+---------------------------------+----------------------------------------------------------------------+------------+
| List Backups for Instance       | GET /instances/{instanceId}/backups                                  | 100/minute |
+---------------------------------+----------------------------------------------------------------------+------------+
| Restore Backup                  | POST /instances                                                      | 20/minute  |
| (same as create instance)       |                                                                      |            |
+---------------------------------+----------------------------------------------------------------------+------------+

If you exceed the thresholds established for your account, a 413 (rate Control)
HTTP response will be returned with a ``Retry-After`` header to notify the
client when it can attempt to try again.

.. _cdb-dg-generalapi-limits-absolute:

Absolute limits
~~~~~~~~~~~~~~~

Refer to the following table for the absolute limits that are set.

+----------------+--------------------------------------------------------------------------+-------+
|    Name        |                             Description                                  | Limit |
+================+==========================================================================+=======+
| Instances      | Maximum number of instances allowed for your account                     |    25 |
+----------------+--------------------------------------------------------------------------+-------+
| Volume Size    | Maximum volume size per instance in gigabytes (GB) for your account      |  1024 |
+----------------+--------------------------------------------------------------------------+-------+
