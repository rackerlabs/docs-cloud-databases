.. _backup-dbinstance-client:

Backing up by using the trove client
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can back up a database instance by using the
**backup-create** command. You need to include the
ID for the database instance and supply a name for the backup.

You can also include an optional backup description, enclosed in
double quotation marks, for example ``"backup for my favorite database"``

The following example creates a back up of the ``mytroveinstance`` database
created by the example in
:ref:`Create a Database Instance <creating-database-instance-and-user>` .

Run the ``backup-create`` command to back up a database instance.

.. code::

    $ trove backup-create <instance_id> <name> --description <description>

The command returns the name and id for the backup among the other
information:

.. code::

    +-------------+--------------------------------------+
    |   Property  |                Value                 |
    +-------------+--------------------------------------+
    |   created   |         2014-04-29T13:53:08          |
    | description |         sample trove backup          |
    |      id     | dcb64318-ddca-452e-a896-02cecc5c0aa1 |
    | instance_id | 18d48a36-0682-4cd7-a419-864105d6079a |
    | locationRef |                 None                 |
    |     name    |            mytrovebackup             |
    |  parent_id  |                 None                 |
    |     size    |                 None                 |
    |    status   |                 NEW                  |
    |   updated   |         2014-04-29T13:53:08          |
    +-------------+--------------------------------------+

.. _backup-dbinstance-curl:

Backing up by using cURL
------------------------

The following example shows the cURL request to backup data for a specified
database instance. You need to include the ID for the database instance in the
request.

This operation does not require a request body.
    
**Example Backup Database Instance cURL request**

.. code::

    curl -s -d \
    '{
      "backup": {
          "description": "<backup_description>",
          "instance": "<instance_id>",
          "name": "<backup_name>"
      }
    }' \
    -H "X-Auth-Token: $AUTH_TOKEN" \
    -H "Content-Type: application/json" \
    $API_ENDPOINT/backups | python -m json.tool

Remember to replace the names in the example above with their actual
respective values:

-  **backup\_description** — description for the backup

-  **instance\_id** — as returned in your create instance response
   (See the the cURL example in
   :ref:`Create a Database Instance <creating-database-instance-and-user>`.)

-  **backup\_name** — name of the backup

The following example shows a successful response for the back up database
request.
    
**JSON response**

.. code::

    HTTP/1.1 202 Accepted
    Content-Type: application/json
    Via: 1.1 Repose (Repose/2.6.7)
    Content-Length: 267
    Date: Thu, 27 Jun 2013 19:47:55 GMT
    Server: Jetty(8.0.y.z-SNAPSHOT)

    {
        "backup": {
            "created": "2013-06-27T19:47:55",
            "description": "My Backup",
            "id": "8c40f9c2-6fe8-4b6b-a823-8a6b1d181f09",
            "instance_id": "f07ac506-1a99-4a2a-9a32-869b453019ef",
            "locationRef": null,
            "name": "snapshot",
               "status": "NEW",
               "updated": "2013-06-27T19:47:55"
        }
    }

You can see that the backups were successfully created.
