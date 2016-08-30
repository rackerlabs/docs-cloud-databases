.. version-v2.14.0-release-notes:

v2.14.0, April 10, 2015
-----------------------

What's new
~~~~~~~~~~

-  The release numbering scheme has been changed to
   make it easier to accomodate hotfixes by using the last number. For example,
   v2.14.1 could be used as the release number for a hotfix for v2.14.0.

-  The ``include_replicas`` query parameter has been added for filtering out
   replicas from the List all database instances and List all replicas and
   replica source database instances API operations. For examples, see
   :ref:`List all instances/replica sources and filter out
   replicas <get-list-all-replicas-and-replica-source-database-instances-version-accountid-instances>`.

Resolved issues
~~~~~~~~~~~~~~~

-  Fixed the following backup issues:

   -  The authentication token was refreshed when it expired in the middle of
      the backup process.

   -  Uncompleted backups are prevented from being restored.

   -  The correct status of the backup (failed, succeeded, and so on) was not
      reported.

Known issues
~~~~~~~~~~~~

|no changes|
