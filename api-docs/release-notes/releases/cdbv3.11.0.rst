.. version-3.11.0-release-notes:

v3.11.0, February 2, 2021
-------------------------

What's new
~~~~~~~~~~

-  Backup ID can be specified when creating a replica of a single instance.

Resolved issues
~~~~~~~~~~~~~~~

-  HA upgrades should no longer fail for MariaDB 10/10.1 HA groups.

-  Replica monitoring for Percona 5.7 should no longer report an issue with
   **libmysqlclient_r**.

-  Failures during resize should result in the instance going into ERROR
   state instead of staying in RESIZING state.

-  Backups should no longer go into COPY_ERROR state when the backup copy
   operation fails.

-  Creation date will no longer be set to None if build retries occur.

-  Redis backups should now work.

Known issues
~~~~~~~~~~~~

|no changes|
