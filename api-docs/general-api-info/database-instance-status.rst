.. _cdb-dg-generalapi-dbinstance:

========================
Database instance status
========================

When you submit an API request to create, list, or delete database instances,
the response returns the current status information for each instance.

following table lists the status values that can be included in the response.

.. csv-table:: Database instance status values
  :widths: 25 75
  :header-rows: 1

  "Status", "Description"
  "``ACTIVE``", "The database instance is online and available to take
  requests."
  "``BACKUP``", "The database instance is currently running a backup process."
  "``BLOCKED``", "The database instance is currently unresponsive."
  "``BUILD``", "The database instance is being provisioned."
  "``CONVERT_TO_HA``", "The database instance is being configured for HA
  conversion."
  "``DELETION_PENDING``", "The database instance is scheduled for deletion."
  "``DETACH_REPLICA``", "The database instance, which was a replica, is being
  detached from the source."
  "``ERROR``", "The last operation for the database instance failed due to an
  error."
  "``FAILED``", "The database instance was created, but failed to set up the
  datastore. If a database instance is in the FAILED state, you should delete
  it and create a new instance."
  "``REBOOT``", "The database instance is rebooting."
  "``REPLICATION_ERROR``", "Replication is broken on the database instance."
  "``RESIZE``", "The database instance is currently being resized."
  "``RESTART_REQUIRED``", "A change has occurred to the configuration of an
  instance that requires the instance to be restarted at the user’s
  convenience."
  "``RESTART``", "The MySQL service for the database instance is restarting."
  "``SHUTDOWN``", "The database instance is terminating services. This status
  can also be returned if the server is running, but the database instance is
  shut down."

.. note::

   The status values are different for a database instance included in a high
   availability instance group. For details, see :ref:`Database instance
   status values for high availability configurations <ha-dbinstance-status>`.
