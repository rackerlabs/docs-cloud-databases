.. _listing flavors:

Listing flavors
~~~~~~~~~~~~~~~

A flavor is an available hardware configuration for a database instance. Each
flavor has a unique combination of memory capacity and priority for CPU time.
The larger the flavor size you use, the larger the amount of RAM and priority
for CPU time your database instance will receive. You can use the list flavors
operation to find the available configurations for your database instance, and
then decide which size you need.

Following are two methods to list flavors:

.. _list-flavors-using-client:

List flavors by using the trove client
--------------------------------------

Run the '`flavor-list`` command from the command line to list available
hardware configuration flavors:

.. code::

     $ trove flavor-list

For each flavor, the command returns the flavor ID, name, and memory:

.. code::

    Flavor List for IAD, DFW, ORD, SYD
   +----+----------------+-------+
   | id |      name      |  ram  |
   +----+----------------+-------+
   | 1  | 512MB Instance |  512  |
   | 2  |  1GB Instance  |  1024 |
   | 3  |  2GB Instance  |  2048 |
   | 4  |  4GB Instance  |  4096 |
   | 5  |  8GB Instance  |  8192 |
   | 6  | 16GB Instance  | 16384 |
   | 7  | 32GB Instance  | 32768 |
   | 8  | 64GB Instance  | 65536 |
   +----+----------------+-------+

The examples in
:ref:`Create a database instance <creating-database-instance-and-user>`
use the flavor ID for the 512MB Standard Instance, which is 1.

.. _list-flavors-using-curl:

List flavors by using the cURL
------------------------------

The following example shows the cURL request and corresponding response to list
flavors.

**Example cURL List Flavors cURL Reques**

.. code::

    curl -s \
         -H "X-Auth-Token: $AUTH_TOKEN" \
         -H "Accept: application/json" \
         $API_ENDPOINT/flavors \
         | python -m json.tool

**JSON response**

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: 1186
   Date: Thu, 13 Feb 2014 21:47:13 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

    {
        "flavors": [
           {
                "id": 1,
                "links": [
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/flavors/1",
                       "rel": "self"
                   },
                    {
                       "href": "https://ord.databases.api.rackspacecloud.com/flavors/1",
                       "rel": "bookmark"
                   }
                ],
               "name": "512MB Instance",
               "ram": 512
            },
            {
                "id": 2,
                "links": [
                    {
                         "href": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/flavors/2",
                         "rel": "self"
                    },
                    {
                        "href": "https://ord.databases.api.rackspacecloud.com/flavors/2",
                        "rel": "bookmark"
                    }
               ],
                "name": "1GB Instance",
                "ram": 1024
           },
           {
                "id": 3,
                "links": [
                   {
                        "href": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/flavors/3",
                        "rel": "self"
                    },
                    {
                       "href": "https://ord.databases.api.rackspacecloud.com/flavors/3",
                        "rel": "bookmark"
                    }
               ],
               "name": "2GB Instance",
               "ram": 2048
           },
           {
                "id": 4,
                "links": [
                   {
                        "href": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/flavors/4",
                        "rel": "self"
                   },
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/flavors/4",
                       "rel": "bookmark"
                    }
               ],
               "name": "4GB Instance",
               "ram": 4096
           },
           {
                "id": 5,
                "links": [
                    {
                        "href": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/flavors/5",
                        "rel": "self"
                   },
                    {
                       "href": "https://ord.databases.api.rackspacecloud.com/flavors/5",
                       "rel": "bookmark"
                    }
               ],
                "name": "8GB Instance",
                "ram": 8192
            },
            {
                "id": 6,
                "links": [
                    {
                       "href": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/flavors/6",
                       "rel": "self"
                   },
                    {
                       "href": "https://ord.databases.api.rackspacecloud.com/flavors/6",
                       "rel": "bookmark"
                   }
               ],
                "name": "16GB Instance",
                "ram": 16384
           },
           {
               "id": 7,
                "links": [
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/v1.0/647683/flavors/7",
                        "rel": "self"
                    },
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/flavors/7",
                       "rel": "bookmark"
                   }
               ],
                "name": "32GB Instance",
                "ram": 32768
            },
            {
                "id": 8,
                "links": [
                   {
                       "href": "https://ord.databases.api.rackspacecloud.com/v1.0/647683/flavors/8",
                       "rel": "self"
                   },
                    {
                        "href": "https://ord.databases.api.rackspacecloud.com/flavors/8",
                        "rel": "bookmark"
                    }
                ],
               "name": "64GB Instance",
               "ram": 65536
            }
        ]
    }


In the response, you can see from the flavor name that there are multiple
flavors available, including 2GB Instance (with 1 virtual CPU and 2 gigabytes
of memory) and 512MB Instance (with 1 virtual CPU and 0.5 gigabytes of memory).

In addition to a flavor ID, the response returns two types of links that can be
used to reference the flavor configuration.

   - The ``self`` links contains a *versioned* link to the flavor resource.
     Use these links in cases where the link is followed immediately
     (as you will see in the next section).

   - The ``bookmark`` links provide a permanent link to each flavor resource.
     You can use the bookmark link for long term storage, and it also works
     across API versions.

The examples in
:ref:`Create a database instance <creating-database-instance-and-user>`
use the flavor ID for the 512MB Standard Instance, which is 1.
