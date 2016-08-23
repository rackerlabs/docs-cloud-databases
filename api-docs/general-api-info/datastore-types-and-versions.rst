.. _cdb-dg-generalapi-datastore:

============================
Datastore types and versions
============================

Datastore types management will allow users of Cloud Databases to select
database type and version from the list of available choices provided by
Rackspace. Rackspace will control datastore types and versions, adding new
types and versions as they become available, and deactivating old versions at
end-of-life.

To take advantage of this capability, users can specify datastore type and
optional version at instance creation. *Datastore Type* is a family of database
engines, like mysql, mongodb, and cassandra. *Datastore Version* defines the
engine version of the selected datastore type. If users do not specify the
datastore type and version at instance creation, the default database is
MySQL 5.6.

..  note::
    For the SYD and HKG datacenters only, the default database is MySQL 5.1 if
    users do not specify the datastore type and version at instance creation.

Refer to :ref:`datastore-types-versions-operations` for the API operations for
datastore types and versions.

For an example of using the `type` and `version` information in the Create
Database Instance API request, see the "Create Database Instance *Datastore*
Request: JSON" example for the Create Database Instance API operation.

See the sections that follow for information about the datastores that are
currently supported.

.. _cdb-dg-generalapi-datastore-mysql56:

MySQL 5.6
~~~~~~~~~

MySQL is a high performance, open source database developed by Oracle. The
latest MySQL release offers great improvements  in InnoDB scalability,
transparency, and replication.

For more information on MySQL, see http://dev.mysql.com/.

For MySQL, the `type` is "MySQL" and the `version` is "5.6".

MySQL 5.6 is the default database for Cloud Databases.

..  note::
    For the SYD and HKG regions only, the only available database is MySQL 5.1.
    If users do not specify the datastore type and version at instance creation
    in these regions, the default is MySQL 5.1.

.. _cdb-dg-generalapi-datastore-mysql51:

MySQL 5.1
~~~~~~~~~

Rackspace currently supports MySQL 5.1. The latest version of MySQL (5.6) has
many improvements over MySQL 5.1 and we will eventually deactivate MySQL 5.1
at end-of-life.

For more information on MySQL, see http://dev.mysql.com/.

For MySQL, the `type` is "MySQL" and the `version` is "5.1".

.. _cdb-dg-generalapi-datastore-percona56:

Percona 5.6
~~~~~~~~~~~

Percona Server is a high performance, open source, drop-in replacement for 
MySQL. It offers all the improvements found in MySQL 5.6 Community Edition 
plus scalability, availability, backup, and security features found only in 
MySQL 5.6 Enterprise Edition.

For more information on Percona,
see http://www.percona.com/software/percona-server.

For Percona, the `type` is "Percona" and the `version` is "5.6".

.. _cdb-dg-generalapi-datastore-mariadb10:

MariaDB 10
~~~~~~~~~~

MariaDB is a high-performance RDBMS. MariaDB is application-compatible with
MySQL, but adds many new capabilities and enhancements to address the most
challenging web and enterprise application use cases.

For more information on MariaDB, see https://mariadb.org/en/about/.

For MariaDB, the `type` is "MariaDB" and the `version` is "10".
