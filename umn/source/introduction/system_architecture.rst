:original_name: nosql_01_0001.html

.. _nosql_01_0001:

System Architecture
===================

GeminiDB is a distributed database store with decoupled storage and compute. Its compute cluster consists of multiple homogeneous nodes.

Data is stored in a distributed shared storage pool.

Compute and storage resources are decoupled from each other so they can be flexibly scaled in or out without having to migrate any data.
