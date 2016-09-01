.. _list-users-db-instance:

Listing users in a database instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

After you add a database user to an instance, you can use the list users
operation to confirm that the user was successfully created.

You need to specify the ID for the database instance in the API request.
The instance ID is the unique identifier assigned when the database was
created. The following examples use the instance ID from the
:ref:`Create database instance <creating-database-instance-and-user>` examples.

Following are two methods to list users:
 
List users for an instance by using the trove client
----------------------------------------------------

Run the ``database-list`` command with the ID for the database instance:

.. code::

    $ trove user-list <instance_id>

For the instance, the command returns the user name and the databases
that the user can access:

.. code::

    +-------------+------+-----------+
    |     name    | host | databases |
    +-------------+------+-----------+
    | mytroveuser |  %   | mytrovedb |
    +-------------+------+-----------+

List users for an instance by using the trove client
---------------------------------------------------- 

Run the following cURL command to create the instance, replacing
``instance_id`` with the ID for the database instance.

**Example List Users in Database Instance Request cURL request**

.. code::

    curl -s \
         -H "X-Auth-Token: $AUTH_TOKEN" \
         -H "Content-Type: application/json" \
         $API_ENDPOINT/instances/instance_id/users | python -m json.tool

**JSON Response**

.. code::

    HTTP/1.1 200 OK
    Content-Type: application/json
    Content-Length: 113
    Date: Thu, 05 Apr 2012 18:13:53 GMT

    {
      "users": [
          {
              "databases": [
                  {
                      "name": "sampledb"
                  }
              ],
             "host": "%",
             "name": "simplestUser"
          }
      ]
     }
