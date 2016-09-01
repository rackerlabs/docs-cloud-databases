.. _manage-tz-cURL:

Managing the time zone with cURL
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. contents::
   :local:
   :depth: 1

This section shows how to use cURL to manage the time zones for
a database instance. You'll learn how to create the configuration group, apply
it to the database, and also how to add custom time zone information to an
existing configuration group.

.. note::
      After updating the settings,
      :ref:`checking the server time zone <check-server-time-zone>` to
      verify that updates were successful.

.. _gs-create-a-config-group-curl:

Create a configuration group (cURL)
-----------------------------------

You can create a configuration group to manage time zones by using the
create configuration operation.

The following example shows the cURL request to create a configuration group
named ``TimeConfig`` that sets the time zone to CST (Central Standard Time).

**Example: Create Configuration Group Request cURL request**

.. code::

    curl -s -d \
    '{
      "configuration": {
        "datastore": {
          "type": "10000000-0000-0000-0000-000000000001",
          "version": "20000000-0000-0000-0000-000000000002"
        },
        "description": "Test config",
        "name": "test-configuration",
        "values": {
          "default_time_zone": "-6:00"
       }
      }
    }' \
   -H "X-Auth-Token: $AUTH_TOKEN" \
   -H "Content-Type: application/json" \
    $API_ENDPOINT/configurations  | python -m json.tool

As an alternative, you could use a named time zone instead of the UTC
offset.

The following example shows the response for Create Configuration Group
Request:
   
**JSON Response**

.. code::

    {
        "configuration": {
           "datastore_version_id": "20000000-0000-0000-0000-000000000002",
            "description": "Test config",
            "id": "63c6e164-2324-4eaa-a3d8-d79528a26e7d",
           "name": "test-configuration",
            "values": {
                "default_time_zone": "-6:00"
           }
       }
   }

In the response, the ``id`` value is a unique identifier assigned to the
configuration group. You need to include this value in configuration group
commands that require it, for example the ``configuration-attach`` command used
to apply the configuration group to a database instance.


Apply the time zone configuration group to an existing database instance (cURL)
-------------------------------------------------------------------------------

You can apply a configuration group to an existing database instance. You need
to include
the ID values for the database instance and configuration group in the command.

The following example shows the cURL request to add an existing configuration
group to a specific
database instance:

**Example: Apply configuration group to a specified database instance cURL request**

.. code::

    curl -i -d \
    '{
      "instance": {
          "configuration": "<config_id>"
      }
   }' \
    -X PUT \
    -H "X-Auth-Token: $AUTH_TOKEN" \
    -H "Content-Type: application/json" \
    $API_ENDPOINT/instances/<instance_id>

Remember to replace the following variables in the example above with
their actual respective values:

-  **config\_id** — as returned in your response to the
   :ref:`create configuration group <gs-create-a-config-group-curl>` operation.

-  **instance\_id** — as returned in your create instance response
   (See the the cURL example in
   :ref:`Create a Database Instance <creating-database-instance-and-user>` .)


If successful, the |apiservice| returns an ``HTTP/1.1 202 Accepted`` response
header to confirm that the settings have been accepted. The operation does not
return a request body.

**JSON response header**

.. code::

    HTTP/1.1 202 Accepted
    Content-Type: application/json
    Via: 1.1 Repose (Repose/2.12)
    Content-Length: 0
    Date: Fri, 02 May 2014 15:18:56 GMT
    Server: Jetty(8.0.y.z-SNAPSHOT)

..  note::

    You need to restart the Cloud Databases instance to apply the new
    configuration settings.
 
Add custom time zone information to an existing configuration group by using cURL
---------------------------------------------------------------------------------

You can update settings in an existing configuration group by using the
update configuration operation. You need to include
the ID value for the configuration group in the command.

The following command shows how to update the ``default_time_zone`` parameter
on an existing configuration group with with id <config\_id> from CST
(Central Standard Time, -6:00) to IST (India Standard Time, +6:00).

**Example: Update default time zone in existing configuration group cURL request**

.. code::

    curl -i -d \
    '{
        "configuration": {
          "values": {
              "default_time_zone": "+6:00"
          }
       }
   }' \
   -X PATCH \
   -H "X-Auth-Token: $AUTH_TOKEN" \
    -H "Content-Type: application/json" \
    $API_ENDPOINT/configurations/<config_id>

If successful, the |apiservice| returns an ``HTTP/1.1 202 Accepted`` response
header to confirm that the settings have been accepted. The operation does not
return a request body.

**JSON response header**

.. code::

       HTTP/1.1 200 OK
       Content-Type: application/json
       Via: 1.1 Repose (Repose/2.12)
       Content-Length: 0
       Date: Fri, 02 May 2014 15:44:43 GMT
       Server: Jetty(8.0.y.z-SNAPSHOT)

After updating the settings,
:ref:`checking the server time zone <check-server-time-zone>` to
verify that updates were successful.
