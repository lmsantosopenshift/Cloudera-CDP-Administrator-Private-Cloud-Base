### Conceptos Cloudera

```
Environments: 
DH CLuster: refers to a workload cluster created and managed by Cloudera Data Hub. These clusters are designed to run specific workloads such as data engineering or data analytics.
DW (Data Warehouse) cluster refers to a cluster specifically designed for data warehousing workloads.
ML (Machine Learning) cluster.
```

### CDP Control Plane
```
Data Catalog
Replication Manager
Workload Manager
Management Console
```
### CDP Private Cloud Base Installation
Managing Multiple Hosts in a Cluster

```
Use automated OS deployment tools for commissioning many hosts (Kikstart Files)
Use configuration management tools to manage the underlying OS (Ej Ansible)
Use Cloudera Manager to install and manage cluster software
```

### Adding a Cluster
Adding a cluster consists of two steps:

```
Add a set of hosts and install Cloudera Runtime and the CM Agent
Select and configure the services to run on the new cluster
```
### Stale Configurations
```
A modified configuration may require one or both of the following
─ Client redeployment
─ Role instance restart or refresh
```
