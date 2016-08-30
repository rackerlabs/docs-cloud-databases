.. _cdb-dg-generalapi-security:

========
Security
========

This section describes security features for Cloud Databases.

.. _cdb-dg-generalapi-security-restriction:

User access restriction by host
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Cloud Databases supports the specification of a ``host`` parameter when
creating and modifying users. This parameter adds the additional security
measure of restricting the hosts from which a database user is allowed to
connect to the database. The ``host`` parameter specifies the host a user
must connect from in order for the username and password to be allowed to
connect to the database on an instance.

The ``host`` parameter must be a string consisting of either a numeric IPv4
address such as "192.168.1.12", or the string "%". The string "%" serves as a
wildcard to the database, and means "from anywhere". Users created without
mention of the ``host`` parameter are given the default value of "%", which
allows them to connect to the database from any host.

It is important to note that two database users with the same name but
different hosts are treated as completely distinct from each other, especially
when it comes to listing users and modifying their database access with the
API. This means that the username alone is not sufficient to refer to a user
in some cases. To remove ambiguity, every API response that names users now
also includes the ``host`` field.

The ``host`` field may optionally be provided for each user in the body of
Create Instance, Create User, and Change User Password calls. In the case of
the List User, List User Access, Grant User Access, and Revoke User Access
calls, the username is part of the request URL instead of a JSON message body.
In these cases, the host can be specified with the username using the format
of *username@host*, for example ``testuser@192.168.1.12``. Should a username
contain the character '@', the hostname must be specified explicitly, as in
*user@name@%*.

.. warning::
    Due to a limitation of the routing middleware, users with periods (.) in
    their name can be parsed incorrectly in GET, DELETE, and PUT calls, where
    such a name is the last section of the request URL.

    In these cases, you must escape the periods by URL encoding them as
    "%252E", so "some.user" would become "some%252Euser". Note that CREATE
    calls are not affected as these names are in JSON data, and not part of
    the request's URL. For request examples with escaped periods in user
    names, refer to List User Access.
