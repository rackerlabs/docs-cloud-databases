
.. _post-resize-the-instance-version-accountid-instances-instanceid-action:

Resize the instance
~~~~~~~~~~~~~~~~~~~

.. code::

    POST /{version}/{accountId}/instances/{instanceId}/action

Resizes the memory of the instance.

This operation changes the memory size of the instance, assuming a valid
flavorRef is provided. Restarts the database service in the process.

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
|415                       |badMediaType             |The entity of the        |
|                          |                         |request is in a format   |
|                          |                         |not supported by the     |
|                          |                         |requested resource for   |
|                          |                         |the requested method.    |
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
|{instanceId}              |String                   |The instance ID for the  |
|                          |                         |specified database       |
|                          |                         |instance.                |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

**Example Resize the instance: JSON request**

The following example shows the Resize instance request:

.. code::

   POST /v1.0/1234/instances/23a3d4fb-3731-497b-afd4-bf25bde2b5fc/action HTTP/1.1
   User-Agent: python-example-client
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 2eeb3252-0164-40f5-8fb7-85df5faa2698
   Accept: application/json
   Content-Type: application/json

   {
       "resize": {
           "flavorRef": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/flavors/2"
       }
   }

Response
--------

**Example Resize the instance: JSON response**

The following example shows the Resize instance response:

.. code::

   HTTP/1.1 202 Accepted
   Content-Type: text/plain; charset=UTF-8
   Content-Length: 58
   Date: Mon, 06 Feb 2012 21:28:10 GMT
