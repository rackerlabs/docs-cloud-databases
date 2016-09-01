
.. _post-convert-replication-setup-to-ha-version-accountid-instances:

Convert replication setup to HA
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /{version}/{accountId}/instances/{instanceId}/action

Converts the replication setup to HA. The specified instance_Id can be the
source or replica ID.

This operation converts the replication setup to HA.

The following table lists the required and optional attributes for Convert
replication setup to HA:

+----------------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------------+
| Name                       | Description                                                                                                             | Required              |
+============================+=========================================================================================================================+=======================+
| name                       | Specifies the name of the HA instance. The length should be limited to 255 characters and any characters are permitted. | Yes                   |
+----------------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------------+
| networks                   | Comma-separated list of networks to be associated with the HA group. For example: {“networks”:[“public”,“servicenet”]}  | No                    |
|                            |                                                                                                                         |                       |
|                            | Notes:                                                                                                                  |                       |
|                            |                                                                                                                         |                       |
|                            | - By default (if not specified), it will be servicenet.                                                                 |                       |
|                            | - If a public network would be required in addition to the servicenet, it would have to be specified in the  option:    |                       |
|                            |   "networks": ["public”]. Note that this will add a public network in addition to a servicenet/private network.         |                       |
|                            | - Both the networks as options: "networks": ["public", "servicenet"], can also be specified.                            |                       |
+----------------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------------+
| acls                       | Comma separated list of IP based ACLs in the CIDR format. This is required to allow the HA group access to the specified| No                    |
|                            | IP. By default, the HA group access is blocked. For eg: "acls": [{"address": "10.0.0.0/0"}, {"address": “1.2.3.4/5”}].  |                       |
|                            | Additionally, if it is not specified while creating the HA group, it can be added later. Refer to                       |                       |
|                            | :ref:`post-add-acls-to-an-ha-instance-version-accountid-ha-haid-acls` for details.                                      |                       |
+----------------------------+-------------------------------------------------------------------------------------------------------------------------+-----------------------+

.. note::

   * By default the replication setup is asynchronous. But for an HA setup, the
     replication setup is changed to **semi-synchronous**.
   * While the source/replicas are being prepared for HA conversion, the
     instances switch to a ``CONVERT_TO_HA`` state.
   * If a source/replica has automated backups enabled, the schedule will be
     converted to an HA group automated backup schedule with the source id set
     to the HA id. The day, hour, and minute settings will be the same as the
     source or replica schedule.
   * **Important**: Once the HA instance is ACTIVE, to be able to switch to
     using the HA cluster, use the new hostname with the appropriate port type
     to connect to the source/replicas as specified in the HA Group details.
     This hostname will remain constant in case of a source failure and replica
     promotion. ACLs will also let you explicitly add an IP that would require
     access to this HA group. For more details for an HA group refer to
     :ref:`high-availability-operations`.

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |Success                  |Request succeeded.       |
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

+--------------------------+-------------------------+--------------------------+
|Name                      |Type                     |Description               |
+==========================+=========================+==========================+
|{accountId}               |String                   |The account ID of the     |
|                          |                         |owner of the specified    |
|                          |                         |instance.                 |
+--------------------------+-------------------------+--------------------------+
|{instanceId}              |String                   |The specified instance_Id,|
|                          |                         |which can be the source   |
|                          |                         |or replica ID.            |
+--------------------------+-------------------------+--------------------------+

**Example Convert replication setup to HA: JSON request**

The following example shows the Convert replication setup to HA request:

.. code::

   POST /v1.0/1234/instances/e0b922ad-a054-40b3-aa3e883201ba79fe/action HTTP/1.1
   User-Agent: python-troveclient
   Host: iad.databases.api.rackspacecloud.com
   X-Auth-Token: e3b2c743aebf467fb6b91cbb644c036e
   Accept: application/json
   Content-Type: application/json


   {
     "convert_to_ha": {
       "acls": [
         {
           "address": "10.0.0.0\/0"
         }
       ],
       "name": "ha-convert-1"
     }
   }

Response
--------

**Example Convert replication setup to HA: JSON response**

The following example shows the Convert replication setup to HA response:

.. code::

   HTTP/1.1 202 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: 697
   Date: Thu, 13 Feb 2014 21:47:17 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)

   {
    "ha_instance": {
        "name": "ha-convert-1",
        "replicas": [
            {
                "status": "ACTIVE",
                "name": "replica-1",
                "links": {},
                "schedule": {
                    "enabled": false
                },
                "hostname": "d95798bb5c9581e8c5d432eecf16aa01e26dc26d.rackspaceclouddb.com",
                "id": "f65bae37-f7ff-42e9-a8dd-0177eb127773",
                "volume": {
                    "size": 1
                },
                "ha_id": "65640327-64dd-4fd0-80b3-1f64e66e0558",
                "flavor": {
                    "id": "2",
                    "links": {}
                },
                "datastore": {
                    "version": "5.6",
                    "type": "mysql"
                },
                "replica_of": {
                    "id": "e0b922ad-a054-40b3-aa3e-883201ba79fe",
                    "links": [
                        {
                            "href": "https://iad.databases.api.rackspacecloud.com/v1.0/938359/instances/e0b922ad-a054-40b3-aa3e-883201ba79fe",
                            "rel": "self"
                        },
                        {
                            "href": "https://iad.databases.api.rackspacecloud.com/instances/e0b922ad-a054-40b3-aa3e-883201ba79fe",
                            "rel": "bookmark"
                        }
                    ]
                }
            }
        ],
        "tenant_id": "938359",
        "replica_source": [
            {
                "status": "ACTIVE",
                "name": "master-1",
                "links": {},
                "replicas": [
                    {
                        "id": "f65bae37-f7ff-42e9-a8dd-0177eb127773",
                        "links": [
                            {
                                "href": "https://iad.databases.api.rackspacecloud.com/v1.0/938359/instances/f65bae37-f7ff-42e9-a8dd-0177eb127773",
                                "rel": "self"
                            },
                            {
                                "href": "https://iad.databases.api.rackspacecloud.com/instances/f65bae37-f7ff-42e9-a8dd-0177eb127773",
                                "rel": "bookmark"
                            }
                        ],
                        "name": "replica-1"
                    }
                ],
                "hostname": "44e777cb84ecd231528e140c05b8bfb09b5e5c72.rackspaceclouddb.com",
                "schedule": {
                    "enabled": false
                },
                "id": "e0b922ad-a054-40b3-aa3e-883201ba79fe",
                "volume": {
                    "size": 1
                },
                "flavor": {
                    "id": "2",
                    "links": {}
                },
                "datastore": {
                    "version": "5.6",
                    "type": "mysql"
                },
                "ha_id": "65640327-64dd-4fd0-80b3-1f64e66e0558"
            }
        ],
        "networks": [],
        "state": "BUILD",
        "acls": [
            {
                "address": "10.0.0.0/0"
            }
        ],
        "datastore": {
            "version": "5.6",
            "type": "mysql"
        },
        "id": "65640327-64dd-4fd0-80b3-1f64e66e0558"
    }
  }

For convenience, notice in the response example above that resources contain
links to themselves. This allows a client to easily obtain resource URIs rather
than to construct them. There are two kinds of link relations associated with
resources. A ``self`` link contains a versioned link to the resource. These
links should be used in cases where the link will be followed immediately. A
``bookmark`` link provides a permanent link to a resource that is appropriate
for long term storage.
