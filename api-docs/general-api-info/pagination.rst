.. _cdb-dg-generalapi-pagination:

==========
Pagination
==========

Pagination provides the ability to limit the size of the returned data in the
response body as well as retrieve a specified subset of a large data set.
Pagination has two key concepts: *limit* and *marker*.

-  *Limit* is the restriction on the maximum number of items for that type
   that can be returned.

-  *Marker* is the ID of the last item in the previous list returned.

   The ID is the UUID in the case of instances, the name in the case of
   databases, and "*name@host*" for users. For example, a query could request
   the next 10 instances after the instance "1234" as follows:

        ?limit=10&marker=1234

   Items are displayed sorted by ID.

If the content returned by a call is paginated, the response includes a
structured link much like an instance item's links, with the basic structure
`{"href": "<url>", "rel": "next"}`. Any response that is truncated by
pagination will have a *next* link, which points to the next item in the
collection. If there are no more items, no *next* link is returned.

Pagination applies only to the calls listed in the following table:

+---------+-----------------------------------+--------------------------------------------------------------+
|  Verb   |                URI                |                         Description                          |
+=========+===================================+==============================================================+
| **GET** | /instances/                       | Lists the status and information for all database instances. |
+---------+-----------------------------------+--------------------------------------------------------------+
| **GET** | /instances/{instanceId}/databases | Lists databases for the specified instance.                  |
+---------+-----------------------------------+--------------------------------------------------------------+
| **GET** | /instances/{instanceId}/users     | Lists the users in the specified database instance.          |
+---------+-----------------------------------+--------------------------------------------------------------+

Cloud Databases has separate paging limits for instances (20), databases (100),
users (20), and backups (20), with the default limit for each set to the paging
limit. If a request supplies no limit or one that exceeds the configured
default limit, the default is used instead.

See the example of paged List Instances calls that follow.

**Example: List instances paged request: JSON**

.. code::

    GET /v1.0/1234/instances?limit=2 HTTP/1.1
    User-Agent: python-troveclient
    Host: ord.databases.api.rackspacecloud.com
    X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
    Accept: application/json
    Content-Type: application/json

Notice that the paged request example above sets the limit to 2 (``?limit=2``),
so the responses that follow each show 2 instances and return a *marker* set to
the UUID of the last item in the returned list
(``?marker=d4603f69-ec7e-4e9b-803f-600b9205576f``). Also a link is provided to
retrieve the next 2 results (``limit=2``) in the link element identified by the
attribute ``"rel":"next"``:

**Example: List instances paged response: JSON**

.. code::

    HTTP/1.1 200 OK
    Content-Type: application/json
    Via: 1.1 Repose (Repose/2.6.7)
    Content-Length: 1237
    Date: Thu, 13 Feb 2014 21:47:16 GMT
    Server: Jetty(8.0.y.z-SNAPSHOT)

    {
        "instances": [
            {
                "datastore": {
                    "type": "mysql"
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
                "id": "4bf79039-dc7f-49c3-a285-03e1ad1e6cbf",
                "links": [
                    {
                        "href": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances/4bf79039-dc7f-49c3-a285-03e1ad1e6cbf",
                        "rel": "self"
                    },
                    {
                        "href": "https://ord.databases.api.rackspacecloud.com/instances/4bf79039-dc7f-49c3-a285-03e1ad1e6cbf",
                        "rel": "bookmark"
                    }
                ],
                "name": "The Third Instance",
                "status": "ACTIVE",
                "volume": {
                    "size": 2
                }
            },
            {
                "datastore": {
                    "type": "mysql"
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
                "status": "ACTIVE",
                "volume": {
                    "size": 2
                }
            }
        ],
        "links": [
            {
                "href": "https://ord.databases.api.rackspacecloud.com/v1.0/1234/instances?marker=d4603f69-ec7e-4e9b-803f-600b9205576f&limit=2",
                "rel": "next"
            }
        ]
    }
