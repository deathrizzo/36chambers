# RaspberryPi Cluster Setup

K3s Playground Setup. Work in progress. Should probably be blogged. 

## Description

Random playground project currently using three RaspberryPi's. Two Pi4's and one Pi3 all running Ubuntu Server 21.04. It will be growing. 

Purpose of this is to have the ability to "PLAY". Experiment with different tools.

AND JUST HAVE FUN!

## Goals - so far

* Run a local kubernetes cluster
* Use distributed block storage for persistent storage for pods.
* Setup Monitoring
* Setup centralized logging
* automate it for the bigger stage

## Getting Started

Be bored and Create.

### Dependencies

* RaspberryPi running Ubuntu 21.04
* Internet access

## Installing

### Install Ubuntu 21.04 on raspberrypi.

Use RaspberryPi Imager to install Ubuntu on each node. They will all communicate via WiFi. (INEEMONEY).

After installation modify /etc/netplan/50-cloud-init.yaml and plug in wifi information.

```
network:
    ethernets:
        eth0:
            dhcp4: true
            optional: true
    version: 2
    wifis:
        wlan0:
            optional: true
            access-points:
              "YourAccessPoint":
                  password: "YourPassword"
            dhcp4: true 
```

### Install k3s
https://rancher.com/docs/k3s/latest/en/quick-start/

Master
```
curl -sfL https://get.k3s.io | sh -
```
```
kubctl get node
```
Workers
```
curl -sfL https://get.k3s.io | K3S_URL=https://myserver:6443 K3S_TOKEN=mynodetoken sh -

```
replace myserver & mynodetoken with output from <b>/etc/rancher/k3s/k3s.yaml</b>

