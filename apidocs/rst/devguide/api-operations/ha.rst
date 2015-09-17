.. _high-availability-operations:

High availability
~~~~~~~~~~~~~~~~~~~~

.. contents::
   :depth: 1
   :local:


Refer to the list of limitations for HA at `Section 3.18, “High
Availability for Cloud Databases” <High-Availability-dle2648.html>`__.

For information about HA Instance Backups, see the following:

-  To create an HA instance backup, see `Create backup of an HA
   Instance <http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/POST_createBackupForHaInstance__version___accountId__backups_backups.html>`__.

-  To get the details of a specified backup, see `List backup by
   ID <http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/GET_getBackupById__version___accountId__backups__backupId__backups.html>`__.

-  To list all available backups (HA/non HA), see `List
   backups <http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/GET_getBackups__version___accountId__backups_backups.html>`__.

-  To list backups for a specified HA instance only, see `List backups
   of an HA
   instance <http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/GET_getBackupsForHaInstance__version___accountId__ha__haId__backups_backups.html>`__.

-  To delete a specified backup, see \ `Delete
   backup <file:///Users/mike.asthalter/Documents/DBaaS/docs-cloud-databases/apidocs/target/docbkx/webhelp/cdb-devguide-external/content/DELETE_deleteBackup__version___accountId__backups__backupId__backups.html>`__.


This section describes the operations that are supported for High Availability (HA)
for Cloud Databases.

.. include:: methods/post-create-ha-database-instance-version-accountid-ha.rst
.. include:: methods/get-list-all-ha-database-instances-version-accountid-ha.rst
.. include:: methods/get-list-ha-database-instance-details-version-accountid-ha-haid.rst
.. include:: methods/delete-delete-ha-database-instance-version-accountid-ha-haid.rst
.. include:: methods/post-add-acls-to-an-ha-instance-version-accountid-ha-haid-acls.rst
.. include:: methods/get-list-acls-for-an-ha-instance-version-accountid-ha-haid-acls.rst
.. include:: methods/delete-delete-acls-from-an-ha-instance-version-accountid-ha-haid-acls-address.rst
.. include:: methods/post-add-replica-to-an-ha-instance-version-accountid-ha-haid-action.rst
.. include:: methods/post-remove-replica-from-an-ha-instance-version-accountid-ha-haid-action.rst



