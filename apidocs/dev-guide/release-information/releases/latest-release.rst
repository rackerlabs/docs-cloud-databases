.. latest-release-notes:

.. Template instructions - Specify version number and date in the title. If no version 
   number, use v"current-version", date.
   

|release|.36.0 October 14, 2015
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Software releases introduce backward compatible updates and modifications to 
|apiservice| |contract version|. These changes are not intended to break any existing 
code that relies on the API (SDK, web applications, scripts, and so on). However, you 
might want to update or extend your code to use the new features and enhancements. 

To report any issues or discuss changes in this release, visit the Rackspace Community or 
contact Rackspace Support. 


.. Template instructions - 
   Content categories: What's New, Resolved Issues, Known Issues, Documentation changes.  
   Limit doc changes to content important to API users and developers, for example
   "added extended example to illustrate use of xxx operation" or something like that.
   
   

.. whats-new:

What's new
^^^^^^^^^^^^

.. Comment Provided bulleted list of all that apply:  New features, enhancements

This release resolves existing issues with |apiservice|  
|contract version|. 

.. Comment - New operations. Defined list with bullets if more than one operation.

.. Comment - Changed operations.  Defined list with bullets.
	
.. Comment - Schema changes. Item, part of schema (param, object, and so on), type of change (add, remove, modify)


.. resolved-issues:

Resolved Issues
^^^^^^^^^^^^^^^^^^

.. Comment Add "None for this release" if applicable.

- Scheduled Backup Fixes

  Convert automated backup schedule when m/s setup is converted to HA.

- HA MySQL Fixes:

  Checks for HA group actions.


Known issues
^^^^^^^^^^^^^^^^

|no changes|


.. doc-changes:

Documentation changes
^^^^^^^^^^^^^^^^^^^^^^

- Added volume and flavor info to the API operation List HA database instance details.

- Added note about converting automated backup schedule, if a source/replica has automated 
  backups enabled, to the API operation Convert replication setup to HA. In this case, 
  the schedule will be converted to an HA group automated backup schedule with the source 
  id set to the HA id. The day, hour and minute settings will be the same as the source or 
  replica schedule. 

- Source changes to RESTART state when enabling as master during replication setup.

