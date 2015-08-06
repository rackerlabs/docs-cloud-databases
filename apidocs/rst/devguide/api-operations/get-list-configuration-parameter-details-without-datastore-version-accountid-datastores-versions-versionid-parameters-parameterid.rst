
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
List Configuration Parameter Details Without Datastore -  Rackspace Cloud Databases Developer Guide
=============================================================================

List Configuration Parameter Details Without Datastore
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-list-configuration-parameter-details-without-datastore-version-accountid-datastores-versions-versionid-parameters-parameterid.html#request>`__
`Response <get-list-configuration-parameter-details-without-datastore-version-accountid-datastores-versions-versionid-parameters-parameterid.html#response>`__

.. code::

    GET /{version}/{accountId}/datastores/versions/{versionId}/parameters/{parameterId}

Lists the details of a specified configuration parameter that may be configured on the system without specifying a datastore.



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
|{versionId}               |xsd:string               |The version for the      |
|                          |                         |specified datastore.     |
+--------------------------+-------------------------+-------------------------+
|{parameterId}             |xsd:string               |The parameter that may   |
|                          |                         |be configured for the    |
|                          |                         |specified datastore and  |
|                          |                         |version.                 |
+--------------------------+-------------------------+-------------------------+








**Example List Configuration Parameter Details Without Datastore: JSON request**


.. code::

    GET /v1.0/1234/datastores/versions/b00000b0-00b0-0b00-00b0-000b000000bb/parameters/innodb_file_per_table HTTP/1.1
    User-Agent: python-troveclient
    Host: ord.databases.api.rackspacecloud.com
    X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
    Accept: application/json
    Content-Type: application/json
    
    
    


Response
^^^^^^^^^^^^^^^^^^





**Example List Configuration Parameter Details Without Datastore: JSON response**


.. code::

    HTTP/1.1 200 OK
    Content-Type: application/json
    Via: 1.1 Repose (Repose/2.6.7)
    Content-Length: 98
    Date: Thu, 13 Feb 2014 21:47:15 GMT
    Server: Jetty(8.0.y.z-SNAPSHOT)
    
    {
        "max": 1, 
        "min": 0, 
        "name": "innodb_file_per_table", 
        "restart_required": true, 
        "type": "integer"
    }
    

