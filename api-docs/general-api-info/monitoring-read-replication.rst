.. _cdb-dg-generalapi-monitoringread:

===========================
Monitoring read replication
===========================

After setting up replication, you should periodically monitor your replicas to
ensure that they are in a healthy state. See the table below for the mysql
variables that you should monitor.

All the variables mentioned in the table below for monitoring replication are
present in the monitoring agent running on your database instance. You can
monitor these variables using https://intelligence.rackspace.com and also set
up alarms to be notified of the state of your replica. You can also monitor
these variables by executing the ‘SHOW GLOBAL STATUS’ and ‘SHOW SLAVE STATUS’
commands.

**Variables for Monitoring Read Replication**

+---------------------+------------------------------------------------------+
|      Variable       |                     Description                      |
+=====================+======================================================+
| Slave\_running      | This is a global status variable and its value       |
|                     | can be ‘ON’ or ‘OFF’. If the value is ‘ON’ that      |
|                     | means the replica is connected to the source DB      |
|                     | instance and both SQL thread and IO thread are       |
|                     | running. If the value is ‘OFF’, you look at          |
|                     | Last\_SQL\_Errno and Last\_SQL\_Error                |
|                     | for more error information.                          |
+---------------------+------------------------------------------------------+
| Slave\_IO\_Running  | This variable is a part of the Show Slave status     |
|                     | and its value can be ‘Yes’, ‘No’, or ‘Connecting’.   |
|                     | If the value is ‘No’, that means the replica         |
|                     | I/O thread is not running and you can look at        |
|                     | Last\_IO\_Errno and Last\_IO\_Error for              |
|                     | more error information.                              |
+---------------------+------------------------------------------------------+
| Slave\_SQL\_Running | This variable is a part of the                       |
|                     | Show Slave status and its value can be ‘Yes’         |
|                     | or ‘No’. It tells whether the replica’s SQL thread   |
|                     | has started and is working well. If the value        |
|                     | is ‘No’, you can look at Last\_SQL\_Errno and        |
|                     | Last\_SQL\_Error for more error information.         |
+---------------------+------------------------------------------------------+
| Last\_IO\_Errno     | Indicates the error number of the most recent thread |
|                     | that caused the I/O thread to stop.                  |
+---------------------+------------------------------------------------------+
| Last\_IO\_Error     | Indicates the error message of the most recent       |
|                     | thread that caused the I/O thread to stop.           |
+---------------------+------------------------------------------------------+
| Last\_SQL\_Errno    | Indicates the error number of the most recent        |
|                     | thread that caused the MySQL thread to stop.         |
+---------------------+------------------------------------------------------+
| Last\_SQL\_Error    | Indicates the error message of the most recent       |
|                     | thread that caused the MySQL thread to stop.         |
+---------------------+------------------------------------------------------+
