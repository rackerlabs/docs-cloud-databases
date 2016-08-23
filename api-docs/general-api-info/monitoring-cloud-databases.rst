.. _cdb-dg-generalapi-monitoring:

==========================
Monitoring Cloud Databases
==========================

Monitoring is available for Cloud Databases to allow users to get more
information about their database instances via the monitoring checks that are
available. The monitoring capability now applies to all instances, not just
those that were created after the v1.0.27 release on July 29, 2013.

There is a 1:1 mapping of Cloud Databases to monitoring entities. The
monitoring entity has a field called ``agent_id`` that is the same as the
Cloud Database ``instance id``. 

A user can list the monitoring checks available on the monitoring entity by
using the
:rax-devdocs:`List Checks for an entity <rackspace-monitoring/v1/developer-guide/#list-checks-for-an-entity>`
operation available in the Rackspace Monitoring API.

The following monitoring checks are available to users:

-  Load Average

-  CPU

-  Memory

-  Storage (Disk)

-  Network

-  Database

   The following data points are supported on the Database checks:

   -  core.aborted\_clients

   -  core.queries

   -  core.connections

   -  core.uptime

   -  threads.created

   -  threads.running

   -  threads.connected

   -  qcache.queries\_in\_cache

   -  qcache.lowmem\_prunes

   -  qcache.free\_memory

   -  qcache.total\_blocks

   -  qcache.inserts

   -  qcache.hits

   -  qcache.not\_cached

   -  qcache.free\_blocks

   -  innodb.buffer\_pool\_pages\_total

   -  innodb.buffer\_pool\_pages\_flushed

   -  innodb.row\_lock\_time\_avg

   -  innodb.rows\_inserted

   -  innodb.row\_lock\_time\_max

   -  innodb.rows\_updated

   -  innodb.buffer\_pool\_pages\_free

   -  innodb.buffer\_pool\_pages\_dirty

   -  innodb.row\_lock\_time

   -  innodb.rows\_deleted

   -  innodb.rows\_read

A user can exercise these checks by submitting a
:rax-devdocs:`Test an existing check <rackspace-monitoring/v1/developer-guide/#test-an-existing-check>`
API request using the Rackspace Monitoring service.

Monitoring alarms available to users include:

-  Storage alarm sent via email to the default admin notification list

   -  label = Low Disk Space

   -  WARNING > 90% used

      message emits = Less than 10% free space left.

   -  CRITICAL > 95% used

      message emits = Less than 5% free space left.

..  note::
    -  Users are *not* allowed to modify the managed entity or checks.

    -  Users *are* allowed to add notifications and alarms to the existing
       checks.

    -  For email notifications, users should check their junk/spam folder in
       case they have filtering on their email messages.

    -  Refer to the following information on the monitoring API for more
       details:

      -  :rax-devdocs:`How cloud monitoring works <rackspace-monitoring/v1/developer-guide/#how-rackspace-monitoring-works>`

      -  :rax-devdocs:`Checks <rackspace-monitoring/v1/developer-guide/#document-api-operations/check-operations>`

      -  :rax-devdocs:`Check types <rackspace-monitoring/v1/developer-guide/#document-api-operations/check-type-operations>`
