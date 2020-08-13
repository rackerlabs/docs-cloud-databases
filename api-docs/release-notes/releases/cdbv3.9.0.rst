.. version-3.9.0-release-notes:

v3.9.0, August 12, 2020
------------------------

What's new
~~~~~~~~~~

-  Encrypted backups for MariaDB 10.4enc instances.

-  MariaDB 10.1enc instances can be upgraded to a new MariaDB 10.4enc instances

-  Backups can be copied, on-demand, to other CDB regions

Resolved issues
~~~~~~~~~~~~~~~

-  Restores using a backup created for a obsolete datastore version should no longer fail.

-  Upgrades of instances that have database users specified in stored procedures should no longer fail.

-  Adding replicas for Percona 5.6 HA groups should no longer fail.

-  Resizes of instances with large and loaded root partitions should have a better chance of success

Known issues
~~~~~~~~~~~~

|no changes|
