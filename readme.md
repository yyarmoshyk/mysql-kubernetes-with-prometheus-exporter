## Description
The primary purpose of this repository is to share the instructions how to deploy and configure a mysql instance in the cluster with persistent storage.
It is recommended to use the pre-defined helm chart for this. There is a set of customisations that we need to apply and this is why I've prepared the customised `values.yaml`

The following default values were updated:
* mysqlRootPassword
* mysqlUser
* mysqlPassword
* mysqlDatabase
* configurationFiles.mysql.cnf
* metrics.enabled
* metrics.annotations
* metrics.flags

Most of these changes can be provided using `--set` argument, but I'm not really sure how to provide `metrics.annotations` and `configurationFiles.mysql.cnf`.
The `metrics.annotations` is required to run the `mysqld-exporter` container in the pod to export metrics into `Prometheus`.
Custom `mysql.cnf` is required to enable `slow_query_log`.

## Installation
```bash
helm install mysql-sample -f values.yaml stable/mysql
```
