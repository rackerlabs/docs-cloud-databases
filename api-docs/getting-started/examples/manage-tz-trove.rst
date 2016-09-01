.. _manage-tz-trove:

Managing time zones by using the trove client
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. contents::
   :local:
   :depth: 1

This section shows how to use trove client commands to manage the time zones
for a database instance. You'll learn how to create the configuration group,
apply it to the database, and also how to add custom time zone information to
an existing configuration group.

.. note::
      After updating the settings,
      :ref:`check the server time <check-server-time-zone>` to
      verify that updates were successful.

.. _gs-create-a-config-group-client:

Create a configuration group
----------------------------

The following example creates a configuration group
named ``TimeConfig`` that sets the time zone to CST (Central Standard Time).

Run the following ``configuration-create`` trove client command with group name
and time zone values:

.. code::

    $ trove configuration-create TimeConfig '{"default_time_zone":"-6:00"}' --datastore MySQL

The command returns the id and name for the configuration group among
the other information:

.. code::

    +----------------------+--------------------------------------+
    |       Property       |                Value                 |
    +----------------------+--------------------------------------+
    | datastore_version_id | 20000000-0000-0000-0000-000000000002 |
    |     description      |                 None                 |
    |          id          | 00f6070d-27f1-4af2-8388-4cae33899c0c |
    |         name         |              TimeConfig              |
    |        values        |    {"default_time_zone": "-6:00"}    |
    +----------------------+--------------------------------------+

As an alternative, you could use a named time zone instead of the UTC
offset.

In the response, the ``id`` value is a unique identifier assigned to the
configuration group. You need to include this value in configuration group
client commands that require it, for example the ``configuration-attach``
command used to apply the configuration group to a database instance.

Apply the time zone configuration group to an existing database instance
------------------------------------------------------------------------

You can apply a configuration group to an existing database instance. You need
to include the ID values for the database instance and configuration group in
the command.

Run the following ``configuration-attach`` trove client command to apply the
configuration group.

.. code::

    $ trove configuration-attach <config_id> <instance_id>

Remember to replace the variables in the example above with their
actual respective values:

-  **config\_id** — as returned in your response to the
   :ref:`create configuration command <gs-create-a-config-group-client>` .

-  **instance\_id** — as returned in your create instance response
   (See the the client example in
   :ref:`Create a Database Instance <creating-database-instance-and-user>` .)

The ``configuration-attach`` command does not return any output.

..  note::

    You need to restart the Cloud Databases instance to apply the new
    configuration settings.

Add custom time zone information to an existing configuration group
-------------------------------------------------------------------

You can update settings in an existing configuration group by using the
**configuration-patch** command. You need to include
the ID value for the configuration group in the command.

The following command shows how to update the ``default_time_zone`` setting
to add the IST (India Standard Time, +6:00) time zone to a
configuration group with id <config\_id>:

.. code::

    $ trove configuration-patch <config_id> '{"default_time_zone":"+6:00"}'

This command does not return any output.
