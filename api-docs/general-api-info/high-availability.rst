.. _cdb-dg-generalapi-high-availability:

=====================================
High availability for Cloud Databases
=====================================

High Availability for Cloud Databases means that Cloud Database users
can run their critical production workloads without worrying about their
database becoming unavailable. When using Cloud Databases High
Availability instance group, users can choose to add one or a maximum of
two replicas to the source database instance. When you use a High
Availability instance group, it ensures that in case the master becomes
unavailable, an automatic failover to the replicas is initiated within
10-30 seconds of downtime. Cloud Databases uses the `MySQL
MHA <https://code.google.com/p/mysql-master-ha/>`__ utility to automate
master failover. In case some of the slaves have not received the latest
relay log events, MHA automatically identifies differential relay log
events from the latest slave, and applies differential events to the
other slaves. This ensures that all replicas can be consistent.

In addition, users can also use replicas for scaling their read-heavy
workloads. You can send only your *read* requests to your replica. All
*write* requests can be sent only to the source database instance. Cloud
Databases High Availability instance group uses semi-synchronous
replication.

High Availability instance groups are supported for MySQL 5.6, Percona
5.6, and MariaDB 10.

The following are guidelines for High Availability instance groups:

-  Currently we are charging the same price for High Availability
   database instances as for single instances for a limited time. In the
   future, there will be an increase in the price of High Availability
   database instances. 

-  Access Control Lists (ACLs) need to be added to the High Availability
   instance group before accessing the High Availability database
   instances. See
   :rax-devdocs:`Add ACLs to an HA instance <cloud-databases/v1/developer-guide/#add-acls-to-an-ha-instance>`.

-  There will be a single access point, hostname, for accessing the
   source database instance and replicas in the HA group. By default all
   the reads and writes will be directed to port 3306. However you
   can direct read-only traffic to port 3307 and the reads will be done
   from each replica in a round robin fashion.

-  There will be a lag between the source database instance and
   replicas. All of the updates will be applied to the replica after
   they occur on the master.

-  The only allowed operations on instances that are part of the HA
   group are Create users and Create databases (on source only). All
   other operations are blocked on these instances.

-  Currently all the nodes that are part of the HA group would need to
   be of the same flavor and size.

-  In case a failover occurs, there will be an automatic failover to the
   replica closest to the failed database instance. Cloud Databases will
   remove the failed database instance. A new replica of the same flavor
   and volume as the other instances that are part of the HA group will
   be built and automatically added to this setup in order to maintain
   the HA node configuration. For the period when the new replica is
   being added, the HA state would be ``ADDING_REPLICA`` and would
   switch to ``ACTIVE`` once the node has been successfully added.

..  warning::

   Automatically adding a new replica node would restart the MHA manager
   service (which monitors the source/replica instances to trigger
   failover) and the haproxy service on the load balancer nodes. Refer
   to the KC article for more details about these components at
   :how-to:`High availability for Cloud Databases
   <high-availability-for-cloud-databases>`.

**Recommendation. **\ It is recommended to have two replicas on an HA
group. Having two replicas will ensure that in case failover occurs,
your database will still have a High Availability setup.

**Limitations. **

-  The maximum number of replicas allowed per source database instance
   is two. We will increase the limit on the number of replicas later.

-  HA group is only available for instance flavors 1GB and above.

-  Both source database instance and replicas should be in the same
   region.

For more details about HA groups refer to the KC article at
:how-to:`High availability for Cloud Databases
<high-availability-for-cloud-databases>`.

.. _ha-dbinstance-status:

HA database instance group status
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

When you perform actions on a high availability database group, the API
service return current cluster status information in the response.

The following table describes the available status values for a cluster.

.. csv-table:: Status values for high availability clusters
  :widths: 25 75
  :header-rows: 1

  "Status", "Description"
  "``BUILD``", "The HA Group is being created."
  "``ACTIVE``", "The HA Group was successfully created
  (Source/Replica(s)/Load Balancers ACTIVE)."
  "``BACKUP``", "The HA Group is being backed up. (The database instance part
  of the HA group being backed up will also be in BACKUP state)."
  "``ADDING_REPLICA``", "A new replica instance is being added to the HA
  Group."
  "``REMOVING_REPLICA``", "A replica instance is being removed from the HA
  Group."
  "``RESTART_REQUIRED``", "A change has occurred to the configuration of
  instances part of the HA Group that requires the HA Group to be restarted
  at the user’s convenience."
  "``REBOOT``", "The database instances included in the HA Group are being
  rebooted."
  "``DELETING``", "The HA Group is being deleted."
  "``DELETED``", "The HA Group has been deleted."
  "``RESIZING_VOLUME``", "The volume for all instances included in the HA
  Group is being resized."
  "``RESIZING_FLAVOR``", "The RAM for all instances included in the HA Group
  is being resized."
  "``FORCING_FAILOVER``", "An admin user has triggered a force failover on
  the HA Group to promote an existing replica to be the new source."
  "``DISABLING_FAILOVER``", "Failover is being disabled on the HA Group
  (initiated via an admin user)."
  "``ENABLING_FAILOVER``", "Failover is being re-enabled on the HA Group
  (initiated via an admin user)."
  "``FAILOVER_DISABLED``", "Failover is currently disabled on the HA Group."
  "``UPDATING_PROXY_NODES``", "The Load Balancer nodes included in the HA Group
  are being re-configured (initiated via an admin user)."
  "``ERROR``", "The HA Group failed to build successfully."
  "``ADD_REPLICA_FAIL``", "There was a failure adding a replica instance to
  the HA Group."
  "``REMOVE_REPLICA_ERROR``", "There was a failure removing a replica from
  the HA Group."
  "``DELETION-ERROR``", "There was a failure deleting the HA Group."
  "``UPDATE_PROXY_NODES_ERROR``", "There was a failure reconfiguring the load
  balancers part of the HA Group."
  "``REPLICATION_ERROR``", "The replication between
  source/replica(s) in the HA Group is broken. The replica instance with broken
  replication will also report this state."
  "``HA_FAILOVER``", "A failover has occurred on the HA Group."
  "``RESIZE_FLAVOR_ERROR``", "There was a failure resizing the flavor/RAM of
  the HA Group."
  "``VOLUME_RESIZE_ERROR``", "There was a failure resizing the volume of the
  HA Group."
