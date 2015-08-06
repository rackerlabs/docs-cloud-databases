
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Update Database Instance -  Rackspace Cloud Databases Developer Guide
=============================================================================

Update Database Instance
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <put-update-database-instance-version-accountid-instances-instanceid.html#request>`__
`Response <put-update-database-instance-version-accountid-instances-instanceid.html#response>`__

.. code::

    PUT /{version}/{accountId}/instances/{instanceId}

Associates a specified database instance with a configuration group.

This operation associates a specified database instance with a configuration group.

Reviewer: should the description note that this can be used for attaching or detaching configurations from an instance?

.. note::
   If any of the parameters in the configuration require a restart, then you will need to reboot the Database instance after associating the configuration. You can call the API operation List Configuration Parameters to find out which of the configuration parameters require a restart.
   
   



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








**Example Update Database Instance: JSON request**


.. code::

    PUT /v1.0/1234/instances/d4603f69-ec7e-4e9b-803f-600b9205576f HTTP/1.1
    User-Agent: python-troveclient
    Host: ord.databases.api.rackspacecloud.com
    X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
    Accept: application/json
    Content-Type: application/json
    
    {
        "instance": {
            "configuration": ""
        }
    }
    


Response
^^^^^^^^^^^^^^^^^^





**Example Update Database Instance: JSON response**


.. code::

    HTTP/1.1 202 Accepted
    Content-Type: application/json
    Via: 1.1 Repose (Repose/2.6.7)
    Content-Length: 0
    Date: Thu, 13 Feb 2014 21:47:15 GMT
    Server: Jetty(8.0.y.z-SNAPSHOT)
    

