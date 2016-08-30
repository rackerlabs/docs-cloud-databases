.. _cdb-dg-generalapi-dbfaults:

======
Faults
======

When an error occurs, the Database Service returns a fault object containing an
HTTP error response code that denotes the type of error. In the body of the
response, the system will return additional information about the fault.

.. note::
    Cloud Databases uses standard `HTTP 1.1 response codes`_.

The following table lists possible fault types with their associated error
codes and descriptions.

+-----------------------+------------+------------------------------------------------------+
|      Fault Type       | Associated |                     Description                      |
|                       | Error Code |                                                      |
+=======================+============+======================================================+
| ``badRequest``        | 400        | There was one or more errors in the user request.    |
+-----------------------+------------+------------------------------------------------------+
| ``unauthorized``      | 401        | The supplied token is not authorized to access       |
|                       |            | the resources, either it's expired or invalid.       |
+-----------------------+------------+------------------------------------------------------+
| ``forbidden``         | 403        | Access to the requested resource was denied.         |
+-----------------------+------------+------------------------------------------------------+
| ``itemNotFound``      | 404        | The back-end services did not find anything          |
|                       |            | matching the Request-URI.                            |
+-----------------------+------------+------------------------------------------------------+
| ``badMethod``         | 405        | The request method is not allowed for this resource. |
+-----------------------+------------+------------------------------------------------------+
| ``overLimit``         | 413        | Either the number of entities in the request         |
|                       |            | is larger than allowed limits, or the user           |
|                       |            | has exceeded allowable request rate limits.          |
|                       |            | See the ``details`` element for more specifics.      |
|                       |            | Contact support if you think you need                |
|                       |            | higher request rate limits.                          |
+-----------------------+------------+------------------------------------------------------+
| ``badMediaType``      | 415        | The requested content type is not supported by       |
|                       |            | this service.                                        |
+-----------------------+------------+------------------------------------------------------+
|``unprocessableEntity``| 422        | The requested resource could not be processed        |
|                       |            | on at the moment.                                    |
+-----------------------+------------+------------------------------------------------------+
| ``instanceFault``     | 500        | This is a generic server error and the message       |
|                       |            | contains the reason for the error.                   |
|                       |            | This error could wrap several error messages         |
|                       |            | and is a catch-all.                                  |
+-----------------------+------------+------------------------------------------------------+
| ``notImplemented``    | 501        | The requested method or resource is not implemented. |
+-----------------------+------------+------------------------------------------------------+
|``serviceUnavailable`` | 503        | The Database Service is not available.               |
+-----------------------+------------+------------------------------------------------------+

The following ``instanceFault`` example shows errors when the server has erred
or cannot perform the requested operation:

**Example fault response: JSON**

.. code::

    HTTP/1.1 500 Internal Server Error
    Content-Length: 120
    Content-Type: application/json; charset=UTF-8
    Date: Tue, 29 Nov 2011 00:33:48 GMT

    {
        "instanceFault": {
            "code": 500,
            "message": "The server has either erred or is incapable of performing the requested operation."
        }
    }

The error code (``code``) is returned in the body of the response for
convenience. The ``message`` element returns a human-readable message that is
appropriate for display to the end user. The ``details`` element is optional
and may contain information that is useful for tracking down an error, such as
a stack trace. The ``details`` element may or may not be appropriate for
display to an end user, depending on the role and experience of the end user.

The fault's root element (for example, ``instanceFault``) may change depending
on the type of error.

The following ``badRequest`` example shows errors when the volume size is
invalid:

**Example badRequest fault on volume size errors: JSON**

.. code::

    HTTP/1.1 400 None
    Content-Length: 120
    Content-Type: application/json; charset=UTF-8
    Date: Tue, 29 Nov 2011 00:33:48 GMT

    {
        "badRequest": {
            "code": 400,
            "message": "Volume 'size' needs to be a positive integer value, -1.0 cannot be accepted."
        }
    }

The next example shows ``itemNotFound`` errors:

**Example itemNotFound fault: JSON**

.. code::

    HTTP/1.1 404 Not Found
    Content-Length: 78
    Content-Type: application/json; charset=UTF-8
    Date: Tue, 29 Nov 2011 00:35:24 GMT

    {
        "itemNotFound": {
            "code": 404,
            "message": "The resource could not be found."
        }
    }

.. _cdb-dg-generalapi-dbfaults-synch:

Synchronous versus asynchronous faults
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

*Synchronous* faults occur at request time. When a synchronous fault occurs,
the fault contains an HTTP error response code, a human readable message, and
optional details about the error. The following Database API calls are
synchronous and may produce synchronous faults:

-  List Users

-  List Instances

-  List Instance Details by ID

-  List Databases

-  List Backups

-  List Backups by Instance

-  Enable Root User

-  List Root-Enabled Status

-  List Flavors

-  List Versions

-  List Version Details

*Asynchronous* faults occur in the background while an instance, database, or
user is being built or an instance is executing an action. When an asynchronous
fault occurs, the system places the instance, database, or user in an ERROR
state and embeds the fault in the offending instance, database, or user. When
an asynchronous fault occurs, the fault contains an HTTP error response code,
a human readable message, and optional details about the error. The following
Database API calls are asynchronous and may produce asynchronous faults:

-  Create Instance

-  Delete Instance

-  Create Database

-  Delete Database

-  Create User

-  Delete User

-  Resize Volume

-  Resize Instance

-  Restart Instance

..  note::
    Note that an asynchronous operation, if it fails, may not give the user an
    error, and the operation can error out without a failure notification.

.. _HTTP 1.1 response codes: http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html
