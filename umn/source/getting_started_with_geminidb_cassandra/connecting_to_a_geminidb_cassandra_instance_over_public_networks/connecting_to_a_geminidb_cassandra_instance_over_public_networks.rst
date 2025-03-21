:original_name: nosql_02_0009.html

.. _nosql_02_0009:

Connecting to a GeminiDB Cassandra Instance Over Public Networks
================================================================

Scenarios
---------

You can use an ECS or local device to connect to a GeminiDB instance over a public network.

This section describes how to use a Linux ECS to connect to a GeminiDB Cassandra instance over a public network.

Prerequisites
-------------

-  Bind an EIP to the GeminiDB Cassandra instance node and set security group rules.
-  You have created an ECS running Linux. For details, see "Creating ECSs" in *ECS User Guide*.
-  You have obtained the `Cassandra client installation package 3.11.3 <https://archive.apache.org/dist/cassandra/3.11.3/apache-cassandra-3.11.3-bin.tar.gz>`__ from the official website.
-  If Python is not installed, download and install `Python 2.7 <https://www.python.org/ftp/python/2.7.16/Python-2.7.16.tgz>`__ and `cassandra-driver <https://pypi.org/project/cassandra-driver/>`__ 3.11.0 or later.

Connecting to a DB Instance Through a Cassandra Client
------------------------------------------------------

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

      -  *<DB_HOST>* indicates the EIP of the node to be connected. Obtain the value from the **EIP** column in the node list on the **Basic Information** page.
      -  *<DB_PORT>* indicates the port number. The default value is **8635** and cannot be changed.
      -  *<DB_USER>* indicates the database account name. The default value is **rwuser**.

#. Check the connection result. If the following information is displayed, the connection is successful.

   .. code-block::

      rwuser@cqlsh>

Follow-up Operations
--------------------

After logging in to the GeminiDB Cassandra instance, you can perform the following operations:

-  Run the **HELP** command to view all supported commands.

-  Run **HELP** *<COMMAND>* to query the usage of a command. Example: **HELP DESC**
-  Keyspace syntax

   -  Create a keyspace. Example:

      **CREATE KEYSPACE IF NOT EXISTS nosql WITH replication = {'class': 'SimpleStrategy', 'replication_factor': '3'};**

      Set the keyspace name to **nosql**, **replication** to **SimpleStrategy**, and **replication_factor** to **3**.

   -  Run **DESC** *<keyspace_name>* to verify the creation results.

   -  Run **use** *<keyspace_name>* to switch to the keyspace you created.

   -  Run **DROP** **KEYSPACE** *<keyspace_name>* to delete the keyspace you created.

-  Table syntax

   -  Create a table. Example:

      **CREATE TABLE nosql_table(user_id int, age int, user_name text, PRIMARY KEY(user_id));**

      **nosql_table** indicates the table name, and the following three columns are defined: **user_id**, **age**, and **user_name**. **user_id** is the user ID of the INT type. **age** is the user age of the INT type. **user_name** is the username of the TEXT type. The primary key is **user_id**.

   -  Run **DESC** *<table_name>* to verify the creation results.

   -  Insert data into the table. Example:

      **INSERT INTO nosql_table (user_id, age, user_name) VALUES (1, 10, 'user1');**

      **INSERT INTO nosql_table (user_id, age, user_name) VALUES (2, 20, 'user2');**

      **INSERT INTO nosql_table (user_id, age, user_name) VALUES (3, 30, 'user3');**

   -  Run **SELECT \* FROM** *<table_name>* to query table data.

   -  Add a column to the table. Example:

      **ALTER TABLE nosql_table ADD gender text;**

   -  Update data in a table of a keyspace. Example:

      **UPDATE nosql.nosql_table SET prename = 'user_prename1' WHERE user_id = 1;**

      **UPDATE nosql.nosql_table SET prename = 'user_prename2' WHERE user_id = 2;**

      **UPDATE nosql.nosql_table SET prename = 'user_prename3' WHERE user_id = 3;**

   -  Delete data from a table in a keyspace. Example:

      Delete the age data of the user whose ID is **1**.

      **DELETE age FROM nosql.nosql_table WHERE user_id=1;**

      Delete the entire record of the user whose ID is **2**.

      **DELETE FROM nosql.nosql_table WHERE user_id=2;**

   -  Clear all records in the table. Example:

      **TRUNCATE nosql.nosql_table;**

   -  Delete the entire table. Example:

      **DROP TABLE nosql.nosql_table;**
