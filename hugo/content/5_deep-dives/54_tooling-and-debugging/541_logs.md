---

title: "Logs"
intro: rapyuta.io is a platform that enables robotics solution development by providing the necessary software infrastructure and facilitating the interaction between multiple stakeholders who contribute to the solution development.

weight: 541

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
## Logs

Logs are verbose text messages and are used for debugging and monitoring. Logs are generated when rapyuta.io builds the source code of a git repository, by a device and during the life cycle of deployment.

rapyuta.io collects and indexes log data. There are three types of logs produced:

* [Build Logs](/3_how-tos/35_tooling_and_debugging/debugging-logs/#build-logs)
* [Deployment Logs](/3_how-tos/35_tooling_and_debugging/debugging-logs/#deployment-logs)
* [Device Logs](/3_how-tos/35_tooling_and_debugging/debugging-logs/#device-logs)

All types of logs are available only for seven days, after which they are automatically destroyed.