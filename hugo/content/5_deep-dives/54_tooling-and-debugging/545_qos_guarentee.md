---

title: "QOS Guarantee"
intro: rapyuta.io is a platform that enables robotics solution development by providing the necessary software infrastructure and facilitating the interaction between multiple stakeholders who contribute to the solution development.

weight: 546

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

The QoS guarantee level is an agreement between the sender of a message and the receiver of a message that defines the guarantee of delivery for a specific message. In rapyuta.io, the messages are generally metrics or logs of a device, which are sent to rapyuta.io servers.

QoS guarantee levels described here are different from the QoS guarantee that you set while adding a new rapyuta.io package.

There are three QoS levels:

* Low
* Medium
* High

## Low QoS guarantee

The minimum QoS level is Low. This level guarantees best-effort delivery but delivers with some data loss. Use Low QoS level when you have a completely or mostly stable connection between sender and receiver, or if the loss of data (metrics or logs) is acceptable. It is suggested to set the QoS level to low when the rate of data generation is high to reduce the overhead cost and lower the latency while sending messages.

## Medium QoS guarantee

Medium QoS level guarantees that metrics or logs are delivered at least once to the receiver. The data can be delivered multiple times. Use Medium QoS level when you need to get every data, and your application can tolerate duplicates and be able to process them accordingly.

## High QoS guarantee

The maximum QoS level is High. This level guarantees that each metric or log is received only once by the receiver. It is the safest and slowest QoS level. Use a High QoS level if it is critical to your application to receive all data exactly once or if a duplicate delivery can harm your application users or subscribing clients. Selecting a high QoS level when the rate of data generation is high will lead to high overhead costs and high latency while sending messages, which you might not want to do.