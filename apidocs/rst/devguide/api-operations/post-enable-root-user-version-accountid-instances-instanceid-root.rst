
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Enable Root User -  Rackspace Cloud Databases Developer Guide
=============================================================================

Enable Root User
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <post-enable-root-user-version-accountid-instances-instanceid-root.html#request>`__
`Response <post-enable-root-user-version-accountid-instances-instanceid-root.html#response>`__

.. code::

    POST /{version}/{accountId}/instances/{instanceId}/root

Enables the root user for the specified database instance and returns the root password.

This operation enables login from any host for the root user and provides the user with a generated root password.



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
|{instanceId}              |xsd:string               |The instance ID for the  |
|                          |                         |specified database       |
|                          |                         |instance.                |
+--------------------------+-------------------------+-------------------------+








**Example Enable Root User: JSON request**


.. code::

    POST /v1.0/1234/instances/d4603f69-ec7e-4e9b-803f-600b9205576f/root HTTP/1.1
    User-Agent: python-troveclient
    Host: ord.databases.api.rackspacecloud.com
    X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
    Accept: application/json
    Content-Type: application/json
    
    
    


Response
^^^^^^^^^^^^^^^^^^





**Example Enable Root User: JSON response**


.. code::

    HTTP/1.1 200 OK
    Content-Type: application/json
    Via: 1.1 Repose (Repose/2.6.7)
    Content-Length: 47
    Date: Thu, 13 Feb 2014 21:47:14 GMT
    Server: Jetty(8.0.y.z-SNAPSHOT)
    
    {
        "user": {
            "name": "root", 
            "password": "12345"
        }
    }
    

