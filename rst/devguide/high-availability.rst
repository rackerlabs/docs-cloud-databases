.. _cdb-dg-generalapi-high-availability:

=====================================
High availability for Cloud Databases
=====================================

High Availability for Cloud Databases means that Cloud Database users can run their critical
production workloads without worrying about their database becoming unavailable.
When using Cloud Databases High Availability instance group, users can choose to add one
or a maximum of two replicas to the source database instance. When you use a High Availability
instance group, it ensures that in case the master becomes unavailable, an automatic
failover to the replicas is initiated within 10-30 seconds of downtime. Cloud Databases uses
the `MySQL MHA utility`_ to automate master failover. In case some of the slaves have not received
the latest relay log events, MHA automatically identifies differential relay log events
from the latest slave, and applies differential events to the other slaves. This ensures that all
replicas can be consistent.

.. _MySQL MHA utility: https://code.google.com/p/mysql-master-ha/

In addition, users can also use replicas for scaling their read-heavy workloads. You can send
only your read requests to your replica. All write requests can be sent only to the source
database instance. Cloud Databases High Availability instance group uses semi-synchronous
replication.

High Availability instance groups are supported for MySQL 5.6, Percona 5.6, and MariaDB 10.

..  note::
    -  Currently we are charging the same price for High Availability database instances
       as for single instances for a limited time. In the future, there will be
       an increase in the price of High Availability database instances.
       
    -  There will be a single access point, hostname, for accessing the source database instance 
       and replicas in the HA group. By default all the reads and writes will be directed to port 
       3306. However you can direct read-only traffic to port 3307 and the reads will be done from 
       each replica in a round robin fashion.

    -  There will be a lag between the source database instance and replicas. All of the updates 
       will be applied to the replica after they occur on the master.
       
    -  Access Control Lists (ACLs) need to be added to the High Availability instance
       group before accessing the High Availability database instances. See `Add ACLs to an HA instance`_.              
       
.. _Add ACLs to an HA instance: http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/POST_addAclToHaInstance__version___accountId__ha__haId__acls_ha.html       


**Recommendation**. It is recommended to have two replicas on an HA group. Having two replicas will ensure that in case failover occurs, your database will still have a High Availability setup.    


Warning

Adding a replica will cause the source database instance to restart and your database will be unavailable for a brief period.

.. _cdb-dg-generalapi-high-availability-limitations:

Limitations
~~~~~~~~~~~

-  The maximum number of replicas allowed per source database instance is two. We will
   increase the limit on the number of replicas later.

-  HA group is only available for instance flavors 1GB and above.

-  Both source database instance and replicas should be in the same region.

-  The source DB instance and replica should be in the same region.

-  Currently you cannot perform backups, resize, or apply configuration groups on an HA group.

-  In case failover occurs, there will be an automatic failover to the replica closest to the
   failed database instance. Cloud Databases will remove the failed database instance. You
   will have to manually create another replica to add to the HA group. The API call for
   adding a new replica is coming soon. In the future, Cloud Databases will automate creating
   another replica after the failover occurs.
