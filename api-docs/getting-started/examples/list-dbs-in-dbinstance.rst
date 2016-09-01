.. _list-dbs-in-instance:

Listing databases for an instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

After you add a database to an instance, you can use the list databases
operation to confirm that it was successfully created.

You need to specify the ID for the database instance in the API request.
The instance ID is the unique identifier assigned when the database was
created. The following examples use the instance ID from the
:ref:`Create database instance <creating-database-instance-and-user>` examples.

Following are two methods for listing database instances:

Listing database instances by using the trove client
----------------------------------------------------
 
Run the ``database-list`` command with ID for the database instance:

.. code::

     $ trove database-list <instance_id>

The command returns the database name(s) for the instance:

.. code::

    +-----------+
    |    name   |
    +-----------+
    | mytrovedb |
    +-----------+

Listing database instances by using cURL
----------------------------------------

Run the following cURL command to create the instance, replacing
``instance_id`` with the ID for the database instance.

**Example List Databases for Instance Request cURLN**

.. code::

    curl -s \
         -H "X-Auth-Token: $AUTH_TOKEN" \
         -H "Content-Type: application/json" \
          $API_ENDPOINT/instances/instance_id/databases | python -m json.tool

**JSON response**

.. code::

     HTTP/1.1 200 OK
     Content-Type: application/json
     Content-Length: 37
     Date: Thu, 05 Apr 2012 18:13:53 GMT

     {
       "databases": [
         {
           "name": "sampledb"
         }
       ]
     }
