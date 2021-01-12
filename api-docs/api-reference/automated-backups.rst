.. _scheduled-backup-operations:

=================
Scheduled backups
=================

This section describes the following API operations for scheduled backups of
database instances.

.. contents::
   :local:
   :depth: 1

.. note::

  Scheduled backups are not available in the SYD and HKG regions.

Cloud Databases allows you to create a schedule for running a weekly
backup for your database instance. There is an incremental backup run at
the end of every day and a full backup is run on the day as defined by
the backup schedule. The backup can always be restored to a new database
instance. For details, see :ref:`post-restore-backup-version-accountid-instances`.

All backups will be stored in Cloud Files and will be charged a fee for
Cloud Files.

..  note::

  Any user calling the scheduled backup operations for Cloud DB will need
  access to Cloud Files.

Supported datastore versions for Scheduled Backups are MySQL 5.6, Percona 5.6, and MariaDB 10.

The Scheduled backups API supports the following operations:

.. include:: methods/post-create-scheduled-backup-version-accountid-schedules.rst
.. include:: methods/get-list-scheduled-backups-version-accountid-schedules.rst
.. include:: methods/get-list-schedule-for-running-backup-by-schedule-id-version-accountid-schedules-scheduleid.rst
.. include:: methods/put-update-schedule-for-backups-by-schedule-id-version-accountid-schedules-scheduleid.rst
.. include:: methods/delete-delete-schedule-for-running-backup-by-schedule-id-version-accountid-schedules-scheduleid.rst
