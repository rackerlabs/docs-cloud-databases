.. _post-restore-backup-version-accountid-instances:

Restore backup
~~~~~~~~~~~~~~

.. code::

    POST /{version}/{accountId}/instances

Creates a new database instance from a backup.

This operation restores a backup onto a new database instance.

The following table lists the required and optional attributes for
RestorePoint:

.. table:: Required and optional attributes for RestorePoint

    +--------------------------+-------------------------+-------------------------+
    |Name                      |Description              |Required                 |
    +==========================+=========================+=========================+
    |backupRef                 |Specifies the id of the  |Yes                      |
    |                          |backup to restore.       |                         |
    +--------------------------+-------------------------+-------------------------+

.. note::


   *  Refer to
      :rax-devdocs:`Create instance <cloud-databases/v1/developer-guide/#create-database-instance>`
      for details on other options available during the creation of a new
      instance.
   *  All users/passwords/access that were on the instance at the time of the
      backup will be restored along with the databases. You can create new
      users or databases if you want, but they cannot be the same as the ones
      from the instance that was backed up.
   *  You can restore from an incremental backup the same as from a full
      backup. The system automatically restores all parents first, and then
      applies the incremental backup.

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
-------

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{accountId}               |String                   |The account ID of the    |
|                          |                         |owner of the specified   |
|                          |                         |instance.                |
+--------------------------+-------------------------+-------------------------+

**Example Restore backup: JSON request**

The following example shows the Restore backup request:

.. code::

   POST /v1.0/1234/instances HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

   {
       "instance": {
           "flavorRef": 1,
           "name": "json_restore",
           "restorePoint": {
               "backupRef": "61f12fef-edb1-4561-8122-e7c00ef26a82"
           },
           "volume": {
               "size": 2
           }
       }
   }

Response
--------

**Example Restore backup: JSON response**

The following example shows the Restore backup response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: 697
   Date: Thu, 13 Feb 2014 21:47:17 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

   {
       "instance": {
           "created": "2014-02-13T21:47:16",
           "datastore": {
               "type": "mysql",
               "version": "5.6"
           },
           "flavor": {
               "id": "1",
               "links": [
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/flavors/1",
                       "rel": "self"
                   },
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/flavors/1",
                       "rel": "bookmark"
                   }
               ]
           },
           "hostname": "e09ad9a3f73309469cf1f43d11e79549caf9acf2.rackspaceclouddb.com",
           "id": "1e9c84df-4443-4f39-9498-5ab7c14a3bb4",
           "links": [
               {
                   "href": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances/1e9c84df-4443-4f39-9498-5ab7c14a3bb4",
                   "rel": "self"
               },
               {
                   "href": "https://ord.databases.api.rackspacecloud.com/instances/1e9c84df-4443-4f39-9498-5ab7c14a3bb4",
                   "rel": "bookmark"
               }
           ],
           "name": "json_restore",
           "status": "BUILD",
           "updated": "2014-02-13T21:47:16",
           "volume": {
               "size": 2
           }
       }
   }
