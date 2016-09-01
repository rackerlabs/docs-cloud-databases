.. _creating-database-instance-and-user:

Creating a database instance, database, and a user
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

A database instance is an isolated database environment with compute and
storage resources in a single tenant environment on a shared physical
host machine.

You can run a database instance with one of the following database engines:
MySQL, Percona, or MariaDB.  For details, see
:ref:`Database types and versions <cdb-dg-generalapi-datastore>`.

The instance created by running the commands in the following examples,  uses
the 512MB Instance flavor and a volume size of 2 gigabytes (GB).

..  note::
      - For the SYD and HKG datacenters only, the default database is MySQL 5.1
        if users do not specify the datastore type and version at instance
        creation.

      - For information about database naming restrictions, see
        :ref:`Create a database <post-create-database-version-accountid-instances-instanceid-databases>`.

      - Note that it can take several minutes to create the database. You
        cannot send requests to get information about the database until the
        database instance status is ``ACTIVE``.

Following are two methods for creating a database instance:

.. _create-database-by-using-trove:

Create a database instance by using the trove client
----------------------------------------------------

The following example creates a MySQL database instance ``mytroveinstance``,
with the following configuration and user settings:

-  the 512MB Instance flavor

-  volume size of 2 gigabytes (GB)

-  a database named ``mytrovedb``

-  a user ``mytroveuser`` with password ``password``

Run the ``create`` command with parameters to provision the database instance,
and create the database and database user:


.. code::

    $ trove create --size 2 --databases mytrovedb --users mytroveuser:password --datastore MySQL mytroveinstance 1

..  note::

     If you want to create a different database and version, use the
     ``--datastore`` and ``--datastore_version`` parameters to specify your
     choice. For example, to specify a Percona 5.6 database, run the following
     command.

     .. code::

        $ trove create --size 2 --databases mytrovedb --users mytroveuser:password --datastore Percona --datastore_version 5.6 mytroveinstance 1


When the instance is created, the command returns the date created, flavor ID,
hostname, id, name, status, and volume size as shown in the following example.

.. code::

    +-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
    |      Property     |                                                                                                          Value                                                                                                          |
    +-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
    |      created      |                                                                                                   2014-04-29T13:33:51                                                                                                   |
    |     datastore     |                                                                                         {u'version': u'5.6', u'type': u'MySQL'}                                                                                         |
    | datastore_version |                                                                                                           5.6                                                                                                           |
    |       flavor      | {u'id': u'1', u'links': [{u'href': u'https://dfw.databases.api.rackspacecloud.com/v1.0/647683/flavors/1', u'rel': u'self'}, {u'href': u'https://dfw.databases.api.rackspacecloud.com/flavors/1', u'rel': u'bookmark'}]} |
    |      hostname     |                                                                              9175290275ef3292efb02be33dd38ed44443e311.rackspaceclouddb.com                                                                              |
    |         id        |                                                                                           18d48a36-0682-4cd7-a419-864105d6079a                                                                                          |
    |        name       |                                                                                                     mytroveinstance                                                                                                     |
    |       status      |                                                                                                          BUILD                                                                                                          |
    |      updated      |                                                                                                   2014-04-29T13:33:51                                                                                                   |
    |       volume      |                                                                                                       {u'size': 2}                                                                                                      |
    +-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

The includes an instance ID value,``id="18d48a36-0682-4cd7-a419-864105d6079a``
which is the unique ID for the database instance.  You need this ID to make
subsequent requests that require it like the list databases for an instance
operation.

.. _create-db-instance-by-using-curl:

Create a database instance by using cURL
----------------------------------------

The following example creates a MySQL database instance ``myrackinstance``,
with the following configuration and user settings:

   -  the 512MB Instance flavor

   -  volume size of 2 gigabytes (GB)

   -  a database named ``sampledb`` with:

      -  ``utf8`` character set

      -  ``utf8_general_ci`` collation

   -  a user ``simplestUser`` with password ``password``

If you want to create a different database and version, use the
``datastore`` ``version`` and ``type`` parameters to specify your
choice. For example, to specify a Percona 5.6 database, include the
following information in the ``flavorRev`` section of the cURL request.

     .. code::

          "datastore": {
              "version": "5.6",
              "type": "Percona"
          },

Submit the following cURL request to create the instance:

**Example Create Instance cURL request**

.. code::

    curl -s -d \
    '{
        "instance": {
            "databases": [
               {
                   "character_set": "utf8",
                   "collate": "utf8_general_ci",
                    "name": "sampledb"
                }
            ],
            "flavorRef": "https://ord.databases.api.rackspacecloud.com/v1.0/$account/flavors/1",
            "name": "myrackinstance",
            "users": [
                {
                    "databases": [
                        {
                            "name": "sampledb"
                        }
                    ],
                "name": "simplestUser",
                "password": "password"
                }
            ],
            "volume":
                {
                    "size": 2
                }
        }
   }' \
    -H "X-Auth-Token: $AUTH_TOKEN" \
    -H "Content-Type: application/json" \
    $API_ENDPOINT/instances | python -m json.tool

.. note::

    Rather than the ``flavorRef URI`` shown in the example, you can also pass
    the flavor id (integer) as the value for flavorRef. For example, the flavor
    id for the flavor URI shown above is "1". The flavorRef URI reference is
    returned in the href self link field of the list flavors operation
    response.
        
**JSON response**

.. code::

    HTTP/1.1 200 OK
    Content-Type: application/json
    Content-Length: 756
    Date: Thu, 05 Apr 2012 16:48:44 GMT

    {
        "instance": {
            "status": "BUILD",
            "updated": "2012-04-05T16:48:44Z",
            "name": "myrackinstance",
            "links": [
                {
                   "href": "http://ord.databases.api.rackspacecloud.com/v1.0/1234/instances/d379ba5c-9a1f-4aa9-9a17-afe237d04c65",
                   "rel": "self"
               },
                {
                    "href": "http://ord.databases.api.rackspacecloud.com/instances/d379ba5c-9a1f-4aa9-9a17-afe237d04c65",
                    "rel": "bookmark"
               }
            ],
            "created": "2012-04-05T16:48:44Z",
            "datastore": {
               "type": "mysql",
                "version": "5.6"
            },
            "hostname": "ca9fa2985e47b351915c75f1a8e95d0729068892.rackspaceclouddb.com",
             "volume": {
                "size": 2
            },
            "flavor": {
                "id": "1",
                "links": [
                    {
                       "href": "http://ord.databases.api.rackspacecloud.com/v1.0/1234/flavors/1",
                        "rel": "self"
                   },
                    {   "href": "http://ord.databases.api.rackspacecloud.com/flavors/1",
                        "rel": "bookmark"
                   }
                ]
              },
              "id": "d379ba5c-9a1f-4aa9-9a17-afe237d04c65"
           }
    }

You will need to specify the instance id returned (in the response
examples above: ``id="d379ba5c-9a1f-4aa9-9a17-afe237d04c65"``) on
subsequent API calls that require it, for example List Databases for
Instance.
