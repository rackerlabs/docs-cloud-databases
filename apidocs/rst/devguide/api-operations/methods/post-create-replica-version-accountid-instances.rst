
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _post-create-replica-version-accountid-instances:

Create replica
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /{version}/{accountId}/instances

Creates a replica of the source instance, as specified by the value of the ``replica_of`` attribute.

This operation asynchronously provisions a replica for the specified source database instance. This call requires the user to specify a flavor and a volume size. It also requires specifying the source database instance using the ``replica_of`` attribute. The service then provisions the replica with the requested flavor and sets up a volume of the specified size.

.. note::
   
   
   *  The replica will be created with the default configuration. If you wish to apply the same configuration as the source database instance or another configuration, you will need to apply that configuration to the replica. Refer to `Update database instance <http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/PUT_updateInstance__version___accountId__instances__instanceId__Database_Instances.html>`__ for details.
   *  Since the process of creating a replica makes a backup behind the scenes, the user calling the Create replica operation will need access to Cloud Files.
   
   
   

.. warning::
   Adding a replica will restart the MySQL service on the source database instance. However the state of the instance might not reflect that and still be ACTIVE. Wait for a couple of seconds for the process to be complete. The best way to verify whether the process is complete is to check the slave metrics as described in `Monitoring read replication <http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/Monitoring_Read_Replication-d1e3694.html>`__.
   
   

.. note::
   Notes
   
   
   
   *  You can create only one database instance per ``POST`` request.
   *  You can create a database instance with one or more databases, and users associated to those databases.
   *  The default binding for the database instance is port 3306.
   *  When used with the ``restorePoint`` attribute, this call performs the Restore Backup operation, creating a new database instance to store the backup.
   *  For information about using SSL with your database instance, refer to `Using SSL with Your Cloud Database Instances <http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/Using_SSL_for_Database_Instances.html>`__.
   
   
   

The following table lists the required and optional attributes for Create replica:

.. table:: Required and optional attributes for Create replica

    
    +--------------+--------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+---------+
    |Applies To    |Name                                                                                                          |Description                                                                                                   |Required |
    +==============+==============================================================================================================+==============================================================================================================+=========+
    |Instance      |flavorRef                                                                                                     |Reference (href) to a flavor as specified in the response from the List Flavors API call. This is the actual  |Yes      |
    |              |                                                                                                              |URI as specified by the href field in the link. Refer to the List Flavors response examples that follow for   |         |
    |              |                                                                                                              |an example of the flavorRef. .. note:: Rather than the flavor URI, you can also pass the flavor id (integer)  |         |
    |              |                                                                                                              |as the value for flavorRef. Refer to `List flavors <http://docs.rackspace.com/cdb/api/v1.0/cdb-               |         |
    |              |                                                                                                              |devguide/content/GET_getFlavors__version___accountId__flavors_flavors.html>`__ for details.                   |         |
    +--------------+--------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+---------+
    |(volume) size |Specifies the volume size in gigabytes (GB). The value specified must be between 1 and 300.                   |Yes                                                                                                           |         |
    +--------------+--------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+---------+
    |name          |Name of the instance to create. The length of the name is limited to 255 characters and any characters are    |No                                                                                                            |         |
    |              |permitted.                                                                                                    |                                                                                                              |         |
    +--------------+--------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+---------+
    |replica_of    |Identifier of the source instance to replicate.                                                               |Yes                                                                                                           |         |
    +--------------+--------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+---------+
    |configuration |Identifier of the configuration group to associate with the instance.                                         |No                                                                                                            |         |
    +--------------+--------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+---------+
    |(datastore)   |Name or uuid of the datastore version and type to associate with the instance. If the datastore is not        |No                                                                                                            |         |
    |version / type|specified, it defaults to mysql.                                                                              |                                                                                                              |         |
    +--------------+--------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+---------+
    |Database      |name                                                                                                          |Specifies database names for creating databases on instance creation. Refer to `Create instance               |No       |
    |              |                                                                                                              |<http://docs.rackspace.com/cdb/api/v1.0/cdb-                                                                  |         |
    |              |                                                                                                              |devguide/content/POST_createInstance__version___accountId__instances_Database_Instances.html>`__ for the      |         |
    |              |                                                                                                              |required json format.                                                                                         |         |
    +--------------+--------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+---------+
    |character_set |Set of symbols and encodings. The default character set is ``utf8``.                                          |No                                                                                                            |         |
    +--------------+--------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+---------+
    |collate       |Set of rules for comparing characters in a character set. The default value for collate is                    |No                                                                                                            |         |
    |              |``utf8_general_ci``.                                                                                          |                                                                                                              |         |
    +--------------+--------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+---------+
    |User          |name                                                                                                          |Specifies user name for the database on instance creation. Refer to `Create user                              |No       |
    |              |                                                                                                              |<http://docs.rackspace.com/cdb/api/v1.0/cdb-                                                                  |         |
    |              |                                                                                                              |devguide/content/POST_createUser__version___accountId__instances__instanceId__users_user_management.html>`__  |         |
    |              |                                                                                                              |for the required json format.                                                                                 |         |
    +--------------+--------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+---------+
    |password      |Specifies password for those users on instance creation. Refer to `Create user                                |No                                                                                                            |         |
    |              |<http://docs.rackspace.com/cdb/api/v1.0/cdb-                                                                  |                                                                                                              |         |
    |              |devguide/content/POST_createUser__version___accountId__instances__instanceId__users_user_management.html>`__  |                                                                                                              |         |
    |              |for the required json format.                                                                                 |                                                                                                              |         |
    +--------------+--------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+---------+
    |(database)    |Specifies names of databases that those users can access on instance creation. Refer to `Create user          |No                                                                                                            |         |
    |name          |<http://docs.rackspace.com/cdb/api/v1.0/cdb-                                                                  |                                                                                                              |         |
    |              |devguide/content/POST_createUser__version___accountId__instances__instanceId__users_user_management.html>`__  |                                                                                                              |         |
    |              |for the required json format.                                                                                 |                                                                                                              |         |
    +--------------+--------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+---------+
    |host          |Specifies the host from which a user is allowed to connect to the database. Possible values are a string      |No                                                                                                            |         |
    |              |containing an IPv4 address or "%" to allow connecting from any host. Refer to `User access restriction by     |                                                                                                              |         |
    |              |host <http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/user_access_restrict_by_host-               |                                                                                                              |         |
    |              |dle387.html>`__ for details. If ``host`` is not specified, it defaults to "%".                                |                                                                                                              |         |
    +--------------+--------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+---------+
    |Restore       |restorePoint                                                                                                  |Specifies the backup id from which to restore the database instance. .. note:: * When you execute the Restore |No       |
    |              |                                                                                                              |Backup operation, a new database instance is created to store the backup whose id is specified by the         |         |
    |              |                                                                                                              |``restorePoint`` attribute. * All users/passwords/access that were on the instance at the time of the backup  |         |
    |              |                                                                                                              |will be restored along with the databases. * You can create new users or databases if you want, but they      |         |
    |              |                                                                                                              |cannot be the same as the ones from the instance that was backed up. * Refer to the Create Database Instance  |         |
    |              |                                                                                                              |Restore Request and Response examples for the required json format and details.                               |         |
    +--------------+--------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+---------+
    

