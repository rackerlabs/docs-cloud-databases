.. version-2.36.0-release-notes:

v2.36.0, October 14, 2015
---------------------------

What's new
~~~~~~~~~~~~

-  Scheduled Backup Fixes:

   -  Convert automated backup schedule when m/s setup is converted to
      HA.

-  HA MySQL Fixes:

   -  Checks for HA group actions.
   

Resolved issues
~~~~~~~~~~~~~~~

|no changes|


Known issues
~~~~~~~~~~~~~~~~~

|no changes|


Documentation Changes
~~~~~~~~~~~~~~~~~~~~~~~

The :ref:`API reference <api-reference>` documentation includes the following updates: 

-  Added volume and flavor info to the API operation List HA database instance details.

-  Added note about converting automated backup schedule, if a source/replica has automated 
   backups enabled, to the Convert replication setup to HA API operation. In this case, 
   the schedule will be converted to an HA group automated backup schedule with the source 
   id set to the HA id. The day, hour and minute settings will be the same as the source or 
   replica schedule.

-  Source changes to RESTART state when enabling as master during replication setup.

