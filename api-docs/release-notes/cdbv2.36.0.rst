.. version-2.36.0-release-notes:

v2.36.0, October 14, 2015
-------------------------

What's new
~~~~~~~~~~

-  Scheduled Backup Fixes:

   -  When a replication setup is converted to high availability (HA), the
      automated backup schedule for the replication is converted as well.

-  HA MySQL Fixes:

   -  Added checks for HA group actions.

Resolved issues
~~~~~~~~~~~~~~~

|no changes|

Known issues
~~~~~~~~~~~~

|no changes|

Documentation Changes
~~~~~~~~~~~~~~~~~~~~~

The :ref:`API reference <api-reference>` documentation includes the following
updates:

-  Added volume and flavor info to the List HA database instance details API
   operation.

-  Added a note about converting an automated backup schedule, if a
   source/replica has automated backups enabled, to the Convert replication
   setup to HA API operation section. The schedule is converted to an HA group
   automated backup schedule, with the source ID set to the HA ID. The day,
   hour and minute settings are the same as the source or replica schedule.

-  Added a warning about the source instance changing to the RESTART state when
   it is enabled as the master during replication setup.
