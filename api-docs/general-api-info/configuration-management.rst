.. _cdb-dg-generalapi-configmgmt:

========================
Configuration management
========================

The configuration management capability allows users of Cloud Databases to
override the default database engine configuration settings provided by the
Cloud Databases service.

A *configuration group* is a collection of key/value pairs, where the valid
key/values are defined in the MySQL manual at
http://dev.mysql.com/doc/refman/5.6/en/server-system-variables.html. Some
directives are capable of being applied dynamically, while other directives
require a server restart to take effect.

A default configuration group is applied to an instance if you create an
instance without associating the instance with a configuration group. The
default configuration is based upon the database engine and the instance
flavor. If you want your database instance to run with custom defined
configuration settings, you need to assign a custom defined configuration group
to the instance. A configuration group can be applied to multiple instances.

You can create a new configuration group, modify parameters of an existing
configuration group, and also modify the database instance to use a different
configuration group. When a configuration group is modified either by way of
adding a new key/value pair or modifying an existing key/value pair, the
service updates the `overrides.cnf` file for every instance that is associated
with the configuration.

The service attempts to dynamically update all associated database instances if
the parameters changed in the configuration group are all dynamic. But if any
of the parameters changed in the configuration group require a restart, then
any instance that has the configuration group assigned to it will require a
restart to apply the configuration group or any changes made to the
configuration group.

Rackspace configures the validation rules for key/value pairs that can be
assigned to a configuration group. These rules can be retrieved by the user
from the API through the configuration parameter's resource as described in
:ref:`Configuration parameters <configuration-parameters-operations>`.

Refer to :ref:`Configurations <configuration-operations>` for the API
operations for configurations.
