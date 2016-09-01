
.. _get-list-scheduled-backups-version-accountid-schedules:

List scheduled backups
~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /{version}/{accountId}/schedules

Lists all scheduled backups for all database instances for an account.

This operation returns a list of all scheduled backups for all database
instances for an account.

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+------------------------+
|Response Code             |Name                     |Description             |
+==========================+=========================+========================+
|200                       |Success                  |Request succeeded.      |
+--------------------------+-------------------------+------------------------+
|400                       |Bad Request              |The request is missing  |
|                          |                         |one or more elements, or|
|                          |                         |the values of some      |
|                          |                         |elements are invalid.   |
+--------------------------+-------------------------+------------------------+
|401                       |Unauthorized             |You are not authorized  |
|                          |                         |to complete this        |
|                          |                         |operation. This error   |
|                          |                         |can occur if the request|
|                          |                         |is submitted with an    |
|                          |                         |invalid authentication  |
|                          |                         |token.                  |
+--------------------------+-------------------------+------------------------+
|403                       |Forbidden                |You are denied access to|
|                          |                         |the requested resource. |
+--------------------------+-------------------------+------------------------+
|404                       |Not Found                |The requested item was  |
|                          |                         |not found.              |
+--------------------------+-------------------------+------------------------+
|405                       |badMethod                |The specified method is |
|                          |                         |not allowed for the     |
|                          |                         |given resource.         |
+--------------------------+-------------------------+------------------------+
|413                       |Over Limit               |The number of items     |
|                          |                         |returned is above the   |
|                          |                         |allowed limit.          |
+--------------------------+-------------------------+------------------------+
|422                       |unprocessableEntity      |The item cannot be      |
|                          |                         |processed.              |
+--------------------------+-------------------------+------------------------+
|500                       |instanceFault            |The instance has        |
|                          |                         |experienced a fault.    |
+--------------------------+-------------------------+------------------------+
|501                       |notImplemented           |The server does not     |
|                          |                         |support the             |
|                          |                         |functionality required  |
|                          |                         |to fulfill the request. |
+--------------------------+-------------------------+------------------------+
|503                       |Service Unavailable      |The service is not      |
|                          |                         |available.              |
+--------------------------+-------------------------+------------------------+

Request
-------

This table shows the URI parameters for the request:

+--------------------------+-------------------------+------------------------+
|Name                      |Type                     |Description             |
+==========================+=========================+========================+
|{accountId}               |String                   |The account ID of the   |
|                          |                         |owner of the specified  |
|                          |                         |instance.               |
+--------------------------+-------------------------+------------------------+

This operation does not accept a request body.

**Example List scheduled backups: JSON request**

The following example shows the List scheduled backups request:

.. code::

   GET /v1.0/1234/schedules HTTP/1.1
   User-Agent: python-troveclient
   Host: troveapi.org
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

Response
--------

**Example List scheduled backups: JSON response**

The following example shows the List scheduled backups response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Content-Length: 346
   Date: Mon, 18 Mar 2013 19:09:17 GMT

   {
       "schedules": [
           {
               "action": "backup",
               "created": "2014-10-30T12:30:00",
               "day_of_month": null,
               "day_of_week": 0,
               "hour": 14,
               "id": "2e351a71-dd28-4bcb-a7d6-d36a5b487173",
               "instance_id": "44b277eb-39be-4921-be31-3d61b43651d7",
               "last_scheduled": null,
               "minute": 30,
               "month": null,
               "next_run": "2014-11-02T14:30:00",
               "updated": "2014-10-30T12:30:00"
           }
       ]
   }
