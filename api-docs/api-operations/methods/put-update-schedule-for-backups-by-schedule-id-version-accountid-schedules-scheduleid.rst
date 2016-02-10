
.. _put-update-schedule-for-backups-by-schedule-id-version-accountid-schedules-scheduleid:

Update schedule for backups by schedule ID
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    PUT /{version}/{accountId}/schedules/{scheduleId}

Updates the backup schedule for the specified schedule.

This operation updates the schedule for running backups for the specified schedule.

The following table shows the required and optional attributes for Update schedule for backups by schedule ID.

.. table:: Required and optional attributes for Update schedule for backups by schedule ID

    
    +--------------------------+-------------------------+-------------------------+
    |Name                      |Description              |Required                 |
    +==========================+=========================+=========================+
    |day_of_week               |The day of the week.     |No                       |
    |                          |Sunday is ``0``.         |                         |
    +--------------------------+-------------------------+-------------------------+
    |hour                      |The hour of the day.     |No                       |
    |                          |Midnight is ``0``.       |                         |
    +--------------------------+-------------------------+-------------------------+
    |minute                    |The minute of the hour.  |No                       |
    +--------------------------+-------------------------+-------------------------+
    |run_now                   |Run the backup           |No                       |
    |                          |immediately.             |                         |
    +--------------------------+-------------------------+-------------------------+
    |full_backup_retention     |The number of full       |No                       |
    |                          |automated backups to     |                         |
    |                          |keep.                    |                         |
    +--------------------------+-------------------------+-------------------------+
    



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
|{scheduleId}              |String                   |The schedule ID for the  |
|                          |                         |specified schedule.      |
+--------------------------+-------------------------+-------------------------+








**Example Update schedule for backups by schedule ID: JSON request**


The following example shows the Update backup schedule by schedule ID request:

.. code::

   PUT /v1.0/1234/schedules/2e351a71-dd28-4bcb-a7d6-d36a5b487173 HTTP/1.1
   User-Agent: python-troveclient
   Host: troveapi.org
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json
   
   {
     "schedule": {
       "day_of_week": 2,
       "hour": 6,
       "minute": 19,
       "run_now": "true"
     }
   }





Response
""""""""""""""""










**Example Update schedule for backups by schedule ID: JSON response**


The following example shows the Update backup schedule by schedule ID response:

.. code::

   HTTP/1.1 202 Accepted
   Content-Type: application/json
   Content-Length: 0
   Date: Mon, 18 Mar 2013 19:09:17 GMT
   




