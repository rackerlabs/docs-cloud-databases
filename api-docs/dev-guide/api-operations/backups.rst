.. _on-demand-backup-operations:

On demand backups
~~~~~~~~~~~~~~~~~~

.. contents::
   :depth: 1
   :local:



This section describes the operations for backups of database instances.

..  note:: 

  Any user calling the backup operations for Cloud DB will need access to
  Cloud Files.

The following table lists the possible statuses returned by the Backup
API:

Table. Backup statuses

+----------------+-------------------------------------------------------+
| Status         | Description                                           |
+================+=======================================================+
| NEW            | A new backup task was created.                        |
+----------------+-------------------------------------------------------+
| BUILDING       | The backup task is currently running.                 |
+----------------+-------------------------------------------------------+
| COMPLETED      | The backup task was successfully completed.           |
+----------------+-------------------------------------------------------+
| FAILED         | The backup task failed to complete successfully.      |
+----------------+-------------------------------------------------------+
| DELETE_FAILED  | The backup task failed to delete Cloud Files objects. |
+----------------+-------------------------------------------------------+


The Backup API supports the following operations:


.. include:: methods/post-create-backup-version-accountid-backups.rst
.. include:: methods/post-create-backup-for-an-ha-instance-version-accountid-backups.rst
.. include:: methods/get-list-backups-version-accountid-backups.rst
.. include:: methods/get-list-backup-by-id-version-accountid-backups-backupid.rst
.. include:: methods/delete-delete-backup-version-accountid-backups-backupid.rst
.. include:: methods/get-list-backups-for-instance-version-accountid-instances-instanceid-backups.rst
.. include:: methods/post-restore-backup-version-accountid-instances.rst
.. include:: methods/get-list-backups-of-an-ha-instance-version-accountid-ha-haid-backups.rst


