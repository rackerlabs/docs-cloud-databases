.. cdb-dg-generalapi-dbaccess:

===============================
Database instance accessibility
===============================

Database instances are directly accessible only on the internal ServiceNet
network and using a Cloud resource within the same regional datacenter. For
example, a database instance in DFW can only be accessed by a Cloud Server in
DFW.

Note that using a public Cloud Load Balancer allows you to access your
ServiceNet database instance from the public network by performing the
following steps:

#. Using the Cloud Databases API, create a database instance. For details see
   Create Instance.

#. Using the Cloud Load Balancers API, create a public load balancer and
   specify your database instance hostname as a node, or use the API to add
   your instance hostname as a node to an existing public load balancer.
   For details refer to the *Cloud Load Balancers Developer Guide* at
   :rax-devdocs:`Cloud Load Balancers Developer Guide <cloud-load-balancers/v1>`.
