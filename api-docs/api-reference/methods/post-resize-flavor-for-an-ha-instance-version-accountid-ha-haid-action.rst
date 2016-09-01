
.. _post-resize-flavor-for-an-ha-instance-version-accountid-ha-haid-action:

Resize flavor for an HA instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /{version}/{accountId}/ha/{haId}/action

Resize the flavor of an HA instance specified by {ha_id}.

This operation resizes the volume of an HA instance specified by {ha_id}. For
the duration of this action, the HA instance goes into a ``RESIZING_FLAVOR``
state and switches back to ``ACTIVE`` once the action is complete.

.. warning::

   Resizing the flavor of the HA cluster would restart the MHA manager service
   (which monitors the source/replica instances to trigger failover) and the
   haproxy service on the load balancer nodes. See
   :how-to:`High Availability for Cloud Databases` in the Rackspace  for more
   details about these components.

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
|{haId}                    |String                   |The ID for the specified |
|                          |                         |HA instance.             |
+--------------------------+-------------------------+-------------------------+

**Example Resize flavor for an HA instance: JSON request**

The following example shows the Resize flavor for an HA instance request:

.. code::

   POST /v1.0/1234/ha/bee7680a-b0bd-4edb-9583-fbac6b59a0cd/action HTTP/1.1
   User-Agent: python-troveclient
   Host: iad.databases.api.rackspacecloud.com
   X-Auth-Token: f47d99adabe14bc8bd7bccda88292918
   Accept: application/json
   Content-Type: application/json

   {"resize_flavor": "3"}

Response
--------

**Example Resize flavor for an HA instance: JSON response**

The following example shows the Resize flavor for an HA instance response:

.. code::

   HTTP/1.1 202 Accepted
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.12)
   Content-Length: 0
   Date: Mon, 14 Sep 2015 16:46:48 GMT
   Connection: close
   Server: Jetty(8.0.y.z-SNAPSHOT)
