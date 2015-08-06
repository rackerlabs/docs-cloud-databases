
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Resize The Instance Volume -  Rackspace Cloud Databases Developer Guide
=============================================================================

Resize The Instance Volume
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <post-resize-the-instance-volume-version-accountid-instances-instanceid-action.html#request>`__
`Response <post-resize-the-instance-volume-version-accountid-instances-instanceid-action.html#response>`__

.. code::

    POST /{version}/{accountId}/instances/{instanceId}/action

Resizes the volume attached to the Instance.

This operation supports resizing the attached volume for an instance. It supports only increasing the volume size and does not support decreasing the size. The volume size is in gigabytes (GB) and must be an integer.

.. note::
   You cannot increase the volume to a size larger than the API volume size limit specifies.
   
   

This operation returns a 202 Accepted response.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |Accepted                 |The request has been     |
|                          |                         |accepted for processing. |
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
|415                       |badMediaType             |The entity of the        |
|                          |                         |request is in a format   |
|                          |                         |not supported by the     |
|                          |                         |requested resource for   |
|                          |                         |the requested method.    |
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








**Example Resize The Instance Volume: JSON request**


.. code::

    POST /v1.0/1234/instances/d4603f69-ec7e-4e9b-803f-600b9205576f/action HTTP/1.1
    User-Agent: python-troveclient
    Host: ord.databases.api.rackspacecloud.com
    X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
    Accept: application/json
    Content-Type: application/json
    
    {
        "resize": {
            "volume": {
                "size": 4
            }
        }
    }
    


Response
^^^^^^^^^^^^^^^^^^





**Example Resize The Instance Volume: JSON response**


.. code::

    HTTP/1.1 202 Accepted
    Content-Type: application/json
    Via: 1.1 Repose (Repose/2.6.7)
    Content-Length: 0
    Date: Thu, 13 Feb 2014 21:47:18 GMT
    Server: Jetty(8.0.y.z-SNAPSHOT)
    

