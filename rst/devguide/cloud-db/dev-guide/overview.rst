.. _cdb-dg-overview:

========
Overview
========

Rackspace Cloud Databases is a fully managed database service based on Openstack. Using Cloud Databases, customers can easily provision database instances of varying virtual resource sizes without the need to maintain and/or update the database engine. Interactions with Cloud Databases occur programmatically via the Cloud Databases API as described in this developer guide.

..  note:: 
    Rackspace recommends that Cloud Databases users back up their data using backups in Cloud Databases.

The following figure shows an overview of Cloud Databases Infrastructure:

.. image:: /_images/cloud-databases-howitworks-graphic.png

.. cdb-dg-overview-intended:

Intended audience
~~~~~~~~~~~~~~~~~

This Guide is intended to assist software developers who want to develop applications using the Cloud Databases API. It assumes the reader has a general understanding of databases and is familiar with:

-  ReSTful web services

-  HTTP/1.1 conventions

-  JSON data serialization formats

-  ATOM Syndication Format

.. cdb-dg-overview-addtl:

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

The Service Level Agreement (SLA) for Cloud Databases is available at http://www.rackspace.com/information/legal/cloud/sla#cloud_databases.

If you elect to use the Backups API in Cloud Databases, your backups are stored using Cloud Files and your use through the API will be billed as per the pricing schedule at http://www.rackspace.com/cloud/files/pricing/.

The Service Level Agreement (SLA) for Cloud Files is available at http://www.rackspace.com/information/legal/cloud/sla#cloud_files.
