:original_name: nosql_02_0005.html

.. _nosql_02_0005:

Connecting to a GeminiDB Cassandra Instance Over Private Networks
=================================================================

Scenarios
---------

This section uses the Linux operating system as an example to describe how to connect an ECS to a GeminiDB Cassandra instance over private networks.

Constraints
-----------

-  The DB instances must be in the same VPC subnet as the ECS.
-  The ECS must be allowed in a security group that has access to the DB instances.

   -  If the target DB instance belongs to the default security group, you do not need to configure security group rules.

   -  If the security group that the target DB instance belongs to is not the default security group, check whether the security group rules allow the ECS to connect to the DB instance. For details, see section :ref:`Configuring Security Group Rules <nosql_02_0004>`.

      If the security group rules allow the access from the ECS, the ECS can connect to the DB instance.

      If the security group rule does not allow the access from the ECS, you need to add an inbound rule to the security group.

-  The default port of the GeminiDB Cassandra instance is 8635.

Prerequisites
-------------

-  You have created an ECS running Linux. For details, see "Creating ECSs" in *ECS User Guide*.
-  You have obtained the `Cassandra client installation package 3.11.3 <https://archive.apache.org/dist/cassandra/3.11.3/apache-cassandra-3.11.3-bin.tar.gz>`__ from the official website.
-  If Python is not installed, download and install `Python 2.7 <https://www.python.org/ftp/python/2.7.16/Python-2.7.16.tgz>`__ and `cassandra-driver <https://pypi.org/project/cassandra-driver/>`__ 3.11.0 or later.

Using the Cassandra Client Tool to Connect to a DB Instance
-----------------------------------------------------------

#. Log in to the ECS. For details, see the section "Logging In to an ECS" in the *Elastic Cloud Server User Guide*.

#. Upload the Cassandra client installation package 3.11.3 to the ECS. If Wget fails to be downloaded, download it to your local PC and then upload it to the ECS.

   wget https://archive.apache.org/dist/cassandra/3.11.3/apache-cassandra-3.11.3-bin.tar.gz

   tar -zxvf apache-cassandra-3.11.3-bin.tar.gz

#. Obtain the client tool cqlsh.

   cd apache-cassandra-3.11.3/bin

#. Connect to the DB instance in the directory where the cqlsh tool is located.

   **./cqlsh** <*DB_HOST*> <*DB_PORT*> **-u** <*DB_USER*>

   Example:

   **./cqlsh 192.168.1.8 8635 -u rwuser**

   .. note::

      -  <*DB_HOST*> indicates the private IP address of the node to be connected. Obtain the value from the **Private IP Address** column in the node list on the **Basic Information** page.
      -  <*DB_PORT*> indicates the port number. The default value is 8635 and cannot be changed.
      -  <*DB_USER*> indicates the database account name. The default value is **rwuser**.

#. Check the connection result. If the following information is displayed, the connection is successful.

   .. code-block::

      rwuser@cqlsh>

**Follow-up Operations**
------------------------

After logging in to the GeminiDB Cassandra instance, you can perform the following operations:

-  Run the **HELP** command to view all supported commands.

-  **HELP** *<COMMAND>*: This command queries the usage of a command. Example: **HELP DESC**
-  Keyspace syntax

   -  Create a keyspace, for example:

      **CREATE KEYSPACE IF NOT EXISTS test_keyspace WITH replication = {'class': 'SimpleStrategy', 'replication_factor': '3'};**

      Set the keyspace name to **test_keyspace**, **replication** to **SimpleStrategy**, and number of replicas to **3**.

   -  **DESC** *<keyspace_name>*: This command verifies the creation result.

   -  **use** *<keyspace_name>*: This command switches to the keyspace you created.

   -  **DROP** **KEYSPACE** *<keyspace_name>*: This command deletes the keyspace you created.

-  Table syntax

   -  Create a table, for example:

      **CREATE TABLE test_table(user_id int, age int, user_name text, PRIMARY KEY(user_id));**

      **test_table** is a table name defined by the following three columns: **user_id**, **age**, and **user_name**. **user_id** indicates a user ID of the INT data type. **age** indicates user age of the INT data type. **user_name** indicates a username of the TEXT data type. The primary key is **user_id**.

   -  **DESC** *<table_name>*: This command verifies the creation result.

   -  Insert data into the table, for example:

      **INSERT INTO test_table (user_id, age, user_name) VALUES (1, 10, 'user1');**

      **INSERT INTO test_table (user_id, age, user_name) VALUES (2, 20, 'user2');**

      **INSERT INTO test_table (user_id, age, user_name) VALUES (3, 30, 'user3');**

   -  **SELECT \* FROM** *<table_name>*: This command queries table data.

   -  Add a column to the table, for example:

      **ALTER TABLE test_table ADD gender text;**

   -  Update data in a table of a keyspace, for example:

      **UPDATE test_keyspace.test_table SET prename = 'user_prename1' WHERE user_id = 1;**

      **UPDATE test_keyspace.test_table SET prename = 'user_prename2' WHERE user_id = 2;**

      **UPDATE test_keyspace.test_table SET prename = 'user_prename3' WHERE user_id = 3;**

   -  Delete data from a table in a keyspace, for example:

      Delete the age data of the user whose ID is **1**.

      **DELETE age FROM test_keyspace.test_table WHERE user_id=1;**

      Delete the entire record of the user whose ID is **2**.

      **DELETE FROM test_keyspace.test_table WHERE user_id=2;**

   -  Clear all records in the table, for example:

      **TRUNCATE test_keyspace.test_table;**

   -  Delete an entire table, for example:

      **DROP TABLE test_keyspace.test_table;**