Refer to `Database instance status <http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/database_instance_status.html>`__ for a list of possible database instance statuses that may be returned.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
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
""""""""""""""""




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{accountId}               |String                   |The account ID of the    |
|                          |                         |owner of the specified   |
|                          |                         |instance.                |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




**Example Create replica: JSON request**


The following example shows the Create replica request:

.. code::

   POST /v1.0/1234/instances HTTP/1.1
   User-Agent: python-troveclient
   Host: ord.databases.api.rackspacecloud.com
   X-Auth-Token: 87c6033c-9ff6-405f-943e-2deb73f278b7
   Accept: application/json
   Content-Type: application/json
   
   
   {
     "instance": {
       "volume": {
         "size": 1
       },
       "flavorRef": "9",
       "name": "t2s1_ALT_GUEST",
       "replica_of": "6bdca2fc-418e-40bd-a595-62abda61862d"
     }
   }
   





Response
""""""""""""""""










**Example Create replica: JSON response**


The following example shows the Create replica response:

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Via: 1.1 Repose (Repose/2.6.7)
   Content-Length: 697
   Date: Thu, 13 Feb 2014 21:47:17 GMT
   Server: Jetty(8.0.y.z-SNAPSHOT)
   
   {
     "instance": {
       "status": "BUILD",
       "updated": "2014-10-14T18:42:15",
       "name": "t2s1_ALT_GUEST",
       "links": [
         {
           "href": "https://ord.databases.api.rackspacecloud.com/v1.0/5919009/instances/8367c312-7c40-4a66-aab1-5767478914fc",
           "rel": "self"
         },
         {
           "href": "https://ord.databases.api.rackspacecloud.com/instances/8367c312-7c40-4a66-aab1-5767478914fc",
           "rel": "bookmark"
         }
       ],
       "created": "2014-10-14T18:42:15",
       "id": "8367c312-7c40-4a66-aab1-5767478914fc",
       "volume": {
         "size": 1
       },
       "flavor": {
         "id": "9",
         "links": [
           {
             "href": "https://ord.databases.api.rackspacecloud.com/v1.0/5919009/flavors/9",
             "rel": "self"
           },
           {
             "href": "https://ord.databases.api.rackspacecloud.com/flavors/9",
             "rel": "bookmark"
           }
         ]
       },
       "datastore": {
         "version": "5.6",
         "type": "mysql"
       },
       "replica_of": {
         "id": "6bdca2fc-418e-40bd-a595-62abda61862d",
         "links": [
           {
             "href": "https://ord.databases.api.rackspacecloud.com/v1.0/5919009/instances/6bdca2fc-418e-40bd-a595-62abda61862d",
             "rel": "self"
           },
           {
             "href": "https://ord.databases.api.rackspacecloud.com/instances/6bdca2fc-418e-40bd-a595-62abda61862d",
             "rel": "bookmark"
           }
         ]
       }
     }
   }
   


For convenience, notice in the response example above that resources contain links to themselves. This allows a client to easily obtain resource URIs rather than to construct them. There are two kinds of link relations associated with resources. A ``self`` link contains a versioned link to the resource. These links should be used in cases where the link will be followed immediately. A ``bookmark`` link provides a permanent link to a resource that is appropriate for long term storage.



