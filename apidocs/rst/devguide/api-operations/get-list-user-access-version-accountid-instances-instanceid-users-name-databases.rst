
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
List User Access -  Rackspace Cloud Databases Developer Guide
=============================================================================

List User Access
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-list-user-access-version-accountid-instances-instanceid-users-name-databases.html#request>`__
`Response <get-list-user-access-version-accountid-instances-instanceid-users-name-databases.html#response>`__

.. code::

    GET /{version}/{accountId}/instances/{instanceId}/users/{name}/databases

Shows a list of all databases a user has access to.

This operation shows a list of all databases a user has access to.



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

+---------------+--------------+-----------------------------------------------+
|Name           |Type          |Description                                    |
+===============+==============+===============================================+
|{accountId}    |xsd:string    |The account ID of the owner of the specified   |
|               |              |instance.                                      |
+---------------+--------------+-----------------------------------------------+
|{instanceId}   |xsd:string    |The instance ID for the specified database     |
|               |              |instance.                                      |
+---------------+--------------+-----------------------------------------------+
|{name}         |xsd:string    |The name for the specified user. Refer to      |
|               |              |`User access restriction by host               |
|               |              |<http://docs.rackspace.com/cdb/api/v1.0/cdb-   |
|               |              |devguide/content/user_access_restrict_by_host- |
|               |              |dle387.html>`__ for details about restricting  |
|               |              |the name to a particular host. Examples:       |
|               |              |testuser, testuser@192.168.1.12 (to restrict   |
|               |              |the user to connecting from a particular host  |
|               |              |IP).                                           |
+---------------+--------------+-----------------------------------------------+








**Example List User Access: JSON request**


.. code::

    GET /v1.0/1234/instances/dcc5c518-73c7-4471-83e1-15fae67a98eb/users/dbuser1/databases HTTP/1.1
    User-Agent: python-reddwarfclient
    Host: ord.databases.api.rackspacecloud.com
    X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
    Accept: application/json
    Content-Type: application/json
    
    
    


**Example List user access for restricted host request: JSON**


.. code::

    GET /v1.0/1234/instances/dcc5c518-73c7-4471-83e1-15fae67a98eb/users/dbuser2%4010%252e0%252e0%252e1/databases HTTP/1.1
    User-Agent: python-reddwarfclient
    Host: ord.databases.api.rackspacecloud.com
    X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
    Accept: application/json
    Content-Type: application/json
    
    
    


Response
^^^^^^^^^^^^^^^^^^





**Example List User Access: JSON response**


.. code::

    HTTP/1.1 200 OK
    Content-Type: application/json
    Via: 1.1 Repose (Repose/2.6.7)
    Content-Length: 38
    Date: Wed, 08 May 2013 22:43:35 GMT
    Server: Jetty(8.0.y.z-SNAPSHOT)
    
    {
        "databases": [
            {
                "name": "databaseE"
            }
        ]
    }
    


**Example List user access for restricted host response: JSON**


.. code::

    HTTP/1.1 200 OK
    Content-Type: application/json
    Via: 1.1 Repose (Repose/2.6.7)
    Content-Length: 61
    Date: Wed, 08 May 2013 22:43:35 GMT
    Server: Jetty(8.0.y.z-SNAPSHOT)
    
    {
        "databases": [
            {
                "name": "databaseB"
            }, 
            {
                "name": "databaseC"
            }
        ]
    }
    

