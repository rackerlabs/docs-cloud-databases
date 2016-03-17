.. _using-trove-client:

Using the trove client
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. contents::
   :local:
   :depth: 1

The trove client is a command-line tool that provides access to all public
Cloud Databases API methods. To send requests using the client, you
have to install the client and set environment variables.

Prerequisites
^^^^^^^^^^^^^^^^^^^

- Linux or Mac OS X
- Python 2.7 or later
- **setuptools** package, installed by default on Mac OS X
- **pip** package
- Rackspace Cloud account and access to Rackspace Cloud Orchestration


Install the trove client
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The python-troveclient package contains the trove client.

Run the following commands for your operating system to install the python-troveclient 
package:

For Ubuntu, Debian, or OS X:

.. code::

    $ sudo apt-get install python2.7-dev

    $ sudo pip install python-troveclient
    
For RHEL, CentOS, or Fedora:

.. code::

     $ sudo pip install python-troveclient
     
     
.. note::
    If you previously installed the python-troveclient package, run the following command 
    for your operating system to upgrade it:

    For Ubuntu, Debian, or OS X:

    .. code:: 
    
         $ sudo pip install --upgrade python-troveclient
         
    For RHEL, CentOS, or Fedora:

    .. code::
    
         $ sudo pip install --upgrade python-troveclient
         
     
.. _set-environment-variables-client:

Configure environment variables for client
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Edit your **bash.profile** file or **.bashrc** file to add and set environment
variables that enable the trove client to connect to your Rackspace
Cloud account. Use nano, or a text editor of your choice, to edit the file.

.. code::

     $ nano ~/.bash_profile

Add the following sets of lines to your bash profile and save the file.
Information about the environment variables is provided after the example.

.. code::

	 export OS_AUTH_URL=https://identity.api.rackspacecloud.com/v2.0/
	 export OS_USERNAME=yourUserName
	 export OS_TENANT_ID=yourTenantId
	 export OS_REGION_NAME=yourRegionName
	 export OS_PASSWORD=yourPassword

	 export TROVE_SERVICE_TYPE=rax:database

The following table describes the environment variables:

+-----------------------+-------------------------------------------------+
| Environment variable  | Description                                     |
+=======================+=================================================+
| OS_USERNAME           | Your Rackspace Cloud user name.                 |
+-----------------------+-------------------------------------------------+
| OS_PASSWORD           | Your Rackspace Cloud password.                  |
+-----------------------+-------------------------------------------------+
| OS_PROJECT_ID         | Your project ID. In these examples, set it to   |
|                       | your Rackspace Cloud account number.            |
+-----------------------+-------------------------------------------------+
| OS_TENANT_ID          | Your Rackspace Cloud tenant ID (account number) |
+-----------------------+-------------------------------------------------+
| TROVE_SERVICE_TYPE    | The Rackspace Cloud service name that you want  |
|                       | trove client to access. Specify ``rax:database``|
|                       | for Cloud Databases.                            |
+-----------------------+-------------------------------------------------+
| OS_AUTH_URL           | The endpoint for the Rackspace Cloud Identity   |
|                       | service, which the trove client uses for        |
|                       | authentication.                                 |
+-----------------------+-------------------------------------------------+
| OS_REGION_NAME        | The regional endpoint (for example, DFW) where  |
|                       | you want to deploy the Cloud Databases          |
|                       | resources. For details, see                     |
|                       | :ref:`service-access-endpoints`.                |
+-----------------------+-------------------------------------------------+

After adding the environment variables, complete the following steps to set 
file permissions and apply the updates.

Set permissions on the bash profile or .bashrc file
.....................................................

Change the file permissions so that other people cannot steal the 
password that you included in the file. 

.. code::

      $ chmod 600 ~/.bash_profile
      
Source the environment variables
...................................

To apply the updates to your current shell environment, source the updated file.
If you added the environment variables to your bash_profile, run the following 
command.

.. code:: 

      $ source ~/.bash_profile

If you set your environment variables in the .bashrc file, run the following command.

.. code:: 

      $ source ~/.bashrc

Test the client
...................

To verify that you can talk to the API server, run the following command to authenticate 
and list flavors:

.. code::

     $ trove flavor-list
     
Then, list database instances:

.. code::

     $ trove list
     
Get trove-client help
.........................
    
Run the following help command to get information about using the trove client.

.. code::

     $ trove help

For a complete list of trove commands, see the
:os-docs:`OpenStack trove client command-line reference
<cli-reference/content/troveclient_commands.html>`.

