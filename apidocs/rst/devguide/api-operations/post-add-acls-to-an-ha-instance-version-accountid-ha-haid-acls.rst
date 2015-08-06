
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Add Acls To An Ha Instance -  Rackspace Cloud Databases Developer Guide
=============================================================================

Add Acls To An Ha Instance
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <post-add-acls-to-an-ha-instance-version-accountid-ha-haid-acls.html#request>`__
`Response <post-add-acls-to-an-ha-instance-version-accountid-ha-haid-acls.html#response>`__

.. code::

    POST /{version}/{accountId}/ha/{haId}/acls

Adds Access Control Lists (ACLs) to an HA instance.

This operation adds ACLs to an HA instance.

The following table lists the required and optional attributes for creating ACLs for an HA setup.

Required and optional attributes for Create databaseName DescriptionRequiredaddressSpecifies the CIDR notated IPV4 address. The IPV4 address to use should be CIDR notated.Yes

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
|404                       |Not Found                |The requested item was   |
|                          |                         |not found.               |
+--------------------------+-------------------------+-------------------------+


Request
^^^^^^^^^^^^^^^^^

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{accountId}               |xsd:string               |The account ID of the    |
|                          |                         |owner of the specified   |
|                          |                         |instance.                |
+--------------------------+-------------------------+-------------------------+
|{haId}                    |xsd:string               |The ID for the specified |
|                          |                         |HA instance.             |
+--------------------------+-------------------------+-------------------------+








**Example Add Acls To An Ha Instance: JSON request**


.. code::

    POST /v1.0/1234/ha/e7fdf90b-7140-4edb-b449-e093d55008fb/acls HTTP/1.1
    User-Agent: python-troveclient
    Host: ord.databases.api.rackspacecloud.com
    X-Auth-Token: f47d99adabe14bc8bd7bccda88292918
    Accept: application/json
    Content-Type: application/json
    
    {"address": "1.2.3.4/32"}
    


Response
^^^^^^^^^^^^^^^^^^





**Example Add Acls To An Ha Instance: JSON response**


.. code::

    HTTP/1.1 200 OK
    Content-Type: application/json
    Via: 1.1 Repose (Repose/2.12)
    Content-Length: 0
    Date: Fri, 08 May 2015 19:25:15 GMT
    Connection: close
    Server: Jetty(8.0.y.z-SNAPSHOT)
    

