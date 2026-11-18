:original_name: nosql_introduction.html

.. _nosql_introduction:

What Is GeminiDB?
=================

GeminiDB is a distributed, multi-model NoSQL database service with decoupled compute and storage architecture. This high availability database is secure and scalable, can be deployed, backed up, or restored quickly, and includes monitoring and alarm management. GeminiDB Cassandra, GeminiDB Influx, GeminiDB DynamoDB-Compatible APIs are compatible with the corresponding mainstream NoSQL databases, Cassandra, InfluxDB, and DynamoDB. With superior I/O performance and low costs, they are well suited to IoT, meteorology, Internet, and gaming sectors.

GeminiDB Cassandra API
----------------------

GeminiDB Cassandra API is a cloud-native NoSQL database compatible with Cassandra. It supports Cassandra Query Language (CQL), which gives you SQL-like syntax. It is secure, reliable, scalable, and easy to manage and can provide high read/write performance.

-  A multi-layer security system, including a VPC, subnet, security group, and SSL, ensures database security and user privacy. You can deploy nodes across three AZs and create backups or restore data with ease. The distributed architecture provides superlative fault tolerance (N-1 reliability).
-  GeminiDB Cassandra API gives you 3 times the performance of the open source version. Data can be written to this high availability database 24/7, and with automated load balancing and elastic scaling, you always have all the performance you need.
-  The distributed architecture, with decoupled compute and storage, means that compute nodes can be expanded in minutes, and storage capacity can be scaled up in seconds without affecting your services.
-  On the visualized instance management console, you can create or delete instances in just a few clicks. Backup and restoration, configuring alarms or adding nodes is just as easy.

GeminiDB Influx API
-------------------

GeminiDB Influx API is a cloud-native NoSQL time-series database with decoupled storage and compute and is full compatible with InfluxDB. This high availability database is secure and scalable, can be deployed, backed up, or restored quickly, and offers monitoring and alarm management capabilities. You can also add storage or compute resources separately. It is widely used to monitor resources, services, IoT devices, and industrial production processes, evaluate production quality, and trace faults. GeminiDB Influx API supports highly-concurrent reads and writes, compressed storage, and SQL-like queries, multi-dimensional aggregation computing, and GUI-based data analysis.

-  It is widely used to monitor resources, services, IoT devices, and industrial production processes, evaluate production quality, and trace faults.
-  It meets the demand of high concurrent read and write, compressed storage, and SQL-like query.
-  It supports multi-dimensional aggregation computing and visualized data analysis.

GeminiDB DynamoDB-Compatible API
--------------------------------

GeminiDB is fully compatible with Amazon DynamoDB, allowing you to access GeminiDB DynamoDB-Compatible API through DynamoDB SDKs or CLIs and smoothly migrate data from DynamoDB to GeminiDB without application refactoring. GeminiDB DynamoDB-Compatible API is secure, reliable, and free from the constraints of closed-source software.

-  Security and reliability

   -  A multi-layer security system, including VPCs, subnets, and security groups, ensures database security and user privacy.
   -  Cross-region active-active disaster recovery (DR) is supported, allowing you to deploy an instance across three AZs and quickly back up or restore data.
   -  The distributed architecture provides superior fault tolerance for up to *N*-1 node failures.

-  No constraints of closed-source software

   -  Storage can be scaled in seconds without affecting workloads.
   -  Compute nodes can be added in minutes, with any resulting jitter lasting only a few seconds.
