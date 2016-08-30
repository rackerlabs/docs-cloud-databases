.. _user-operations:

=====
Users
=====

This section describes the following API operations that are supported for
users.

.. contents::
   :local:
   :depth: 1

In this section, "user has access to a database" means that the user has full
create, read, update, and delete access to the given database. In other words,
on a cloud database instance, a user named USER and a database named DATABASE
exist, and within MySQL, a ``GRANT ALL ON DATABASE.* TO USER`` has been issued
on the instance.

.. include:: methods/post-create-user-version-accountid-instances-instanceid-users.rst
.. include:: methods/get-list-users-in-database-instance-version-accountid-instances-instanceid-users.rst
.. include:: methods/put-change-user(s)-password-version-accountid-instances-instanceid-users.rst
.. include:: methods/put-modify-user-attributes-version-accountid-instances-instanceid-users-name.rst
.. include:: methods/get-list-user-version-accountid-instances-instanceid-users-name.rst
.. include:: methods/delete-delete-user-version-accountid-instances-instanceid-users-name.rst
.. include:: methods/get-list-user-access-version-accountid-instances-instanceid-users-name-databases.rst
.. include:: methods/put-grant-user-access-version-accountid-instances-instanceid-users-name-databases.rst
.. include:: methods/delete-revoke-user-access-version-accountid-instances-instanceid-users-name-databases-databasename.rst
