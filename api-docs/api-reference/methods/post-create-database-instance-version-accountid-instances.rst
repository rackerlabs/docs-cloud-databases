
.. _post-create-database-instance-version-accountid-instances:

Create database instance
~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /{version}/{accountId}/instances

Creates a new database instance.

This operation asynchronously provisions a new database instance. This call
requires the user to specify a flavor and a volume size. The service then
provisions the instance with the requested flavor and sets up a volume of the
specified size, which is the storage for the database instance.

.. note::

   *  You can create only one database instance per ``POST`` request.
   *  You can create a database instance with one or more databases, and users
      associated to those databases.
   *  The default binding for the database instance is port 3306.
   *  When used with the ``restorePoint`` attribute, this call performs the
      Restore Backup operation, creating a new database instance to store the
      backup.
   *  For information about using SSL with your database instance, refer to
      :ref:`cdb-dg-generalapi-ssl`.

The following table lists the required and optional attributes for Create
instance:

.. table:: Required and optional attributes for Create instance

    +--------------+--------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+---------+
    |Applies To    |Name                                                                                                          |Description                                                                                                     |Required |
    +==============+==============================================================================================================+================================================================================================================+=========+
    |Instance      |flavorRef                                                                                                     |Reference (href) to a flavor as specified in the response from the List Flavors API call. This is the actual    |Yes      |
    |              |                                                                                                              |URI as specified by the href field in the link. Refer to the List Flavors response examples that follow for an  |         |
    |              |                                                                                                              |example of the flavorRef. Note: Rather than the flavor URI, you can also pass the flavor id (integer) as        |         |
    |              |                                                                                                              |the value for flavorRef. Refer to :rax-devdocs:`List flavors <cloud-databases/v1/developer-guide/#list-flavors>`|         |
    |              |                                                                                                              |for details.                                                                                                    |         |
    |              +--------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+---------+
    |              |(volume) size                                                                                                 |Specifies the volume size in gigabytes (GB). The value specified must be between 1 and 300.                     |Yes      |
    |              +--------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+---------+
    |              |name                                                                                                          |Name of the instance to create. The length of the name is limited to 255 characters and any characters are      |No       |
    |              |                                                                                                              |permitted                                                                                                       |         |
    |              +--------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+---------+
    |              |configuration                                                                                                 |Identifier of the configuration group to associate with the instance.                                           |No       |
    |              +--------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+---------+
    |              |(datastore)                                                                                                   |Name or uuid of the datastore version and type to associate with the instance. If the datastore is not          |No       |
    |              |version / type                                                                                                |specified, it defaults to mysql.                                                                                |         |
    +--------------+--------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+---------+
    |Database      |name                                                                                                          |Specifies database names for creating databases on instance creation. Refer to :rax-devdocs:`Create database    |No       |
    |              |                                                                                                              |<cloud-databases/v1/developer-guide/#create-database>`                                                          |         |
    |              |                                                                                                              |for the required json format.                                                                                   |         |
    |              +--------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+---------+
    |              |character_set                                                                                                 |Set of symbols and encodings. The default character set is ``utf8``.                                            |No       |
    |              +--------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+---------+
    |              |collate                                                                                                       |Set of rules for comparing characters in a character set. The default value for collate is                      |No       |
    |              |                                                                                                              |``utf8_general_ci``.                                                                                            |         |
    +--------------+--------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+---------+
    |User          |name                                                                                                          |Specifies user name for the database on instance creation. Refer to :rax-devdocs:`Create user                   |No       |
    |              |                                                                                                              |<cloud-databases/v1/developer-guide/#create-user>`                                                              |         |
    |              |                                                                                                              |for the required json format.                                                                                   |         |
    |              +--------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+---------+
    |              |password                                                                                                      |Specifies password for those users on instance creation. Refer to :rax-devdocs:`Create user                     |No       |
    |              |                                                                                                              |<cloud-databases/v1/developer-guide/#create-user>`                                                              |         |
    |              |                                                                                                              |for the required json format.                                                                                   |         |
    |              +--------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+---------+
    |              |(database)                                                                                                    |Specifies names of databases that those users can access on instance creation. Refer to                         |No       |
    |              |name                                                                                                          |:rax-devdocs:`Create user <cloud-databases/v1/developer-guide/#create-user>`                                    |         |
    |              |                                                                                                              |for the required json format.                                                                                   |         |
    |              +--------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+---------+
    |              |host                                                                                                          |Specifies the host from which a user is allowed to connect to the database. Possible values are a string        |No       |
    |              |                                                                                                              |containing an IPv4 address or "%" to allow connecting from any host. Refer to :ref:`User access restriction by  |         |
    |              |                                                                                                              |host <cdb-dg-generalapi-security-restriction>` for details.                                                     |         |
    |              |                                                                                                              |If ``host`` is not specified, it defaults to "%".                                                               |         |
    +--------------+--------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+---------+
    |Restore       |restorePoint                                                                                                  |Specifies the backup id from which to restore the database instance. **Note:** When you execute the Restore     |No       |
    |              |                                                                                                              |Backup operation, a new database instance is created to store the backup whose id is specified by the           |         |
    |              |                                                                                                              |``restorePoint`` attribute. All users/passwords/access that were on the instance at the time of the backup      |         |
    |              |                                                                                                              |will be restored along with the databases. You can create new users or databases if you want, but they cannot   |         |
    |              |                                                                                                              |be the same as the ones from the instance that was backed up. Refer to the Create Database Instance Restore     |         |
    |              |                                                                                                              |Request and Response examples for the required json format and details.                                         |         |
    +--------------+--------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+---------+

Refer to :ref:`Database instance status <cdb-dg-generalapi-dbinstance>` for a
list of possible database instance statuses that may be returned.

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

