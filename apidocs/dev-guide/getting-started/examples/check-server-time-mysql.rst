.. _check-server-time-zone:

Check the server time zone
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can check the current time zone setting for an instance by
`logging in to the mysql console <http://ord.admin.kc.rakr.net/knowledge_center/article/connecting-to-your-cloud-database>`__
and querying the value of ``global.time_zone``:

.. code::  

    SELECT @@global.time_zone;  

The returned value will show the instance's current time zone
setting, for example:

.. code::  

     +--------------------+ | @@global.time_zone | +--------------------+ | +06:00  |


If the time zone does not reflect what you set in the configuration group attached to the 
instance, the instance may need to be restarted in order for the change to take effect.
