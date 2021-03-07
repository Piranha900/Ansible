# Kubernetes Cluster using Ansible
* Clone repository.
* Change the “ad_addr” in the env_variables file with the IP address of the Kubernetes master node.
* Run the following command to setup the Kubernetes Master node.


```
ansible-playbook setup_master_node.yml
```
* Once the master node is ready, run the following command to set up the worker nodes.

```
ansible-playbook setup_worker_nodes.yml
```

* Once the workers have joined the cluster, run the following command to check the status of the worker nodes.
```
kubectl get nodes
```

## Additional information
* The IP addresses of the workers and masters added to the /etc/hosts file on all workers and masters as part of the [prerequisites.yml](centos/playbooks/prerequisites.yml) playbook,
if necessary or in case of DNS issues make sure the addresses have been added to /etc/hosts file.



## Bind/unbind etcd
* For bind/unbind node from etcd cluster you need to to:
```
- etcdctl --endpoints 127.0.0.1:2379 --cacert /etc/kubernetes/pki/etcd/ca.crt --cert /etc/kubernetes/pki/etcd/server.crt --key /etc/kubernetes/pki/etcd/server.key member list
- etcdctl --endpoints 127.0.0.1:2379 --cacert /etc/kubernetes/pki/etcd/ca.crt --cert /etc/kubernetes/pki/etcd/server.crt --key /etc/kubernetes/pki/etcd/server.key member remove <node_id>

```
