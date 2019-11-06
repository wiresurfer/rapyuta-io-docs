---
title: "Device Logs"
description:
type: developer-guide
date: 2019-10-25T13:23:38+05:30
pre: "c. "
weight: 525
---
By default, device logs are not collected until you explicitly subscribe to a
ROS topic in case of ROS deployments.

Before viewing device logs, it is necessary to have the ROS Master up and running.
Add a _ROS Publisher_ package that has a _Talker_ component with device runtime.
It publishes */telemetry* ROS topic with **High** **QoS**.

1. On left navigation bar, click **Devices**.
2. Select a device whose device logs you want to view. In this example,
   _ROS Publisher Subscriber Device_ is selected.
3. Under **Logs** tab, to subscribe to a ROS topic, click **Subscribe** against
   the topic. In this example, the topic `/telemetry` is subscribed to.
   Ensure the status of the subscribed topic(s) is **Subscribed** and is highlighted
   in green.

![To subscribe](/images/core-concepts/logging/device-logs/yet-to-subscribe.png?classes=border,shadow&width=60pc)

Once you subscribe to a topic, the device logs are displayed in the
_logging area_ (a terminal-like window).

Initially, you will see the latest 500 logs in the logging area. As you scroll
up to the top of the terminal window previous 500 logs are displayed. You may
continue scrolling up till all the logs are exhausted.

![Logging Area](/images/core-concepts/logging/device-logs/logging-terminal-window.png?classes=border,shadow&width=60pc)

To get updated logs, scroll down to the bottom of the logging area, and then
click **Get recent logs**.

To switch between the topics, click the drop-down list (at the top-left corner
of logging area) and select one of the subscribed topics. A tick mark against
the topic `/telemetry` indicates that you are currently viewing the logs
belonging to `/telemetry`.

You can search the logs for matching phrases using the **Search** bar. All
occurrences of a match are highlighted.

If you prefer to view the timestamp of every log displayed in the logging area,
select **Show timestamps** checkbox.

Topics such as `/rosout` and `/rosout_agg` are already available for a
ROS-based device.

## Batch Upload
You can upload logs collected from a device (like dmesg,
journalctl, rosbags etc.) to rapyuta.io. This lets you:

* *Save* logs for future reference. The logs are saved to the
  cloud storage.
* *Process* and *analyze* logs for insights as per your requirements.

The log data can be text, images or videos. You can upload
log files by clicking on the **Upload** button, which
is found on the device's **Manage** tab.
![Manage Tab](/images/core-concepts/logging/device-logs/upload-logs/manage-tab.png?classes=border,shadow&width=40pc)

A list of statuses indicates the progress of an ongoing upload.
They are:

* **In Progress**: uploading a log file (to the cloud storage) is underway.
* **Failed**: uploading a log file failed due to an error.
* **Complete**: uploading a log file (to the storage) is succeeded.
* **Cancelled**: ongoing process of uploading a log file is cancelled 

#### Parameters for Uploading Log Files
There are certain parameters to take care of while uploading a
log file from a device to rapyuta.io

When providing the absolute path of the log file ensure it does
not end with a backslash. Hence, folders are not supported. You are
only allowed to upload a single log file at a time.

Sometimes constrained resources can limit a device's ability to
execute tasks while uploading logs. For instance, a significant amount
of network bandwidth is consumed while uploading
enormous log data, which can affect execution of other high priority
tasks on the device. In this case, rapyuta.io lets you tune network
bandwidth based on the device and its environment limitations. This lets
you upload log files without interfering with task execution. You can
choose the upload rate value in ***Mega bytes***, or ***Giga bytes***.

Select the **purge** option to remove a log file from a device
after successfully uploading it to the cloud storage.

Select the **override** option to replace an existing log file
with a new log file with the same name.

**Metadata** lets you create static tags for log files while uploading.

![Upload Parameters](/images/core-concepts/logging/device-logs/upload-logs/upload-log-dialog-box.png?classes=border,shadow&width=40pc)

A summary of the log file is generated after completion as shown below:
![Summary Post Upload](/images/core-concepts/logging/device-logs/upload-logs/log-file-summary.png?classes=border,shadow&width=40pc)

After successfully uploading the log file:

*   ***view*** a list of all the log files that you uploaded for a device.
*   ***download*** a log file locally on your system.
*   ***delete*** a log file from the cloud storage.
*   ***filter*** list of log files based on upload status.
*   ***sort*** list of log files based on filename, file size and time of creation.