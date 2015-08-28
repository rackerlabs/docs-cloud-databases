
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _api-operations-get-list-datastore-type-version-accountid-datastores-datastoreid:

List datastore type
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /{version}/{accountId}/datastores/{datastoreId}

Lists datastore type.

This operation lists datastore type for the specified datastore.



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
""""""""""""""""




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{accountId}               |String                   |The account ID of the    |
|                          |                         |owner of the specified   |
|                          |                         |instance.                |
+--------------------------+-------------------------+-------------------------+
|{datastoreId}             |String                   |The ID for the specified |
|                          |                         |datastore.               |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




**Example List datastore type: JSON request**


.. code::

    GET /v1.0/1234/datastores/a00000a0-00a0-0a00-00a0-000a000000aa HTTP/1.1
    User-Agent: python-troveclient
    Host: ord.databases.api.rackspacecloud.com
    X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
    Accept: application/json
    Content-Type: application/json
    
    
    


Response
""""""""""""""""










**Example List datastore type: JSON response**


.. code::

    HTTP/1.1 200 OK
    Content-Type: application/json
    Via: 1.1 Repose (Repose/2.6.7)
    Content-Length: 360
    Date: Thu, 13 Feb 2014 21:47:14 GMT
    Server: Jetty(8.0.y.z-SNAPSHOT)
    
    {
        "datastore": {
            "default_version": "7104c15f-ace0-479b-97ad-b368de32cb68",
            "id": "a00000a0-00a0-0a00-00a0-000a000000aa",
            "links": [
                {
                    "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/1234/datastores/a00000a0-00a0-0a00-00a0-000a000000aa",
                    "rel": "self"
                },
                {
                    "href": "https://api.staging.ord1.clouddb.rackspace.net/datastores/a00000a0-00a0-0a00-00a0-000a000000aa",
                    "rel": "bookmark"
                }
            ],
            "name": "mysql",
            "versions": [
                {
                    "id": "b00000b0-00b0-0b00-00b0-000b000000bb",
                    "links": [
                        {
                            "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/1234/datastores/versions/b00000b0-00b0-0b00-00b0-000b000000bb",
                            "rel": "self"
                        },
                        {
                            "href": "https://api.staging.ord1.clouddb.rackspace.net/datastores/versions/b00000b0-00b0-0b00-00b0-000b000000bb",
                            "rel": "bookmark"
                        }
                    ],
                    "name": "5.1"
                },
                {
                    "id": "c00000b0-00c0-0c00-00c0-000b000000cc",
                    "links": [
                        {
                            "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/1234/datastores/versions/c00000b0-00c0-0c00-00c0-000b000000cc",
                            "rel": "self"
                        },
                        {
                            "href": "https://api.staging.ord1.clouddb.rackspace.net/datastores/versions/c00000b0-00c0-0c00-00c0-000b000000cc",
                            "rel": "bookmark"
                        }
                    ],
                    "name": "5.6"
                }
            ]
        }
    }
    
    

