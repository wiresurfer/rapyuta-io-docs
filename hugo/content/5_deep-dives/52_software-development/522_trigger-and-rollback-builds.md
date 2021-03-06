---
title: "Builds: Trigger and Rollback"
description:
type: developer-guide
date: 2019-10-25T12:39:12+05:30
# pre: "c. "
weight: 522
tags:
    - Deep Dive
---

## Trigger and Rollback

As a developer, you may want to trigger a new build or rollback to a previous build generation. 
The rapyuta.io **Development>Builds** allows you to do that.

In the **Development>Builds** page select the particular build from the build list and click on **SHOW MORE**, 
this will open the **Details** tab of the selected build. 
It displays information on the build, current build generation number, git repository, etc. 

Suppose the current build generation number is _i_. If you update the
source code in the git repository, you may want to trigger a new build to reflect the new code changes. 
As a result, a new build generation number _(i+1)_ is generated. To trigger a new build, 
select the particular build and click **Trigger build** for that build.

You may always **Trigger** a new build irrespective of the status of the previous
build. That is you can trigger a new build from either a **Complete** build or an
**Error** build.

When you trigger a new build, a pop-up message appears and prompts whether you want to use the default trigger/tag name or use different names for the build. If you select **Yes**, the build is triggered with the default trigger/tag name. If you select **No**, the **Trigger Build** dialog-box appears and you can add a different trigger and tag name for the build.

  ![goo](/images/core-concepts/builds/build-creation/trigger-build.png?classes=border,shadow&width=30pc)


{{% notice note %}}

Packages which have builds that are in **Complete** status are suitable for deployment. The **InProgress** and **Failed** builds are unfit for deployment.

{{% /notice %}}

You may also view details such as the git repository URL where the source code is hosted, 
the latest commit SHA number, the commit message, the commit owner’s name, and the docker image  by clicking **View details/logs** in the **Build history** tab of the build.

![View details or logs](/images/core-concepts/builds/trigger-rollback-view-deails.png?classes=border,shadow&width=50pc)

You may also **Rollback** to a previous build generation number if there
is any, irrespective of the previous build status. Rollbacking to a
previous build does not restart the build process. Instead, on using the build 
in next deployment it would run the corresponding docker image that was generated for that build generation.

The **Current build generation** number (Gen) is shown below the build ID.

![Current build generation number](/images/core-concepts/builds/current-build-number.png?classes=border,shadow&width=30pc)


The builds are automatically restarted on rapyuta.io platform internal failures.
Click **Refresh** if you observe that the build logs are abruptly disconnected or stopped.

When a build fails, it is recommended to check the corresponding [build logs]({{< ref "/3_how-tos/35_tooling_and_debugging/354_view-deployment-logs" >}}) to debug. It can be due to multiple reasons like:

1. Repository access issue
2. Incorrect context directory path
3. Incorrect catkin parameters
4. Incorrect docker file path