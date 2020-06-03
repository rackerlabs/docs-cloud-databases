.. version-3.8.0-release-notes:

v3.8.0, June 2, 2020
------------------------

What's new
~~~~~~~~~~

-  Percona version 5.7 is available for instance and HA group provisioning.

-  MariaDB version 10.4enc is available for instance and HA group provisioning. This version has
   data-at-rest encryption enabled.

-  Binary logging has been disabled by default for MySQL 8.0 instances.

-  Additional options are available for the on-demand upgrade for single instances of MySQL 5.6 and MariaDB 10.4:

   -  You can upgrade MySQL 5.6 to MariaDB 10.4enc.
   -  You can upgrade MariaDB 10.4 to MariaDB 10.4enc.

-  The API no longer allows you to specify the deprecated datastore versions, MySQL 5.1/5.6 and MariaDB 10/10.1,
   when building new instances or HA groups.

   **Note:** This does not impact existing instances or HA groups with respect to adding replicas, failovers, etc.

Resolved issues
~~~~~~~~~~~~~~~

-  Modifying only a user's password now works as expected.

-  The InternalServerError response has been replaced with the ACLNotFound response when you make a request to delete an ACL from an HA group with no ACLs.

Known issues
~~~~~~~~~~~~

|no changes|
