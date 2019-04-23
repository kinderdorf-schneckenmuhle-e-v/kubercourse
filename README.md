# Kubernetes Cluster
* NOTE: This document is still under construction

## Deploying a Lightweight Environment with k3s
A lightweight cluster can be setup semi-automatically by executing `curl -sfL https://get.k3s.io | sh -` on the server shell. 
Verify the installation by executing `k3s kubectl get node` - it should display the actual node.

## Firewall Rules
To allow inter-pod communication, following cluster-related firewall rules must be set:
```
firewall-cmd --permanent --direct --add-rule ipv4 filter INPUT 1 -i cni0 -s 10.42.0.0/16 -j ACCEPT
firewall-cmd --permanent --direct --add-rule ipv4 filter FORWARD 1 -s 10.42.0.0/15 -j ACCEPT
```
and loaded by executing `firewall-cmd --reload`.

[WIP]
