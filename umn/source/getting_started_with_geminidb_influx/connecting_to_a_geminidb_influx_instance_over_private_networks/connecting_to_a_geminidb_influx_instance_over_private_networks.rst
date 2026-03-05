:original_name: nosql_02_0053.html

.. _nosql_02_0053:

Connecting to a GeminiDB Influx Instance Over Private Networks
==============================================================

Scenarios
---------

This section uses the Linux operating system as an example to describe how to connect an ECS to a GeminiDB Influx instance over private networks.

Usage Notes
-----------

-  The target instance and ECS must be in the same VPC and subnet.
-  The ECS must be in a security group that can access the target instance.

   -  If the target instance is associated with the default security group, you do not need to configure security group rules for the instance and ECS.
   -  If the target instance is associated with a non-default security group, check whether the non-default security group rules allow the ECS to access the instance. For details, see section :ref:`Configuring Security Group Rules <nosql_02_0052>`.

-  The default port of the GeminiDB Influx instance is 8635 and cannot be changed.

Prerequisites
-------------

.. important::

   The instance and ECS must be in the same VPC and subnet.

-  Download the InfluxDB client from the `official website <https://dl.influxdata.com/influxdb/releases/influxdb-1.7.9-static_linux_amd64.tar.gz>`__.

SSL Connection
--------------

#. Log in to the ECS. For details, see section "Creating ECSs" in the *Elastic Cloud Server User Guide*.

#. Upload the InfluxDB client installation package to the ECS.

#. Decompress the client package.

   .. code-block::

      tar -xzf influxdb-1.7.9-static_linux_amd64.tar.gz

#. Connect your instance to the InfluxDB client.

   a. Run the following command to go to the InfluxDB directory:

      .. code-block::

         cd influxdb-1.7.9-1

   b. Run the following command to connect to the InfluxDB shell:

      .. code-block::

         ./influx -ssl -host <DB_HOST> -port <DB_PORT>

      Example:

      .. code-block::

         ./influx -ssl -host 192.168.1.201 -port 8635

   c. Run the **auth** command to authenticate the user.

      **auth**

      Enter the username and password as prompted.

      **username**:*<DB_USER>*

      **password**:*<DB_PWD>*

   .. note::

      -  *<DB_USER>* indicates the administrator name. The default value is **rwuser**.

      -  *<DB_PWD>* indicates the administrator password.

      -  *<DB_HOST>* indicates the private IP address of the node to be connected. Obtain the value from the **Private IP Address** column in the node list on the **Basic Information** page.

         If your instance has multiple nodes, select the private IP address of a node.

      -  *<DB_PORT>* indicates the port. The default value is **8635** and cannot be changed.

#. After the authentication is successful, run the **show databases** command.

   If the following information is displayed, the connection is successful.

   .. code-block::

      name: databases
      name
      ----
      _internal

Non-SSL Connection
------------------

#. Log in to the ECS. For details, see section "Creating ECSs" in the *Elastic Cloud Server User Guide*.

#. Upload the InfluxDB client installation package to the ECS.

#. Decompress the client package.

   .. code-block::

      tar -xzf influxdb-1.7.9-static_linux_amd64.tar.gz

#. Connect your instance to the InfluxDB client.

   a. Run the following command to go to the InfluxDB directory:

      **cd** **influxdb-1.7.9-1**

   b. Run the following command to connect to the InfluxDB shell:

      .. code-block::

         ./influx -host <DB_HOST> -port <DB_PORT>

      Example:

      .. code-block::

         ./influx -host 192.168.1.201 -port 8635

   c. Run the **auth** command to authenticate the user.

      **auth**

      Enter the username and password as prompted.

      **username**:*<DB_USER>*

      **password**:*<DB_PWD>*

   .. note::

      -  *<DB_USER>* indicates the administrator name. The default value is **rwuser**.

      -  *<DB_PWD>* indicates the administrator password.

      -  *<DB_HOST>* indicates the private IP address of the node to be connected. Obtain the value from the **Private IP Address** column in the node list on the **Basic Information** page.

         If your instance has multiple nodes, select the private IP address of a node.

      -  *<DB_PORT>* indicates the port. The default value is **8635** and cannot be changed.

#. After the authentication is successful, run the **show databases** command.

   **show databases**

   If the following information is displayed, the connection is successful.

   .. code-block::

      name: databases
      name
      ----
      _internal
