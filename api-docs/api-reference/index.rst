.. _api-reference:

=============
API Reference
=============

Learn about the available |apiservice| resources and operations, and
see request and response examples. You can use the |apiservice| operations
to interact directly with the service.

You can also perform operations by using the
:rax-devdocs:`Rackspace Command Line Interface (rack CLI) <#sdks>`, one
of the language-specific :rax-devdocs:`software development kits <#sdks>`,
or the `Cloud Control Panel <https://mycloud.rackspace.com/>`_.

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
