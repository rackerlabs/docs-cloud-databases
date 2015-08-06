.. _cdb-dg-overview:

========
Overview
========

Rackspace Cloud Databases is a fully managed database service based on Openstack. Using Cloud Databases, customers can easily provision database instances of varying virtual resource sizes without the need to maintain and/or update the database engine. Interactions with Cloud Databases occur programmatically via the Cloud Databases API as described in this developer guide.

..  note:: 
    Rackspace recommends that Cloud Databases users back up their data using backups in Cloud Databases.

The following figure shows an overview of Cloud Databases Infrastructure:

.. image:: /_images/cloud-databases-howitworks-graphic.png

.. _cdb-dg-overview-intended:

Intended audience
~~~~~~~~~~~~~~~~~

This Guide is intended to assist software developers who want to develop applications using the Cloud Databases API. It assumes the reader has a general understanding of databases and is familiar with:

-  ReSTful web services

-  HTTP/1.1 conventions

-  JSON data serialization formats

-  ATOM Syndication Format

.. _cdb-dg-overview-dochistory:

Document change history
~~~~~~~~~~~~~~~~~~~~~~~

This version of the Developer Guide replaces and obsolesces all previous versions. The most recent changes are described in the table below:

.. _cdb-dg-overview-dochistory-25062015:

June 25, 2015
--------------

Updated HA platform support information in :ref:`High availability for Cloud Databases <cdb-dg-generalapi-high-availability>` .

.. _cdb-dg-overview-dochistory-15062015:

June 15, 2015
--------------

Added information for incremental backups in Section 4.7, “On Demand Backups”.

Added information for scheduled backups in Section 4.8, “Scheduled Backups”.

Added information for High Availability database instances in Section 3.18, “High Availability for Cloud Databases” and Section 4.10, “High Availability”.

.. _cdb-dg-overview-dochistory-29042015:

April 29, 2015
-----------------

Added note about access to Cloud Files in Section 4.7, “On Demand Backups” and Create replica.

Removed warning about detaching replica in Section 3.17, “Replication”.

Added DETACH_REPLICA status to Section 3.9, “Database instance status”.

Changed warning to note and added information about DETACH_REPLICA status for Section 4.9.5, “Detach replica”.

.. _cdb-dg-overview-dochistory-10042015:

April 10, 2015
----------------

Added query parameter include_replicas in Section 4.2.2, “List all database instances” and Section 4.9.2, “List all replicas and replica source database instances”.

Added new examples for List all instances/replica sources and filter out replicas in Section 4.9.2, “List all replicas and replica source database instances”.

.. _cdb-dg-overview-addtl:

Additional resources
~~~~~~~~~~~~~~~~~~~~

Descriptive information about Cloud Databases is also published in its Web Application Description Language (WADL) and XML Schema Definition (XSD). You are welcome to read this information here:

-  The WADL is http://docs.rackspace.com/cdb/api/v1.0/cdb.wadl.

-  The XSD is http://docs.rackspace.com/cdb/api/v1.0/xsd/cdb.xsd.

You can download the most current versions of other API-related documents from http://docs.rackspace.com/.

For more details about Rackspace Cloud Databases, refer to http://www.rackspace.com/cloud/databases/. This site also offers links to Rackspace's official support channels, including knowledge center articles, forums, phone, chat, and email.

Using this API document, your Rackspace Cloud account, and at least one Cloud Server, you can get started whenever you'd like. See the *Getting Started with Rackspace Cloud Databases and Servers* at http://docs.rackspace.com/ for information about getting started using the API.

Please visit our `Product Feedback Forum`_ and let us know what you think about Cloud Databases!

You can also follow Rackspace updates and announcements via `Twitter`_.

This API uses standard HTTP 1.1 response codes as documented at http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html.

.. _Product Feedback Forum: http://feedback.rackspace.com
.. _Twitter: https://twitter.com/rackspace

.. _cdb-dg-overview-pricing:

Pricing and service level
~~~~~~~~~~~~~~~~~~~~~~~~~

Cloud Databases is part of the Rackspace Cloud and your use through the API will be billed as per the pricing schedule at http://www.rackspace.com/cloud/databases/pricing/.

.. note:: Currently Rackspace is charging the same price for High Availability database instances as for single instances for a limited time. In the future, there will be an increase in the price of High Availability database instances.

The Service Level Agreement (SLA) for Cloud Databases is available at http://www.rackspace.com/information/legal/cloud/sla#cloud_databases.

If you elect to use the Backups API in Cloud Databases, your backups are stored using Cloud Files and your use through the API will be billed as per the pricing schedule at http://www.rackspace.com/cloud/files/pricing/.

The Service Level Agreement (SLA) for Cloud Files is available at http://www.rackspace.com/information/legal/cloud/sla#cloud_files.
