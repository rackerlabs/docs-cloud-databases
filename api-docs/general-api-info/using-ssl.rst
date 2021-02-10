.. _cdb-dg-generalapi-ssl:

======================================
Using SSL for Cloud Database instances
======================================

SSL (Secure Sockets Layer) is a security protocol that uses encryption
technology to ensure that your sensitive information sent over the internet
is protected.

Cloud Databases installs a certificate on the database instance at the time
of provisioning.

..  note::
    All database instances created before October 20, 2014 should be restarted
    before accepting SSL connections.

To use SSL, perform the following steps:

-  For encrypting connections using SSL, download the certificate from
   the following URL:

     http://ssl.rackspaceclouddb.com/rackspace-ca-2021.pem.

-  To use SSL with the default MySQL command line, pass the downloaded SSL
   certificate to the client at startup:

   .. code::

       mysql —ssl-ca=/path/to/rackspace-ca-2021.pem

   For additional information, see the
   `MySQL documentation <http://dev.mysql.com/doc/refman/5.6/en/using-ssl-connections.html>`_.

-  (Optional) To set up restrictions on a user to require SSL for communicating
   with the database, MySQL supports GRANT statement modifier “REQUIRE SSL”.
   For example, to restrict ‘database\_user’ to read, write, delete on
   prod\_database only using secure SSL connection, login to MySQL as root
   and then issue the following command:

   .. code::

       GRANT SELECT, INSERT, UPDATE, DELETE ON prod_database.* TO 'database_user'@'%' REQUIRE SSL;

   ..  note::
        If the user already exists, you must revoke all existing privileges
        for the user and then use the preceding grant statement to give
        appropriate privileges to the user. Then remember to FLUSH PRIVILEGES
        to make the privilege changes take effect.

.. warning::
    Using SSL encryption is a resource intensive operation and may have some
    impact on the latency of your database connection.
