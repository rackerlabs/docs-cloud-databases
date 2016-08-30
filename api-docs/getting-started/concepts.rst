.. _concepts:

==================
|service| concepts
==================

To use the Cloud Databases API effectively, you should understand several key
concepts.

.. _concepts-backup:

Backup
~~~~~~

A copy of computer data for a database instance that can be used to restore the
original instance if necessary.

.. _concepts-configgroup:

Configuration group
~~~~~~~~~~~~~~~~~~~

A configuration group is a collection of key/value pairs, where the valid
key/values are defined per datastore. Some directives are capable of being
applied dynamically, while other directives require a server restart to take
effect. The configuration group can be applied to an instance at creation or
applied to an existing instance to modify the behavior of the running datastore
on the instance. A configuration group consists of a collection of
configuration parameters.

.. _concepts-configparam:

Configuration parameter
~~~~~~~~~~~~~~~~~~~~~~~

A configuration parameter is a key/value pair that represents settings that can
be applied to a database instance.

.. _concepts-dbinstance:

Database instance
~~~~~~~~~~~~~~~~~

A database instance is an isolated database environment with compute and
storage resources in a single tenant environment on a shared physical host
machine. You can run a database instance with your choice of one of the
following database engines: MySQL, Percona, or MariaDB.

.. _concepts-db:

Database
~~~~~~~~

The database is the database engine running on your instance. Currently the
supported database engines and their versions are: MySQL 5.6, MySQL 5.1,
Percona 5.6, and MariaDB 10.

.. _concepts-flavor:

Flavor
~~~~~~

A flavor is an available hardware configuration for a database instance. Each
flavor is optimized for performance and has a unique combination of memory
capacity, priority for CPU time, and network bandwidth.

.. _concepts-ha-instance-group:

High Availability Instance Group
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

A High Availability Instance Group includes a source database instance and one
or two replicas. In the event that the primary source database instance becomes
unavailable, it triggers an automatic failover to one of the replicas attached.

.. _concepts-replica:

Replica
~~~~~~~

A replica is an exact copy of a database instance that is kept synchronized
with its database instance source.

.. _concepts-volume:

Volume
~~~~~~

A volume is user-specified storage that contains the database engine data
directory. Volumes are automatically provisioned on shared Internet Small
Computer System Interface (iSCSI) storage area networks (SAN) that provide for
increased performance, scalability, availability and manageability.
Applications with high I/O demands are performance optimized and data is
protected through both local and network RAID-10. Additionally, network RAID
provides synchronous replication of volumes with automatic failover and load
balancing across available storage clusters.

