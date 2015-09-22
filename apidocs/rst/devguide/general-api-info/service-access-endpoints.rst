.. _cdb-dg-generalapi-service-access-endpoints:

========================
Service access endpoints
========================

The Database Service is a regionalized service. The user of the service
is therefore responsible for appropriate replication, caching, and
overall maintenance of Cloud Databases data across regional boundaries
to other Cloud Databases servers.

You can find the available service access/endpoints for Cloud Databases
summarized in the table below.

..  tip:: 

  To help you decide which regionalized endpoint to use, read about
  special considerations for choosing a region at
  http://www.rackspace.com/knowledge_center/article/about-regions.

Table 3.1. Regionalized service endpoints

+-------------------------+----------------------------------------------------------------------------+
| Region                  | Endpoint                                                                   |
+=========================+============================================================================+
| Chicago (ORD)           | ``https://ord.databases.api.rackspacecloud.com/v1.0/``\ ``1234``/          |
+-------------------------+----------------------------------------------------------------------------+
| Dallas/Ft. Worth (DFW)  | ``https://dfw.databases.api.rackspacecloud.com/v1.0/``\ ``1234``/          |
+-------------------------+----------------------------------------------------------------------------+
| Northern Virginia (IAD) | ``https://iad.databases.api.rackspacecloud.com/v1.0/``\ ``1234``/          |
+-------------------------+----------------------------------------------------------------------------+
| London (LON)            | ``https://lon.databases.api.rackspacecloud.com/v1.0/``\ ``1234``/          |
+-------------------------+----------------------------------------------------------------------------+
| Sydney (SYD)            | ``https://syd.databases.api.rackspacecloud.com/v1.0/``\ ``1234``/          |
+-------------------------+----------------------------------------------------------------------------+
| Hong Kong (HKG)         | ``https://hkg.databases.api.rackspacecloud.com/v1.0/``\ ``1234``/          |
+-------------------------+----------------------------------------------------------------------------+

Replace the sample account ID number, ``1234``, with your actual account
number returned as part of the authentication service response.

You will find the actual account number after the final '/' in the
``publicURL`` field returned by the authentication response. For
example, in the previous "Example: Authenticate: JSON Response" you can
see from the ``publicURL`` field for ``cloudServers``
("https://servers.api.rackspacecloud.com/v1.0/**1100111**") that the
account number is 1100111.
