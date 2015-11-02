.. version-v2.14.0-release-notes:

v2.14.0, April 10, 2015
---------------------------

What's new
~~~~~~~~~~~~

This release includes the following updates:

-  The release numbering scheme has been changed to
   be easier to accomodate hotfixes using the last number. For example,
   v2.14.1 could be used as the release number for a hotfix for v2.14.0.

-  Add query parameter ``include_replicas`` for filtering out replicas
   from List all database instances and List all replicas and replica
   source database instances API operations. For examples, see `List all
   instances/replica sources and filter out
   replicas <get-list-all-replicas-and-replica-source-database-instances-version-accountid-instances>`.
   
Resolved issues
~~~~~~~~~~~~~~~~

-  Fixed the following backup issues:

   -  Refresh authentication token when it expires in the middle of the
      backup process.

   -  Prevent restoring uncompleted backups.

   -  Report the correct status of backup failed, succeeded, and so
      forth.
      
Known issues
~~~~~~~~~~~~~~~~~

|no changes|


