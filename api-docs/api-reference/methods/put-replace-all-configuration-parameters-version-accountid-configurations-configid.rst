.. _put-replace-all-configuration-parameters-version-accountid-configurations-configid:

Replace all configuration parameters
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    PUT /{version}/{accountId}/configurations/{configId}

Replaces all of the configuration parameter s associated with the specified
configuration group.

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |You are not authorized   |
|                          |                         |to complete this         |
|                          |                         |operation. This error    |
|                          |                         |can occur if the request |
|                          |                         |is submitted with an     |
|                          |                         |invalid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+
|403                       |Forbidden                |You are denied access to |
|                          |                         |the requested resource.  |
+--------------------------+-------------------------+-------------------------+
|404                       |Not Found                |The requested item was   |
|                          |                         |not found.               |
+--------------------------+-------------------------+-------------------------+
|405                       |badMethod                |The specified method is  |
|                          |                         |not allowed for the      |
|                          |                         |given resource.          |
+--------------------------+-------------------------+-------------------------+
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|422                       |unprocessableEntity      |The item cannot be       |
|                          |                         |processed.               |
+--------------------------+-------------------------+-------------------------+
|500                       |instanceFault            |The instance has         |
|                          |                         |experienced a fault.     |
+--------------------------+-------------------------+-------------------------+
|501                       |notImplemented           |The server does not      |
|                          |                         |support the              |
|                          |                         |functionality required   |
|                          |                         |to fulfill the request.  |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+

Request
-------

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{accountId}               |String                   |The account ID of the    |
|                          |                         |owner of the specified   |
|                          |                         |instance.                |
+--------------------------+-------------------------+-------------------------+
|{configId}                |String                   |The configuration ID for |
|                          |                         |the specified            |
|                          |                         |configuration group.     |
+--------------------------+-------------------------+-------------------------+

**Example Replace all configuration parameters: JSON request**

The following example shows the Replace all configuration parameters request:

.. code::

   PUT /v1.0/1234/configurations/f5aaf933-86b2-440e-a9dc-36c24665b3b4 HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

   {
       "configuration": {
           "description": "example updated description",
           "name": "example-updated-name",
           "values": {
               "collation_server": "utf8_unicode_ci",
               "connect_timeout": 150
           }
       }
   }

.. note::
   Each value provided for ``name`` and ``description`` must be a string
   composed of 1 to 255 alphanumeric characters. Both uppercase and lowercase
   alpha characters may be used.

Response
--------

**Example Replace all configuration parameters: JSON response**


The following example shows the Replace all configuration parameters response:

.. code::

   HTTP/1.1 202 Accepted
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: 0
   Date: Thu, 13 Feb 2014 21:47:15 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

This operation does not return a response body.
