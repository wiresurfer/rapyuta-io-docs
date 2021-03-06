---

title: "ROS Routed Network"
intro: rapyuta.io is a platform that enables robotics solution development by providing the necessary software infrastructure and facilitating the interaction between multiple stakeholders who contribute to the solution development.

weight: 531
draft: true

versions:
  free-pro-team: '*'
  enterprise-server: '*'

layout: false
permissions: 'rapyuta.io'

showMiniToc: true
miniTocMaxHeadingLevel: 4

allowTitleToDifferFromFilename: false
mapTopic: false
hidden: false


redirect_from: []
gettingStartedLinks : []
popularLinks: []
guideLinks: []
introLinks: {}
tags:
    - Deep Dive
---
The routed network is a rapyuta.io resource to enable ROS communication between different ROS package deployments. Binding a routed network resource to your deployment will enable other deployments on the same routed network to consume ROS topics/services/actions as defined in the package. 
Data flow occurs only when another package chooses to subscribe to a topic, call a service or call an action. 

#### Illustrated Example
For this illustration let's assume the following network and packages.

* You have a routed network __networkN__
* You have __PackageA__ publishing _“topicA”_
* You have __PackageB__ publishing _“serviceB”_

We deploy the packages described above in the following configuration.

* Deploy __PackageA__ binding to routed network __networkN__ as _DeploymentA_
* Deploy __PackageB__ binding to routed network __networkN__ as _DeploymentB_

The result is as follows 

* ROS nodes in  _DeploymentA_ can now call _“serviceB”_
* ROS nodes in  _DeploymentB_ can now subscribe to _“topicA”_

A routed network can be deployed to a cloud or a device.


## Cloud Routed Network

When a user deploys a routed network to the cloud it is considered a cloud routed network. Any compute resources (CPU/memory) consumed by this routed network deployment count against your cloud deployment hours quota.

Package deployments in the cloud __OR__ device can bind to a cloud routed network.

When creating a cloud routed network, the Resource limit field define the memory allocation and computational ability of the routed network. These resources are reserved in the platform for effective ROS communication. You can choose the resource limit of a routed network based on the following requirements.

* size of ROS messages
* frequency of ROS messages
* number of topics/services/actions
* QOS of ROS message
* number of publishers/subscribers that will be active under a particular routed network

## Device Routed Network

In certain cases where communication is latency-sensitive or has high throughput, the user can choose to deploy a routed network to a device. While avoiding a round trip of information to the cloud minimizes latency and allows for better throughput **ONLY** deployments on devices on the same local area network can bind to it.

Routed networks can be deployed to a device with the following parameters:

* **Device**: Any online device with docker runtime and AMD64 architecture
* **Device IP Interface**: network interface (i.e., an IP address) that will be used by other deployments for communication to this routed network.
* **Restart policy**: Kindly refer to the restart policy.
On reboot, devices configured using DHCP may boot up with a new IP address and the network configuration of a deployed routed network becomes invalid. This can be avoided by assigning a static IP to the device you intend to deploy a routed network to esp in production systems.


