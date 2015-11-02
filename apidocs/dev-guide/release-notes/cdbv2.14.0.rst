=============================================================================
v2.14.0, April 10, 2015 - Rackspace Cloud Databases Release Notes  - API v1.0
=============================================================================

.. rubric::  v2.14.0, April 10, 2015
   :name: v2.14.0-april-10-2015
   :class: title

What's new
~~~~~~~~~~~~

-  With this release, the release numbering scheme has been changed to
   be easier to accomodate hotfixes using the last number. For example,
   v2.14.1 could be used as the release number for a hotfix for v2.14.0.

-  Add query parameter ``include_replicas`` for filtering out replicas
   from List all database instances and List all replicas and replica
   source database instances API operations. For examples, see `List all
   instances/replica sources and filter out
   replicas <http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/GET_getReplicasOrReplicaSources__version___accountId__instances_replication.html>`__.

-  Fixed the following backup issues:

   -  Refresh authentication token when it expires in the middle of the
      backup process.

   -  Prevent restoring uncompleted backups.

   -  Report the correct status of backup failed, succeeded, and so
      forth.

**Resources**

-  Get started using the Cloud Databases API to create databases in
   the Getting Started Guide at: http://docs.rackspace.com/api/.

-  Get reference information and examples in the Cloud Databases
   Developer Guide at: http://docs.rackspace.com/api/.

-  Support for Cloud Databases is available for US, UK, HKG, and SYD
   customers 24x7x365 via phone, chat, or you may also `File a
   Ticket <https://manage.rackspacecloud.com/Tickets/YourTickets.do>`__.

-  Please visit our \ `Product Feedback
   Forum <http://feedback.rackspace.com>`__ and let us know what you
   think about Cloud Databases!
