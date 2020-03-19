.. version-3.6.1-release-notes:

v3.6.1, March 18, 2020
------------------------

What's new
~~~~~~~~~~

|no changes|

Resolved issues
~~~~~~~~~~~~~~~

- Backups with new backup strategy, introduced in previous release, no longer fail immediately
- Backups of databases within 10% of the database volume size are no longer rejected
- Incorrect backup type is no longer reported for failed backups
- Replication status alert for Percona 5.6 replicas no longer reports missing package
- Full backups are no longer created for Incremental backups

Known issues
~~~~~~~~~~~~

|no changes|
