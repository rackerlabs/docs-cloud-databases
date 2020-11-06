.. version-3.10.0-release-notes:

v3.10.0, October 27, 2020
-------------------------

What's new
~~~~~~~~~~

-  Upgrading a single instance puts both the instance and its upgraded
   replica into a VERIFY_UPGRADE state.

   **Note:** Both the instance and upgraded replica remain in this state
   until the upgraded replica is detached from the instance.

   This keeps the data current in the upgraded replica while the
   customer validates that their application doesn't have any issues with the
   upgraded replica and plans a maintenance to disconnect their application from
   the instance and connect to the upgraded replica.

-  You can set up scheduled backups to take a full backup every day instead of
   taking a full backup one day a week and incrementals on the other days.

-  On-demand upgrade of HA groups:

   -  You can upgrade HA MySQL 5.1/5.6 to MySQL 5.7.
   -  You can upgrade HA MariaDB 10/10.1 to MariaDB 10.4.
   -  You can upgrade HA MariaDB 10.4 to MariaDB 10.4enc.

-  General availability of backup copy functionality for on-demand and scheduled
   backups.

Resolved issues
~~~~~~~~~~~~~~~

-  Request for an on-demand upgrade of single instance is rejected if the
   instance is a source to or a replica of another instance.

-  The final state for a revived instance is ACTIVE instead of REVIVED.

Known issues
~~~~~~~~~~~~

|no changes|
