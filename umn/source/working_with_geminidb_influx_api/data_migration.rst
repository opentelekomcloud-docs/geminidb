:original_name: nosql_09_0015.html

.. _nosql_09_0015:

Data Migration
==============

InfluxDB Community Edition is a popular time series database that focuses on high-performance queries and storage.

GeminiDB Influx API has better query, write, and data compression performance than InfluxDB Community Edition.

This section describes how to migrate data from InfluxDB Community Edition to GeminiDB Influx API.

How Data Is Migrated
--------------------

Use a migration tool to parse the TSM and WAL files of InfluxDB Community Edition and write the files to a line protocol file. Then, the line protocol file data is parsed and migrated to the destination side.

The migration process is divided into two phases:

-  Export: TSM and WAL files of InfluxDB Community Edition are concurrently parsed, and the parsed data is written into a line protocol file.
-  Import: Data in the line protocol file is concurrently read and is sent to each node in the GeminiDB Influx cluster.

The migration tool supports full migration and incremental migration, which can be configured in the configuration file.

Usage Notes
-----------

-  Deploy the migration tool on the same server as InfluxDB Community Edition and prepare a configuration file.
-  The migration tool needs to extract data from TSM and WAL files to the local line protocol file, obtain data from the line protocol file, and send the data to the destination GeminiDB Influx instance. This process may affect the performance of the source database. You are advised to run the migration tool during off-peak hours.
-  Reserve sufficient disk space because TSM and WAL file data needs to be extracted to the line protocol file.
-  The migration tool supports only InfluxDB 1.\ *X* Community Edition.

Prerequisites
-------------

-  The network between the source InfluxDB (Community Edition) instance and destination GeminiDB Influx instance is connected.
-  The corresponding database has been created and the retention policy has been configured in the destination GeminiDB Influx instance.

Procedure
---------

To migrate data from InfluxDB (Community Edition) to GeminiDB Influx API, contact technical support.

Migration Performance Reference
-------------------------------

-  Migration environment:

   -  Source: Deploy a single-node InfluxDB instance and the migration tool on an ECS with 4 vCPUs and 16 GB of memory.
   -  Destination: Deploy a three-node GeminiDB Influx instance with 4 vCPUs and 16 GB of memory.

-  Migration performance:

   -  The data export rate of a single process on the source database is 1 GB/min.
   -  The import rate of a single thread on the destination database is 1 GB/min.
