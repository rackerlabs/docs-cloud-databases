.. _setup-gui-client::

MySQL and GUI administration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you want to access your database using the command line MySQL client,
then you have now completed the *Getting Started*.

Otherwise, you can use a GUI tool such as phpMyAdmin to interact with
your database instance. Common operations include managing databases,
tables, fields, relations, indexes, users, and permissions. Included
below is a procedure to set up phpMyAdmin on an Ubuntu 11.04 Cloud
Server.

For more detailed installation configuration instructions see the
phpMyAdmin documentation at: http://www.phpmyadmin.net/documentation/.

..  note:: 

    Rackspace does not provide phpMyAdmin support, and the user is
    responsible for any security related configuration.

 
Install and configure phpMyAdmin on an Ubuntu 11.04 Cloud Server
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Install phpMyAdmin:

   code:: 
   
   sudo apt-get install phpmyadmin
   

2. Set up a symbolic link to the phpmyadmin config file:
   
   .. code::
   
      sudo ln -s /etc/phpmyadmin/apache.conf/etc/apache2/conf.d/phpmyadmin.conf
      

3. Edit the ``/etc/phpmyadmin/config-db.php`` config file to point to
   your database instance:
   
   .. code::

      $dbserver='<cloud database hostname>';
      

4. Restart apache:
  
    .. code::
    
       sudo apachectl restart
       

5. Access phpMyAdmin at ``http://<your\_ipaddress>/phpMyAdmin:``

   .. image:: ../_images/phpMyAdmin.png
