---
title: "Hello World Web Application"
description:
type: dev-tutorials
date: 2019-04-26T16:27:32+05:30
pre: "a. "
weight: 405
---
An executable of a package can be a dockerfile. In that case, rapyuta.io
applies [dockerfile build strategy](/core-concepts/builds/#dockerfile-strategy)
while deploying the package. The tutorial illustrates this strategy, where
a dockerfile is built into a docker image.

## Learning objectives
The tutorial will show you how to use a dockerfile to build an executable
of a package.

## Prerequisites
1. Ensure that the [Google Chrome browser](https://www.google.com/chrome/)
   is installed on a computer.
2. You should be familiar with the [core concepts](/core-concepts/) of rapyuta.io

## Difficulty
Beginner

## Estimated time
10 minutes

## Tutorial walkthrough
You will add and deploy ***simple-hello-world*** package. To create a new package,
follow the below instructions in sequence:

1. On the left navigation bar, click **CATALOG**.
2. Click **ADD NEW PACKAGE**.
3. You should provide information about the package such as the name of the package, its version, whether its a singleton or bindable package and a short description.
   1. In the **Package Name** box, type in a name for the package like `simple-hello-world`
   2. In the **Package Version** box, type in the version of the package. By default, the version is set to *1.0.0*
   3. Ensure **Is a singleton package** is *not selected*.
   4. Make sure **Is a bindable package** is *selected*.
   5. Describe the package in a sentence or two like `Demo package for dockerfile build strategy`.
4. Click **NEXT**.
5. In the **Component Name** box, enter a name for the component say `Flask_Application`.
   {{% notice info %}}
   The name of a component must consist of alphabets [A-Z, a-z], digits [0-9], hyphen - and an underscore _ character. It must not begin with a digit.
   {{% /notice %}}
6. Select **Cloud** for **Component Runtime**.
7. Ensure **Is ROS Component** is *not selected*.
8. The value of **Replicas to run the component** is set to the default value of *1*
9.  In the **Executable Name** box, type in a name for the executable say `flask_runner`.
{{% notice info %}}
The name of an executable must consist of alphabets [A-Z, a-z], digits [0-9], hyphen - and an underscore _ character. It must not begin with a digit.
{{% /notice %}}
10. Select **Git** for **Executable Type**.
11. In the **Git Repository** box, enter the git repository's URL address: `https://github.com/rapyuta-robotics/io_tutorials`
12. In the **Context directory** box, enter the name of the parent directory that contains the dockerfile. In this example, it is `flask_helloworld`.
13. Select **Use docker build strategy**.
![Executable details](/images/tutorials/hello-world/exec-details.png?classes=border,shadow&width=50pc)
14. You must expose a network endpoint for viewing the output of the tutorial:
    1.  Click **Add Endpoint**.
    2.  Provide a name for the endpoint, like `HELLO_WORLD`, in the **Endpoint Name** box.
    3.  Make sure **Exposed exernally** is *selected*.
    4.  Click **HTTPS/WSS** under **Protocol**.
    5.  The value of **Port** is automatically set to *443* because the protocol is HTTPS/WSS.
    6.  In the **Target Port** box, enter `5000`.
![Network endpoint](/images/tutorials/hello-world/endpoint-details.png?classes=border,shadow&width=50pc)
15. Click **NEXT** > **CONFIRM PACKAGE CREATION**.

The package takes about five minutes to build the dockerfile in the *flask_helloworld* directory into a running docker container. You can
analyze the corresponding [build logs](/core-concepts/logging/build-logs/)
for debugging failing builds.

A flickering yellow dot next to the package name indicates that the
**Build Status** is **BuildInProgress**, while a green dot indicates
that the **Build Status** is **Complete**.

![Package build](/images/tutorials/hello-world/build-pkg-success.png?classes=border,shadow&width=50pc)

Additionally, you may verify if the package is built successfully and is
ready to be deployed by checking to see if the **Deploy package** button is
active.

To deploy the ***simple-hello-world*** package, walk through the below
instructions in sequence:

1. On the left navigation bar, click **CATALOG**.
2. Select *simple-hello-world* package.
3. Click **Deploy package**.
4. In the **Name of deployment** box, enter the name of the deployment you are creating like `Simple Flask Application`.
5. Click **CREATE DEPLOYMENT** > **Confirm**.

You will be redirected to the **Details** page of the newly created deployment.
The **Simple Flask Application** deployment is successfully running only when
the green colored bar moves to **Succeeded** and **Status:Running** indicating that
the **DEPLOYMENT PHASE** is **Succeeded** and the **STATUS** is **Running**.

![Deployment details](/images/tutorials/hello-world/successful-deployment.png?classes=border,shadow&width=50pc)

You can also analyze the corresponding [deployment logs](/core-concepts/logging/deployment-logs/) to check if everything is working as expected by clicking on **Historical Logs** or **Live Logs** tab.

Once the package is successfully deployed, the **NETWORK ENDPOINTS** generates a
URL address on the **Details** page. Copy this specific URL address (it may be different
from that shown in the below image), paste in the web browser and press *Enter*.

![Network endpoint](/images/tutorials/hello-world/network-endpoint.png?classes=border,shadow&width=50pc)

You will view ***Hello from rapyuta.io*** message.