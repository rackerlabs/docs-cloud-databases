.. _ha-dbinstance-status:

===========================
HA Database instance status
===========================

When you perform actions on a high availability database group, the API
service return current cluster status information in the response.

The following table describes the available status values for a cluster.

.. csv-table:: Status values for high availability clusters
  :header: "Status", "Description"
  :widths: 25 75

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
