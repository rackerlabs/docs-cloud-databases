.. _high-availability-operations:

=================
High availability
=================

Refer to the list of limitations for HA at
:ref:`cdb-dg-generalapi-high-availability`.

Supported datastore versions for HA are MySQL 5.7, MySQL 8.0, Percona 5.7,
MariaDB 10.4, and MariaDB 10.4enc.

For information about HA Instance Backups, see the following:

-  To create an HA instance backup, see
   :ref:`post-create-backup-for-an-ha-instance-version-accountid-backups`.

-  To get the details of a specified backup, see
   :ref:`get-list-backup-by-id-version-accountid-backups-backupid`.

-  To list all available backups (HA/non HA), see
   :ref:`get-list-backups-version-accountid-backups`.

-  To list backups for a specified HA instance only, see
   :ref:`get-list-backups-of-an-ha-instance-version-accountid-ha-haid-backups`.

-  To delete a specified backup, see 
   :ref:`delete-delete-backup-version-accountid-backups-backupid`.

.. note::

   To create an HA instance from an existing replication setup, see
   :ref:`post-convert-replication-setup-to-ha-version-accountid-instances`.

This section describes the following API operations that are supported for
High Availability (HA) for Cloud Databases.

.. contents::
   :local:
   :depth: 1

.. include:: methods/post-create-ha-database-instance-version-accountid-ha.rst
.. include:: methods/get-list-all-ha-database-instances-version-accountid-ha.rst
.. include:: methods/get-list-ha-database-instance-details-version-accountid-ha-haid.rst
.. include:: methods/delete-delete-ha-database-instance-version-accountid-ha-haid.rst
.. include:: methods/post-add-acls-to-an-ha-instance-version-accountid-ha-haid-acls.rst
.. include:: methods/get-list-acls-for-an-ha-instance-version-accountid-ha-haid-acls.rst
.. include:: methods/delete-delete-acls-from-an-ha-instance-version-accountid-ha-haid-acls-address.rst
.. include:: methods/post-add-replica-to-an-ha-instance-version-accountid-ha-haid-action.rst
.. include:: methods/post-remove-replica-from-an-ha-instance-version-accountid-ha-haid-action.rst
.. include:: methods/post-resize-volume-for-an-ha-instance-version-accountid-ha-haid-action.rst
.. include:: methods/post-resize-flavor-for-an-ha-instance-version-accountid-ha-haid-action.rst
.. include:: methods/post-restart-ha-instance-version-accountid-ha-haid-action.rst
.. include:: methods/patch-attach-configuration-group-to-ha-instance-version-accountid-ha-haid.rst
.. include:: methods/patch-remove-configuration-group-from-ha-instance-version-accountid-ha-haid.rst
.. include:: methods/post-upgrade-ha-instance-version-accountid-ha-haid-action.rst
