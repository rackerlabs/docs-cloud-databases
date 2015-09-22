.. _cdb-dg-overview:

========
Overview
========

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

.. _cdb-dg-overview-dochistory-10092015:

September 10, 2015
---------------------

Updated information on backup schedule for :ref:`Create scheduled backup <post-create-scheduled-backup-version-accountid-schedules>`.

Added new API operation :ref:`Update schedule for backups by schedule ID <put-update-schedule-for-backups-by-schedule-id-version-accountid-schedules-scheduleid>`.

.. _cdb-dg-overview-dochistory-02092015:

September 2, 2015
---------------------

Updated information for :ref:`High Availability for Cloud Databases <cdb-dg-generalapi-high-availability>`.

Added information for backups to :ref:`High Availability <high-availability-operations>`.

Updated description for acls parameter and example for Create HA database instance: JSON
request for :ref:`Create database instance <post-create-database-instance-version-accountid-instances>`.

Enhanced description for :ref:`Add replica to HA instance <post-add-replica-to-an-ha-instance-version-accountid-ha-haid-action>`.

Added new operations :ref:`Remove replica from an HA instance <post-remove-replica-from-an-ha-instance-version-accountid-ha-haid-action>`, 
:ref:`Create backup for an HA instance <post-create-backup-for-an-ha-instance-version-accountid-backups>`,
and :ref:`List backups of an HA instance <get-list-backups-of-an-ha-instance-version-accountid-ha-haid-backups>`.

Updated examples for :ref:`List backups <get-list-backups-version-accountid-backups>`.

Updated examples for :ref:`List backups by ID <get-list-backup-by-id-version-accountid-backups-backupid>`.

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
