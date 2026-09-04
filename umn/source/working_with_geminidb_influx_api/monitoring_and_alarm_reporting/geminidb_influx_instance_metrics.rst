:original_name: nosql_09_0036.html

.. _nosql_09_0036:

GeminiDB Influx Instance Metrics
================================

Description
-----------

This section describes GeminiDB metrics reported to Cloud Eye as well as their namespaces and dimensions. You can use APIs provided by Cloud Eye to query the metrics of the monitored object and alarms generated for GeminiDB.

Namespace
---------

SYS.NoSQL

Metrics
-------

.. table:: **Table 1** Metrics

   +-------------------------------+---------------------------+--------------------------------------+-------------+-------------------------------------------------+--------------------------------+
   | Metric ID                     | Metric Name               | Description                          | Value Range | Monitored Object                                | Monitoring Interval (Raw Data) |
   +===============================+===========================+======================================+=============+=================================================+================================+
   | gemini001_cpu_usage           | CPU Usage                 | CPU usage of the monitored system    | 0-100       | Measured object: ECS                            | 1 minute                       |
   |                               |                           |                                      |             |                                                 |                                |
   |                               |                           | Unit: %                              |             | Monitored object: GeminiDB instance             |                                |
   +-------------------------------+---------------------------+--------------------------------------+-------------+-------------------------------------------------+--------------------------------+
   | gemini002_mem_usage           | Memory Usage              | Memory usage of the monitored system | 0-100       | Measured object: ECS                            | 1 minute                       |
   |                               |                           |                                      |             |                                                 |                                |
   |                               |                           | Unit: %                              |             | Monitored object: GeminiDB instance             |                                |
   +-------------------------------+---------------------------+--------------------------------------+-------------+-------------------------------------------------+--------------------------------+
   | gemini003_bytes_out           | Network Output Throughput | Outgoing traffic in bytes per second | >= 0        | Measured object: ECS                            | 1 minute                       |
   |                               |                           |                                      |             |                                                 |                                |
   |                               |                           | Unit: kbit/s                         |             | Monitored object: GeminiDB instance             |                                |
   +-------------------------------+---------------------------+--------------------------------------+-------------+-------------------------------------------------+--------------------------------+
   | gemini004_bytes_in            | Network Input Throughput  | Incoming traffic in bytes per second | >= 0        | Measured object: ECS                            | 1 minute                       |
   |                               |                           |                                      |             |                                                 |                                |
   |                               |                           | Unit: kbit/s                         |             | Monitored object: GeminiDB instance             |                                |
   +-------------------------------+---------------------------+--------------------------------------+-------------+-------------------------------------------------+--------------------------------+
   | influxdb001_series_num        | Time Series               | Total number of time series          | >= 0        | Monitored object: database                      | 1 minute                       |
   |                               |                           |                                      |             |                                                 |                                |
   |                               |                           | Unit: count                          |             | Monitored object: GeminiDB Influx instance node |                                |
   +-------------------------------+---------------------------+--------------------------------------+-------------+-------------------------------------------------+--------------------------------+
   | influxdb002_query_req_ps      | Query Requests Per Second | Number of query requests per second  | >= 0        | Monitored object: database                      | 1 minute                       |
   |                               |                           |                                      |             |                                                 |                                |
   |                               |                           | Unit: count/second                   |             | Monitored object: GeminiDB Influx instance node |                                |
   +-------------------------------+---------------------------+--------------------------------------+-------------+-------------------------------------------------+--------------------------------+
   | influxdb003_write_req_ps      | Write Requests Per Second | Number of write requests per second  | >= 0        | Monitored object: database                      | 1 minute                       |
   |                               |                           |                                      |             |                                                 |                                |
   |                               |                           | Unit: count/second                   |             | Monitored object: GeminiDB Influx instance node |                                |
   +-------------------------------+---------------------------+--------------------------------------+-------------+-------------------------------------------------+--------------------------------+
   | influxdb004_write_points_ps   | Write Points              | Number of write points per second    | >= 0        | Monitored object: database                      | 1 minute                       |
   |                               |                           |                                      |             |                                                 |                                |
   |                               |                           | Unit: count/second                   |             | Monitored object: GeminiDB Influx instance node |                                |
   +-------------------------------+---------------------------+--------------------------------------+-------------+-------------------------------------------------+--------------------------------+
   | influxdb005_write_concurrency | Concurrent Write Requests | Number of concurrent write requests  | >= 0        | Monitored object: database                      | 1 minute                       |
   |                               |                           |                                      |             |                                                 |                                |
   |                               |                           | Unit: count                          |             | Monitored object: GeminiDB Influx instance node |                                |
   +-------------------------------+---------------------------+--------------------------------------+-------------+-------------------------------------------------+--------------------------------+
   | influxdb006_query_concurrency | Concurrent Queries        | Number of concurrent query requests  | >= 0        | Monitored object: database                      | 1 minute                       |
   |                               |                           |                                      |             |                                                 |                                |
   |                               |                           | Unit: count                          |             | Monitored object: GeminiDB Influx instance node |                                |
   +-------------------------------+---------------------------+--------------------------------------+-------------+-------------------------------------------------+--------------------------------+
   | nosql005_disk_usage           | Storage Space Usage       | Storage usage of a monitored object  | 0-100       | Monitored object: database                      | 1 minute                       |
   |                               |                           |                                      |             |                                                 |                                |
   |                               |                           | Unit: %                              |             | Monitored object: GeminiDB Influx instance node |                                |
   +-------------------------------+---------------------------+--------------------------------------+-------------+-------------------------------------------------+--------------------------------+
   | nosql006_disk_total_size      | Total Storage Space       | Disk size of a monitored object      | >= 0        | Monitored object: database                      | 1 minute                       |
   |                               |                           |                                      |             |                                                 |                                |
   |                               |                           | Unit: GB                             |             | Monitored object: GeminiDB Influx instance node |                                |
   +-------------------------------+---------------------------+--------------------------------------+-------------+-------------------------------------------------+--------------------------------+
   | nosql007_disk_used_size       | Used Storage Space        | Used storage of a monitored object   | >= 0        | Monitored object: database                      | 1 minute                       |
   |                               |                           |                                      |             |                                                 |                                |
   |                               |                           | Unit: GB                             |             | Monitored object: GeminiDB Influx instance node |                                |
   +-------------------------------+---------------------------+--------------------------------------+-------------+-------------------------------------------------+--------------------------------+

Dimensions
----------

+--------------------------------------+-------------------------------------------------------+
| Key                                  | Value                                                 |
+======================================+=======================================================+
| influxdb_cluster_id.influxdb_node_id | Cluster ID or node ID of the GeminiDB Influx instance |
+--------------------------------------+-------------------------------------------------------+