This operation does not accept a request body.

**Example Create database instance: JSON request**

The following example shows the Create database instance request:

.. code::

   POST /v1.0/1234/instances HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json

   {
       "instance": {
           "databases": [
               {
                   "character_set": "utf8",
                   "collate": "utf8_general_ci",
                   "name": "sampledb"
               },
               {
                   "name": "nextround"
               }
           ],
           "flavorRef": 1,
           "name": "json_rack_instance",
           "users": [
               {
                   "databases": [
                       {
                           "name": "sampledb"
                       }
                   ],
                   "name": "demouser",
                   "password": "demopassword"
               }
           ],
           "volume": {
               "size": 2
           }
       }
   }

**Example Create database instance restore request: JSON**

The following example shows the Create database instance restore request:

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

**Example Create database instance configuration request: JSON**

The following example shows the Create database instance configuration request:

.. code::

   {
      "instance": {
          "name": "mysql_instance",
          "flavorRef": "https://endpoint/v1.0/1234/flavors/1",
          "volume": {
              "size": 2
          },
          "configuration": "12345678-1111-2222-3333-444444444444"
      }
   }

**Example Create database instance datastore request: JSON**

The following example shows the Create database instance datastore request:

.. code::

   {
      "instance": {
          "name": "mysql_instance",
          "flavorRef": "https://endpoint/v1.0/1234/flavors/1",
          "volume": {
              "size": 2
          },
          "datastore": {
              "version": "5.1",
              "type": "MySQL"
          }
      }
   }

Response
--------

**Example Create database instance: JSON response**

The following example shows the Create database instance response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: 703
   Date: Thu, 13 Feb 2014 21:47:13 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

   {
       "instance": {
           "created": "2014-02-13T21:47:13",
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
           "id": "d4603f69-ec7e-4e9b-803f-600b9205576f",
           "links": [
               {
                   "href": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances/d4603f69-ec7e-4e9b-803f-600b9205576f",
                   "rel": "self"
               },
               {
                   "href": "https://ord.databases.api.rackspacecloud.com/instances/d4603f69-ec7e-4e9b-803f-600b9205576f",
                   "rel": "bookmark"
               }
           ],
           "name": "json_rack_instance",
           "status": "BUILD",
           "updated": "2014-02-13T21:47:13",
           "volume": {
               "size": 2
           }
       }
   }

For convenience, notice in the response examples above that resources contain
links to themselves. This allows a client to easily obtain resource URIs rather
than to construct them. There are two kinds of link relations associated with
resources. A ``self`` link contains a versioned link to the resource. These
links should be used in cases where the link will be followed immediately. A
``bookmark`` link provides a permanent link to a resource that is appropriate
for long term storage.

**Example Create database instance restore response: JSON**

The following example shows the Create database instance restore response:

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

**Example Create database instance config response: JSON**

The following example shows the Create database instance configuration response:

.. code::

   {
      "instance": {
          "created": "2012-01-25T21:53:09Z",
          "flavor": {
              "id": "1",
              "links": [
                  {
                      "href": "https://endpoint/v1.0/1234/flavors/1",
                      "rel": "self"
                  },
                  {
                      "href": "https://endpoint/flavors/1",
                      "rel": "bookmark"
                  }
              ]
          },
          "configuration": {
             "id": "12345678-1111-2222-3333-444444444444",
             "name": "MySQL Tuned Config",
             "links": [
                 {
                     "href": "https://endpoint/v1.0/1234/configurations/12345678-1111-2222-3333-444444444444",
                     "rel": "self"
                 },
                 {
                     "href": "https://endpoint/configurations/12345678-1111-2222-3333-444444444444",
                     "rel": "bookmark"
                 }
             ]
         },
          "hostname": "e09ad9a3f73309469cf1f43d11e79549caf9acf2.hostname",
          "id": "dea5a2f7-3ec7-4496-adab-0abb5a42d635",
          "links": [
              {
                  "href": "https://endpoint/v1.0/1234/instances/dea5a2f7-3ec7-4496-adab-0abb5a42d635",
                  "rel": "self"
              },
              {
                  "href": "https://endpoint/instances/dea5a2f7-3ec7-4496-adab-0abb5a42d635",
                  "rel": "bookmark"
              }
          ],
          "name": "json_rack_instance",
          "status": "BUILD",
          "updated": "2012-01-25T21:53:10Z",
          "volume": {
              "size": 2
          }
      }
   }

Notice in the response example above the configuration named "MySQL Tuned
Config" is returned in the response.

**Example Create database instance datastore response: JSON**

The following example shows the Create database instance datastore response:

.. code::

   {
      "instance": {
          "created": "2012-01-25T21:53:09Z",
          "flavor": {
              "id": "1",
              "links": [
                  {
                      "href": "https://endpoint/v1.0/1234/flavors/1",
                      "rel": "self"
                  },
                  {
                      "href": "https://endpoint/flavors/1",
                      "rel": "bookmark"
                  }
              ]
          },
          "datastore": {
              "version": "5.1",
              "type": "MySQL"
          },
          "hostname": "e09ad9a3f73309469cf1f43d11e79549caf9acf2.hostname",
          "id": "dea5a2f7-3ec7-4496-adab-0abb5a42d635",
          "links": [
              {
                  "href": "https://endpoint/v1.0/1234/instances/dea5a2f7-3ec7-4496-adab-0abb5a42d635",
                  "rel": "self"
              },
              {
                  "href": "https://endpoint/instances/dea5a2f7-3ec7-4496-adab-0abb5a42d635",
                  "rel": "bookmark"
              }
          ],
          "name": "json_rack_instance",
          "status": "BUILD",
          "updated": "2012-01-25T21:53:10Z",
          "volume": {
              "size": 2
          }
      }
   }
