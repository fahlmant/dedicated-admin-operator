# Dedicated Admin Operator

## Summary
The Dedicated Admin Operator was created for the OpenShift Dedicated platform to manage permissions (via k8s RoleBindings) to all the projects/namespaces owned by the clients. The idea is to monitor the creation of new namespaces and add the proper permissions for the dedicated-admins, a group of local admin (not cluster admins) managed by the client.

It contains the following components:

* Dedicated Admin Namespace controller: watches for new namespaces and guarantees that the proper RoleBindings are assigned to them. 

To avoid giving admin permission to infra/cluster-admin related namespaces, a blacklist is used (stored in a ConfigMap) to determine which namespaces should get the RoleBinding assignment.

## Metrics
The Dedicated Admin Operator exposes the following metrics to Prometheus:

* dedicated_admin_blacklisted: counter of blacklisted namespaces


