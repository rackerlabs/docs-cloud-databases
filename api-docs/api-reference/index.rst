.. _api-reference:

=============
API reference
=============

Learn about the available |apiservice| resources and operations, and
see request and response examples. You can use the |apiservice| operations
to interact directly with the service.

You can use the Cloud DB API operations to interact directly with the Cloud
Databases service.  You can also run DB API operations by using the Rackspace
Command Line Client, the SDK, or from the Cloud Control panel.

.. note::

   Do not use trailing slashes (/) at the end of calls to API operations, since
   this may cause the call to fail. For example, do not use
   ``GET /instances/detail/`` (with the trailing slash at the end). Rather, use
   ``GET /instances/detail`` instead.

.. toctree::
   :maxdepth: 2

   api-versions
   database-instances
   database-instance-actions
   databases
   user-management
   flavors
   backups
   automated-backups
   replication
   ha
   configurations
   configuration-parameters
   datastore-types-versions
