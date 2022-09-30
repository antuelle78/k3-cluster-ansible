K3S HA CLUSTER WITH ANSIBLE
===========================

Simple deployment of k3s HA cluster with embedded database.

REF: https://rancher.com/docs/k3s/latest/en/installation/ha-embedded/

Requirements
------------

**OS:** Ubuntu 20.04/22.04

**RAM:** 2GB minimum per node

**CPU:** 2 CPU minimum per node

*HA:*** At least three nodes are required to achive high availability

Role Variables
--------------

**k3s_version:** default v1.25.0+k3s1

**master_ip:** IP address of first node

**master_server:** Inventory hostname of first node

**token:** Shared secret for join nodes to the cluster

**k3s_url:** FQDN configured for cluster access

**VARIBLES ARE SET IN:**

https://github.com/antuelle78/k3-cluster-ansible/blob/main/k3s_cluster/defaults/main.yml


How to use:
-----------

Prepare an inventory file and then run the deploy.yml playbook: 

    ---

    all:
      hosts:
        k3s-server-4:
          ansible_host: 10.0.245.201
        k3s-server-5:
          ansible_host: 10.0.245.90
        k3s-server-6:
          ansible_host: 10.0.245.204
      vars:
        ansible_user: admin


License
-------

GPLv3

Author Information
------------------

**Name:** Michael Nelson

LET'S GET IT AUTOMATED AND BE LAZY :<)

