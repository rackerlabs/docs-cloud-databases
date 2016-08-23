.. _cdb-dg-generalapi-versions:

==============================
Contract version & API version
==============================

.. _cdb-dg-generalapi-versions-contract:

Contract version
~~~~~~~~~~~~~~~~

The contract version denotes the data model and behavior that the API supports.
The requested contract version is included in all request URLs. Different
contract versions of the API may be available at any given time and are not
guaranteed to be compatible with one another.

**Example Request URL**::

  https://ord.databases.api.rackspacecloud.com/v1.0/1234

.. note::
  This document pertains to contract version 1.0.

.. _cdb-dg-generalapi-versions-api:

API version
~~~~~~~~~~~

The API List Versions call is available to show the current API version as well
as information about all versions of the API.
