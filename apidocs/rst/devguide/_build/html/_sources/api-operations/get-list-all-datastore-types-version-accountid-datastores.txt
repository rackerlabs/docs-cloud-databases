
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-list-all-datastore-types-version-accountid-datastores:

List all datastore types
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /{version}/{accountId}/datastores

Lists all datastore types.

This operation lists all datastore types.



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





This operation does not accept a request body.




**Example List all datastore types: JSON request**


The following example shows the List all datastore types request:

.. code::

   GET /v1.0/1234/datastores HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json
   
   
   





Response
""""""""""""""""










**Example List all datastore types: JSON response**


The following example shows the List all datastore types response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: 957
   Date: Thu, 13 Feb 2014 21:47:14 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)
   
   
   
   {
       "datastores": [
           {
               "default_version": "c00000b0-00c0-0c00-00c0-000b000000cc",
               "id": "10000000-0000-0000-0000-000000000001", 
               "links": [
                   {
                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/1234/datastores/10000000-0000-0000-0000-000000000001", 
                       "rel": "self"
                   }, 
                   {
                       "href": "https://api.staging.ord1.clouddb.rackspace.net/datastores/10000000-0000-0000-0000-000000000001", 
                       "rel": "bookmark"
                   }
               ], 
               "name": "mysql", 
               "versions": [
                   {
                       "ha_supported": false,
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
                       "name": "5.1",
                       "replication_supported": false
                   }, 
                   {
                       "ha_supported": true,
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
                       "name": "5.6",
                       "replication_supported": true
                   }
               ]
           }, 
           {
               "default_version": "e8b1ee46-58c9-459e-bb02-50ddc8844be7", 
               "id": "17e9bb89-0dce-476d-b785-0c8485f932c0", 
               "links": [
                   {
                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/1234/datastores/17e9bb89-0dce-476d-b785-0c8485f932c0", 
                       "rel": "self"
                   }, 
                   {
                       "href": "https://api.staging.ord1.clouddb.rackspace.net/datastores/17e9bb89-0dce-476d-b785-0c8485f932c0", 
                       "rel": "bookmark"
                   }
               ], 
               "name": "percona", 
               "versions": [
                   {
                       "ha_supported": true,
                       "id": "e8b1ee46-58c9-459e-bb02-50ddc8844be7", 
                       "links": [
                           {
                               "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/1234/datastores/versions/e8b1ee46-58c9-459e-bb02-50ddc8844be7", 
                               "rel": "self"
                           }, 
                           {
                               "href": "https://api.staging.ord1.clouddb.rackspace.net/datastores/versions/e8b1ee46-58c9-459e-bb02-50ddc8844be7", 
                               "rel": "bookmark"
                           }
                       ], 
                       "name": "5.6",
                       "replication_supported": true
                   }
               ]
           }, 
           {
               "default_version": "bf414e62-0e66-4e0f-9b76-05d7408eb140", 
               "id": "a87786d5-879d-4680-a98c-684122bd7cce", 
               "links": [
                   {
                       "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/1234/datastores/a87786d5-879d-4680-a98c-684122bd7cce", 
                       "rel": "self"
                   }, 
                   {
                       "href": "https://api.staging.ord1.clouddb.rackspace.net/datastores/a87786d5-879d-4680-a98c-684122bd7cce", 
                       "rel": "bookmark"
                   }
               ], 
               "name": "mariadb", 
               "versions": [
                   {
                       "ha_supported": true,
                       "id": "53e8fe38-c18d-47d8-9d9e-2ba09a57ae6c", 
                       "links": [
                           {
                               "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/1234/datastores/versions/53e8fe38-c18d-47d8-9d9e-2ba09a57ae6c", 
                               "rel": "self"
                           }, 
                           {
                               "href": "https://api.staging.ord1.clouddb.rackspace.net/datastores/versions/53e8fe38-c18d-47d8-9d9e-2ba09a57ae6c", 
                               "rel": "bookmark"
                           }
                       ], 
                       "name": "10.0",
                       "replication_supported" true
                   }, 
                   {
                       "id": "bf414e62-0e66-4e0f-9b76-05d7408eb140", 
                       "links": [
                           {
                               "href": "https://api.staging.ord1.clouddb.rackspace.net/v1.0/1234/datastores/versions/bf414e62-0e66-4e0f-9b76-05d7408eb140", 
                               "rel": "self"
                           }, 
                           {
                               "href": "https://api.staging.ord1.clouddb.rackspace.net/datastores/versions/bf414e62-0e66-4e0f-9b76-05d7408eb140", 
                               "rel": "bookmark"
                           }
                       ], 
                       "name": "10"
                   }
               ]
           }
       ]
   }




