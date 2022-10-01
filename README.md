K3S HA CLUSTER WITH ANSIBLE
===========================

Simple deployment of k3s HA cluster with embedded database and any number of
worker nodes.

REF: https://rancher.com/docs/k3s/latest/en/installation/ha-embedded/

Requirements
------------

**OS:** Ubuntu 20.04/22.04

**RAM:** 2GB minimum per node

**CPU:** 2 CPU minimum per node

***HA:*** At least three server nodes are required to achive high availability

Role Variables
--------------

**k3s_version:** default v1.25.2+k3s1

**master_ip:** IP address of first node

**master_server:** Inventory hostname of first node

**token:** Shared secret for join nodes to the cluster

**install_primary:** default "true", can be set to "fales" if we just want to

add nodes to an existing cluster

**install_secs:** default "true", if set to "false" only first server with

--cluster-init option will be configured

**k3s_url:** FQDN configured for cluster access

**VARIBLES ARE SET IN:**

https://github.com/antuelle78/k3-cluster-ansible/blob/main/k3s_cluster/defaults/main.yml

These values can be provided at launch if using the "deploy_intr.yml" playbook.


How to use:
-----------

Prepare an inventory file similar to the example below and then run the deploy.yml playbook:


    ---

    all:
      hosts:
        k3s-server-1:
          ansible_host: 10.0.245.201
        k3s-server-2:
          ansible_host: 10.0.245.90
        k3s-server-3:
          ansible_host: 10.0.245.204
        k3s-worker-1:
          ansible_host: 10.0.245.205
      vars:
        ansible_user: admin

**NOTE: Any node with the string "worker" in it's inventory name will be**

   **configured with the k3s-agent and added to the cluster as a woker node.**

```
ansible-playbook deploy.yml -i inventory.yml

```

To launch in interactive mode:

```
ansible-playbook deploy.yml -i inventory.yml

```

License
-------

GPLv3

Author Information
------------------

**Name:** Michael Nelson

LET'S GET IT AUTOMATED AND BE LAZY :<)

