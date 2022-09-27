---
title: "System Boot Screens"
description: "This article provides information on the boot environment screens and settings."
weight: 40
alias:
tags:
 - scaleboot
---

{{< toc >}}

The **System > Boot** screen displays a list of boot environments on the TrueNAS system. Each time the system updates to a new software release it creates a new boot environment.

![SystemBootScreenSCALE](/images/SCALE/22.02/SystemBootScreenSCALE.png "System Boot Screen")

Each boot environment on the list includes:

* **Name** which is the name of the boot entry as it appears in the boot menu
* **Active** that indicates which entry boots by default if a boot environment is not active. Activated environment displays **Non/Reboot**.
* **Created** that shows creation date and time, **Space** that shows boot environment size
* **Keep** that indicates whether TrueNAS deletes this boot environment when a system update does not have enough space to proceed.

### Batch Operations

Select the checkbox(es) for each boot environment displays the **Batch Operations** that allows you to delete the selected environments at one time.

![BootBatchOperationsOption](/images/SCALE/22.02/BootBatchOperationsOption.png "Batch Operations Boot Screen")

The <i class="fa fa-ellipsis-v" aria-hidden="true" title="Options"></i> displays a list of boot environment actions that change based on whether it is activated or not.

### Boot Environment Actions Lists

The <i class="fa fa-ellipsis-v" aria-hidden="true" title="Options"></i> for an environment displays actions available to that environment. 

| Action | Boot State | Description |
|--------|------------|-------------|
| **Activate** | Deactivated | Opens the **Activate** dialog. Changes the **System Boot** screen status to **Reboot** and changes the current **Active** entry from **Now/Reboot** to **Now**, indicating that it is the current boot environment but is not used on next boot. |
| **Clone** | Both states | Opens the **Clone Boot Environment** window. Copies the selected boot environment into a new entry. Enter a new name using only alphanumeric characters, and/or the allowed dashes (-), underscores (_), and periods (.) characters. |
| **Delete** | Deactivated | Opens the **Delete** dialog. Does not display if the boot environment is activated/ You cannot deleted the default or activated boot environment. Removes the highlighted entry and also removes that entry from the boot menu.  |
| **Rename** | Both states | Opens the **Rename Boot Environment** window. Enter a new name using only alphanumeric characters, and/or the allowed dashes (-), underscores (_), and periods (.) characters. |
| **Keep** | If set to false | Opens the **Keep** dialog, and toggles the boot environment action to **Unkeep**. Use to prevent the TrueNAS updater from automatically deleting the environment to make more space for a new environment when there is insufficient space for it. |
| **Unkeep** | If **Keep** is set to **True** | Opens the **Unkeep** dialog, and toggles the boot environment action to **Keep**. Use to allow TrueNAS updater to automatically delete the environment to make space for a new boot environment when there is not enough space for it. |

### System Boot Actions

**ACTIONS** at the top right corner of the **System > Boot** screen displays four options.

|Setting | Description |
|--------|-------------|
| **Add** | Opens the **Create Boot Environment** window where you make a new boot environment from the active environment. Enter a new name using only alphanumeric characters, and/or the allowed dashes (-), underscores (_), and periods (.) characters. |
| **Stats/Settings** | Opens the **Stats/Settings** window with the **Boot pool Condition**, **Size** and **Used**, and **Last Scrub Run** statistics for the operating system device, and provides the option to change the default duration between the operating system device scrubs from every 7 days to a new duration in days. |
| **Boot Pool Status** | Opens the **[Boot Pool Status]() screen that displays the status of each device in the operating system device (boot pool), and lists any read, write, or checksum errors. |
|**Scrub Boot Pool** | Opens the **Scrub** dialog. Performs a manual data integrity check (scrub) of the operating system device. |

## Boot Pool Status Screen

The **System > Boot > Status** screen shows the **Boot Pool Status** of the current **boot-pool**. It includes the current status, the path, and the number of read, write and checksum errors.

![BootPoolStatusScreenSCALE](/images/SCALE/22.02/BootPoolStatusScreenSCALE.png "Boot Pool Status")

The <i class="fa fa-ellipsis-v" aria-hidden="true" title="Options"></i> displays two options, **Attach** or **Replace**.

### Attach Screen
The boot status **Attach** screen settings specify a device as the disk member and how much of the device is used.

![BootStatusAttachScreenSCALE](/images/SCALE/22.02/BootStatusAttachScreenSCALE.png "Boot Status Attach")

Select a device from the **Member Disk** dropdown. 

Select **Use all disk space** to use the entire capacity of the new device.

### Replace Screen

**Replace** settings specify a replacement device from the **Member Disk** dropdown

![BootStatusReplaceScreenSCALE](/images/SCALE/22.02/BootStatusReplaceScreenSCALE.png "Boot Status Replace")

To return to the **System > Boot** screen, click **Boot** in the breadcrumb header.

{{< taglist tag="scaleboot" limit="10" >}}