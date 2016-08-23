.. _cdb-dg-generalapi-replication:

===========
Replication
===========

Replication allows users of Cloud Databases to create a read replica of a
database instance that can be used for scaling out read-heavy workloads or for
ensuring availability of your database in case of instance failure. As the term
implies, you can send only your *read* requests to your replica. All the write
requests can be sent only to the source database instance. When you create a
read replica, you should specify an existing database instance as the source
of the replica. Rackspace Cloud Databases uses asynchronous replication.

Replication is supported for MySQL 5.6, Percona 5.6, and MariaDB 10. For
instances running MySQL 5.1,
:how-to:`upgrade to MySQL 5.6 <upgrade-a-cloud-databases-instance-from-mysql-51-to-mysql-56>`.

..  note::
    There is a lag between the source database instance and the replica. All
    the updates are applied to the replica after they occur on the master.

.. _cdb-dg-generalapi-replication-limitations:

Limitations
~~~~~~~~~~~

-  The maximum number of replicas allowed per source database instance
   is two.

-  Replication can be only set up on instance flavors 1GB and above.

-  Both source database instance and replica should be running the same
   database and version.

-  The source DB instance and replica should be in the same region.

-  It is recommended to have the same disk and RAM size on your replica
   as you have for your source database instance.

.. warning::
    Adding a replica will restart the MySQL service on the source database
    instance. However the state of the instance might not reflect that and
    still be `ACTIVE`. Wait for a couple of seconds for the process to be
    complete. The best way to verify whether the process is complete is to
    :ref:`check the slave metrics <cdb-dg-generalapi-monitoringread>`.

There are several use cases where you may want to use replication:

-  **Scaling**

   You can create replicas of your DB instance and distribute read traffic for
   your applications on the replicas. All the writes and updates will be
   applied to the source instance, whereas reads can take place on any one of
   the replica instances. This can help improve the overall performance of an
   application as writes would only be dedicated to the source instance and
   reads will be spread across replicas.

-  **Increased Availability**

   In case of instance failure, the replica can act as the new source database
   instance and ensure that an application has minimal downtime.

   To make the replica the new source database instance for your application,
   you will have to detach the replica (hyperlink) from the source instance
   and change the application endpoint to this new source database instance.

-  **Analytics**

   A large number of applications using MySQL databases are used for performing
   analysis. Replication helps in maintaining multiple copies of the data, and
   analysis of information can be done on the replica without affecting the
   performance of writes/updates on the source database instance.

-  **Improved Reliability**

   Replication can be used to back up data from a replica. The replica can be
   paused from the replication process, and you can make a copy of live data
   without affecting any operations on the source database instance.

For information about monitoring read replication, refer to
:ref:`monitoring read replication <cdb-dg-generalapi-monitoringread>`.

For the API operations for replication, refer to :ref:`replication-operations`.
