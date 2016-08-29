.. _service-access:

========================
Service access endpoints
========================

The |apiservice| service is a regionalized service. The user of the service
is therefore responsible for appropriate replication, caching, and
overall maintenance of Cloud Databases data across regional boundaries
to other Cloud Databases servers.

The following table lists the |product name| endpoints that are available
for each region.

.. tip::
   To help you decide which regionalized endpoint to use, read about
   :how-to:`special considerations for choosing a region <about-regions>`.

**Regionalized service endpoints**

+-------------------------+----------------------------------------------------------------------------+
| Region                  | Endpoint                                                                   |
+=========================+============================================================================+
| Chicago (ORD)           | ``https://ord.databases.api.rackspacecloud.com/v1.0/1234``                 |
+-------------------------+----------------------------------------------------------------------------+
| Dallas/Ft. Worth (DFW)  | ``https://dfw.databases.api.rackspacecloud.com/v1.0/1234``                 |
+-------------------------+----------------------------------------------------------------------------+
| Northern Virginia (IAD) | ``https://iad.databases.api.rackspacecloud.com/v1.0/1234``                 |
+-------------------------+----------------------------------------------------------------------------+
| London (LON)            | ``https://lon.databases.api.rackspacecloud.com/v1.0/1234``                 |
+-------------------------+----------------------------------------------------------------------------+
| Sydney (SYD)            | ``https://syd.databases.api.rackspacecloud.com/v1.0/1234``                 |
+-------------------------+----------------------------------------------------------------------------+
| Hong Kong (HKG)         | ``https://hkg.databases.api.rackspacecloud.com/v1.0/1234``                 |
+-------------------------+----------------------------------------------------------------------------+

Replace the sample account ID number, ``1234``, with your actual account number
that is returned as part of the authentication response. The account number is
located  after the  final slash (/) in the ``publicURL`` field.

The service catalog returned in the authentication response specifies the
correct service access endpoint for your account to use for accessing
|product name|. Use the service type (``rax:database``) to locate the
correct endpoint in the service catalog. 