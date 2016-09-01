.. _manage-tz-dbinstance-using-config-grp:

==============================
Manage time zone configuration
==============================

The server time zone for a set of current and future database instances
can be set using the configuration groups feature of Cloud Databases.
Suppose you want to set the default time zone for a set of database
instances.

The server time zone is set in MySQL in the ``default_time_zone``
parameter, and the default value is ‘SYSTEM’. You can set the time zone
in MySQL using either:

-  named time zones

-  UTC (Coordinated Universal Time) offsets

To set the time zone using named time zones, use the appropriate name
for your zone, such as "Europe/London" or "US/Eastern" to set the
``default_time_zone``, for example:

-  ``{"default_time_zone":"Europe/London"}``

-  ``{"default_time_zone":"US/Eastern"}``

For more information about named time zones, see the `MySQL documentation`_ .

To set the ``default_time_zone`` using offsets of the time zone from
`UTC (Coordinated Universal Time)`_  use the appropriate offset value for your
zone. For example the CST (Central Standard Time) time zone would be "-6:00":

``{"default_time_zone":"-6:00”}``

If you lived in the AEST (Australian Eastern Standard Time) time zone on
the other hand, the offset would be "+10:00".

You can set ``default_time_zone`` in a configuration group that can be
applied to your database instance. You can create a new configuration
group just for the time zone management, or add the time zone parameter
to an existing configuration group.

After you update time zone settings on a database instance, you can
:ref:`check the server time <check-server-time-zone>` to verify the change.

Following are two methods for using a configuration group to set the default
time zone:

.. include:: examples/manage-tz-trove.rst
.. include:: examples/manage-tz-curl.rst
.. include:: examples/check-server-time-mysql.rst

.. Below are links definitions for above time zone info

.. _MySQL documentation: http://dev.mysql.com/doc/refman/5.6/en/time-zone-support.html
.. _UTC (Coordinated Universal Time): https://en.wikipedia.org/wiki/Coordinated_Universal_Time
