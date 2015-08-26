
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

Create database
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /{version}/{accountId}/instances/{instanceId}/databases

Creates a new database within the specified instance.

This operation creates a new database within the specified instance.

The ``name`` of the database is a required attribute.

The following additional attributes can be specified for each database: ``collate`` and ``character_set``.

Required and optional attributes for Create databaseName DescriptionRequirednameSpecifies the database name for creating the database. Refer to the request examples for the required json format.Yescharacter_setSet of symbols and encodings. The default character set is ``utf8``.NocollateSet of rules for comparing characters in a character set. The default value for collate is ``utf8_general_ci``.NoSee the database service documentation for information about supported character sets and collations. Refer to `Datastore types and versions <http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/Datastore_Types_and_Versions-d1e9263.html>`__ for references to the documentation for each database service. For example, for MySQL information see `http://dev.mysql.com/doc/refman/5.1/en/charset-mysql.html <http://dev.mysql.com/doc/refman/5.1/en/charset-mysql.html>`__.

.. note::
   The following database names are reserved and cannot be used for creating databases: lost+found, information_schema, and mysql.
   
   

Refer to the following tables for information about characters that are valid/invalid for creating database names.

Valid characters that can be used in a database nameCharacterLetters (upper and lower cases allowed)Numbers'@', '?', '#', and spaces are allowed, but not at the beginning and end of the database name'_' is allowed anywhere in the database nameCharacters that cannot be used in a database nameCharacterSingle quotesDouble quotesBack quotesSemicolonsCommasBackslashesForwardslashesLength restrictions for database nameRestrictionValueDatabase-name maximum length64

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
|{instanceId}              |String                   |The instance ID for the  |
|                          |                         |specified database       |
|                          |                         |instance.                |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




**Example Create database: JSON request**


.. code::

    POST /v1.0/1234/instances/d4603f69-ec7e-4e9b-803f-600b9205576f/databases HTTP/1.1
    User-Agent: python-troveclient
    Host: ord.databases.api.rackspacecloud.com
    X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
    Accept: application/json
    Content-Type: application/json
    
    {
        "databases": [
            {
                "character_set": "utf8", 
                "collate": "utf8_general_ci", 
                "name": "testingdb"
            }, 
            {
                "name": "anotherdb"
            }, 
            {
                "name": "oneMoreDB"
            }
        ]
    }
    


Response
""""""""""""""""







**Example Create database: JSON response**


.. code::

    HTTP/1.1 202 Accepted
    Content-Type: application/json
    Via: 1.1 Repose (Repose/2.6.7)
    Content-Length: 0
    Date: Thu, 13 Feb 2014 21:47:14 GMT
    Server: Jetty(8.0.y.z-SNAPSHOT)
    


