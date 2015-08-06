
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Create Ha Database Instance -  Rackspace Cloud Databases Developer Guide
=============================================================================

Create Ha Database Instance
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <post-create-ha-database-instance-version-accountid-ha.html#request>`__
`Response <post-create-ha-database-instance-version-accountid-ha.html#response>`__

.. code::

    POST /{version}/{accountId}/ha

Creates a new HA instance.

This operation creates a new HA instance.

The ``name`` of the HA instance is a required attribute.

The following attributes are required for each HA instance:

Required and optional attributes for Create HA instanceName DescriptionRequirednameSpecifies the name of the HA instance.                             The length should be limited to 255 characters and any characters are permitted.Yes(datastore)                            version/typeThe version and type of the datastore.Yesreplica_source                            (name/flavorRef/volume)The name, flavorRef, and volume of the replica source.                            For details of each of these parameters refer to the required and optional attributes for Create instance.Yesreplicas                            (name/flavorRef/volume                            of replicas)Name, flavorRef, and volume of the replicas.                            For details of each of these parameters refer to the required and optional attributes for Create instance.YesnetworksComma-separated list of networks to be associated with the HA group. For example: ``{“networks”:[“public”,“servicenet”]}``

.. note::
   Notes 
   
   *  By default (if not specified), it will be servicenet.
   *  If a public network would be required in addition to the servicenet, it would have to be specified in the option: ``"networks": ["public”]``. Note that this will add a public network in addition to a servicenet/private network.
   *  Both the networks as options: ``"networks": ["public", "servicenet"]``, can also be specified.
   
   
   

NoaclsIP based ACL in the CIDR format. For example: 1.2.3.4/32. This is required to allow the                             HA group access to the specified IP. By default, the HA group access is blocked. Additionally, if it                             is not specified while creating the HA group, it can be added later. Refer to `Add ACLs to an HA instance <http://docs.rackspace.com/cdb/api/v1.0/cdb-devguide/content/POST_addAclToHaInstance__version___accountId__ha__haId__acls_ha.html>`__section 4.10.5 for details.No

This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |Accepted                 |The request has been     |
|                          |                         |accepted for processing. |
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
|404                       |Not Found                |The requested item was   |
|                          |                         |not found.               |
+--------------------------+-------------------------+-------------------------+


Request
^^^^^^^^^^^^^^^^^

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{accountId}               |xsd:string               |The account ID of the    |
|                          |                         |owner of the specified   |
|                          |                         |instance.                |
+--------------------------+-------------------------+-------------------------+








**Example Create Ha Database Instance: JSON request**


.. code::

    POST /v1.0/1234/ha HTTP/1.1
    User-Agent: python-troveclient
    Host: ord.databases.api.rackspacecloud.com
    X-Auth-Token: e3b2c743aebf467fb6b91cbb644c036e
    Accept: application/json
    Content-Type: application/json
    {  
       "ha":{  
          "datastore":{  
             "version":"5.6",
             "type":"MYSQL"
          },
          "replicas":[  
             {  
                "volume":{  
                   "size":1
                },
                "flavorRef":"2",
                "name":"source_replica1"
             }
          ],
          "name":"ha-1",
          "replica_source":[  
             {  
                "volume":{  
                   "size":1
                },
                "flavorRef":"2",
                "name":"source"
             }
          ]
       }
    }
    


Response
^^^^^^^^^^^^^^^^^^





**Example Create Ha Database Instance: JSON response**


.. code::

    HTTP/1.1 202 Accepted
    Content-Type: application/json
    Via: 1.1 Repose (Repose/2.6.7)
    Content-Length: ‘219’
    Date: Fri, 08 May 2015 13:03:06 GMT
    Server: Jetty(8.0.y.z-SNAPSHOT)
    
    {  
       "ha_instance":{  
          "name":"ha-1",
          "replicas":[  
    
          ],
          "replica_source":[  
    
          ],
          "id":"e7fdf90b-7140-4edb-b449-e093d55008fb",
          "state":"BUILD",
          "acls":[  
    
          ],
          "datastore":{  
             "version":"5.6",
             "type":"mysql"
          },
          "networks":[  
    
          ]
       }
    }
    

