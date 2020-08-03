# Kubernets Monitopia

Kubernets Monitopia is a single node Kubernetes setup that provides the following applications:

* Alerta
* Prometheus
* Nagios
* Grafana

The goal of this is to provide an example of how to build and deploy a monitoring stack using Kubernetes.

# Setup

Kubernets Monitopia uses Vagrant for deployments.  This allows you to quickly create a sandbox environment
where you can test this deployment.

## CentOS/7 Installation Via Vagrant 

Deploy a single CentOS/7 host via the `Vagrant` file.
```
vagrant up
```
This will deploy a single CentOS/7 host.  The `bootstrap.sh` file will provision Kubernetes onto the node.
Once the machine has come up, you should then log on and run the `user-k8.sh` script to deploy flannel and
to configure kubectl for the `vagrant` user.

## Configure NGINX

Since we are running Kubernetes on a single (virtual) bare metal host, we will need to use NGINX as our
inbound proxy.

## Deploy Applications Using Kubernetes

Several Kubernetes deployment files are included which will allow you to deploy Alerta, Prometheus, Nagios and
Grafana.

# Operations

## NGINX 

NGINX will need to be restarted anytime you have one of the proxy forwarding targets changed.  Use
`ngnix -s reload` to do so.
