# Metrics provided by the prometheus plugin

_Note: All metrics have common prefix (by default `opensearch_`). This prefix was omitted in the below lists._ 

## Cluster metrics

The following metrics are based on response of [Cluster health API](https://opensearch.org/docs/latest/opensearch/rest-api/cluster-health/).

| Name                                  | Type  | Labels        | Description                                                                                                                                                                                                                                    |
|:--------------------------------------|:------|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| cluster_status                        | gauge | cluster       | Cluster status. Possible values: \[0,1,2\].<br>0&nbsp;=&nbsp;Green, 1&nbsp;=&nbsp;Yellow, 2&nbsp;=&nbsp;Red.<br>Visit [Cluster health documentation](https://opensearch.org/docs/latest/opensearch/rest-api/cluster-health/) for more details. |
| cluster_nodes_number                  | gauge | cluster       | Number of all nodes in the cluster.                                                                                                                                                                                                            |                                                                                                                                                                                               
| cluster_datanodes_number              | gauge | cluster       | Number of data nodes in the cluster.                                                                                                                                                                                                           |                                                                                                                                                                                          
| cluster_shards_active_percent         | gauge | cluster       | Percent of active shards.                                                                                                                                                                                                                      |                                                                                                                                                                                                    
| cluster_shards_number                 | gauge | cluster, type | Number of shards.                                                                                                                                                                                                                              |                                                                                                                                                                                                            
| cluster_pending_tasks_number          | gauge | cluster       | Number of pending tasks.                                                                                                                                                                                                                       |
| cluster_task_max_waiting_time_seconds | gauge | cluster       | Max waiting time for tasks.                                                                                                                                                                                                                    |
| cluster_is_timedout_bool              | gauge | cluster       | Has the cluster health request timed out?                                                                                                                                                                                                      |
| cluster_inflight_fetch_number         | gauge | cluster       | Number of in flight fetches.                                                                                                                                                                                                                   |

Example:
```text
opensearch_cluster_status{cluster="opensearch",} 1.0
opensearch_cluster_nodes_number{cluster="opensearch",} 1.0
opensearch_cluster_datanodes_number{cluster="opensearch",} 1.0
opensearch_cluster_shards_active_percent{cluster="opensearch",} 50.0
opensearch_cluster_shards_number{cluster="opensearch",type="relocating",} 0.0
opensearch_cluster_shards_number{cluster="opensearch",type="active",} 1.0
opensearch_cluster_shards_number{cluster="opensearch",type="initializing",} 0.0
opensearch_cluster_shards_number{cluster="opensearch",type="unassigned",} 1.0
opensearch_cluster_shards_number{cluster="opensearch",type="active_primary",} 1.0
opensearch_cluster_pending_tasks_number{cluster="opensearch",} 0.0
opensearch_cluster_task_max_waiting_time_seconds{cluster="opensearch",} 0.0
opensearch_cluster_is_timedout_bool{cluster="opensearch",} 0.0
opensearch_cluster_inflight_fetch_number{cluster="opensearch",} 0.0
```

## Node metrics

| Name           | Type   | Labels        | Description |
|:---------------|:-------|:--------------|:------------|
| node_role_bool | gauge  | cluster, role | Node role.  |

Example:
```text
opensearch_node_role_bool{cluster="opensearch",node="Node-A1",nodeid="VC0d4RgbTM6kLDwuud2XZQ",role="master",} 1.0
opensearch_node_role_bool{cluster="opensearch",node="Node-A1",nodeid="VC0d4RgbTM6kLDwuud2XZQ",role="ingest",} 1.0
opensearch_node_role_bool{cluster="opensearch",node="Node-A1",nodeid="VC0d4RgbTM6kLDwuud2XZQ",role="data",} 1.0
opensearch_node_role_bool{cluster="opensearch",node="Node-A1",nodeid="VC0d4RgbTM6kLDwuud2XZQ",role="remote_cluster_client",} 1.0
```