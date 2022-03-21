.. version-3.16.0-release-notes:

v3.16.0, March 16, 2022
-------------------------

What's new
~~~~~~~~~~

-  Eliminated downtime during backup phase of upgrades for single instances and
   HA groups.

Resolved issues
~~~~~~~~~~~~~~~

-  MySQL connector drivers, like Google Data Studio, should no longer fail
   trying to connect to MariaDB 10.4/10.4enc databases.

-  Disk resizes for large volumes should no longer timeout after 2 minutes

-  Upgrade of single instance should no longer fail if instance to be upgraded
   has replication configuration that was not cleaned up upon detach

-  Upgraded replicas will now have appropriate RAM and volume for the new
   datastore version

Known issues
~~~~~~~~~~~~

|no changes|
