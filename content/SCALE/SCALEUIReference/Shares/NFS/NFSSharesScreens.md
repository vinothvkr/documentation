---
title: "NFS Shares Screens"
description: "This article provides information on NFS Shares screens and settings."
weight: 50
aliases: 
tags:
 - scalenfs
 - scaleshares
---

{{< toc >}}

The **Sharing** screen opens after you click **Shares** on the main navigation panel.  

## Unix (NFS) Share Widget
The **Unix (NFS) Share <span class="material-icons">launch</span>** widget includes the widget toolbar that displays the status of the NFS service and the **Add** button. 
After adding NFS shares, the widget displays a list of the shares below the toolbar.

![NFSShareWidgetNoShare](/images/SCALE/22.02/NFSShareWidgetNoShare.png "Unix (NFS) Share Widget")

After adding the first NFS share, the system opens an enable service dialog. 

![SharingNFSEnableServiceDialog](/images/SCALE/22.02/SharingNFSEnableServiceDialog.png "Unix (NFS) Share Widget")

**Enable Service** turns the NFS service on and changes the toolbar status to **Running**. 
If you added shares of other types, the widget occupies a quarter of the screen. 

The **Enable** toggle for each share shows the current status of the share. When disabled, it disables the share but does not delete the configuration from the system.

The <span class="material-icons">delete</span> delete icon displays a delete confirmation dialog that removes the share from the system.

![NFSShareWidgetDeleteDialog](/images/SCALE/22.02/NFSShareWidgetDeleteDialog.png "Unix (NFS) Share Delete")

**View Details** and clicking anywhere on **Unix (NFS) Share** the opens the **Sharing > NFS** screen with the list view of NFS shares. 

The NFS share on the widget opens the **[Edit NFS](#add-and-edit-nfs-screens)** screen.

### Unix (NFS) Share Widget Toolbar
The **Unix (NFS) Share** widget toolbar includes the **Add** button and an actions menu.

![NFSWidgetOptions](/images/SCALE/22.02/NFSWidgetOptions.png "Unix (NFS) Share Widget Options")

The <span class="material-icons">more_vert</span> on the toolbar displays options turn the NFS service on or off. **Turn Off Service** displays if the service is running or **Turn On Service** if the service is stopped. The **Config Service** option opens the **[Services > NFS]({{< relref "NFSServiceScreen.md" >}})** configuration screen. 

The toolbar displays the **STOPPED** service status in red before you start the service or click **Enable Service** when the dialog displays. When service is started it displays **RUNNING** in blue.

## Sharing NFS Details Screen
The **Sharing > NFS** details screen displays the same list of NFS shares as the **Unix (NFS) Share** widget.

Customize the information using the **Columns** dropdown list. Select from the  **Unselect All,** **Description**, **Enabled**, and **Reset to Defaults** options. 

The <span class="material-icons">more_vert</span> displays a list of options for the share. 
**Edit** opens the **Edit NFS** configuration screen.
**Delete** opens an **Unshare *path*** confirmation dialog.

![SharingNFSDeleteDialog](/images/SCALE/22.02/SharingNFSDeleteDialog.png "Sharing NFS Delete")

Select **Confirm** and then **UNSHARE** to remove the share without affecting the data in the share dataset.

## Add and Edit NFS Screens
The **Add NFS** and **Edit NFS** display the same **Basic Options** and **Advanced Options** settings.

### Basic Options Settings

![AddNFSBasicOptionsScreen](/images/SCALE/22.02/AddNFSBasicOptionsScreen.png "Add NFS Basic Options")

| Setting | Description |
|---------|-------------|
| **Path** | Click **Add** to display the **Add paths** settings. Enter the path or use the <span class="material-icons">arrow_right</span> icon to the left of **<span class="material-icons">folder</span>/mnt** to locate the dataset and populate the path. **Path** is the directory tree on the local file system that TrueNAS exports over the NFS protocol. Click **Add** for each path you want to add. |
| **Description** | Enter any notes or reminders about the share.   |
| **Enabled** | Select to enable this NFS share. Clear the checkbox to disable this NFS share without deleting the configuration. |
| **Add networks** | Click **Add** to display the **Authorized Networks** IP address and CIDR fields. Enter an allowed network IP and select the mask CIDR notation. Click **Add** for each network address and CIDR you want to define as an authorized network. Defining an authorized network restricts access to all other networks. Leave empty to allow all networks. |
| **Add hosts** | Click **Add** to display the **Authorized Hosts and IP addresses** field. Enter a host name or IP address to allow that system access to the NFS share. Click **Add** for each allowed system you want to define. Defining authorized systems restricts access to all other systems. Leave the field empty to allow all systems access to the share. |

### Advanced Options Settings 
**Advanced Options** settings tune the share access permissions and define authorized networks.
**Advanced Options** includes these **Basic Options** settings. Only the **Access** settings display on the **Advanced Options** screen.

![AddNFSAdvancedOptionsAccessSettings](/images/SCALE/22.02/AddNFSAdvancedOptionsAccessSettings.png "Add NSF Advanced Options Access Settings")

| Setting | Description |
|---------|-------------|
| **Read Only** | Select to prohibit writing to the share. |
| **Maproot User** | Enter a string or select a user from the dropdown to apply permissions for that user to the *root* user. |
| **Maproot Group** | Enter a string or select a group from the dropdown to apply permissions for that group to the *root* user. |
| **Mapall User** | Enter a string or select a user to apply the permission for the chosen user to all clients. |
| **Mapall Group** | Enter a string or select a group to apply the permission for the chosen group to all clients. |

{{< taglist tag="scalenfs" limit="10" >}}
