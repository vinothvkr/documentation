---
title: "Setting Up Data Sharing"
description: "This article provides general information on setting up basci data sharing on TrueNAS SCALE."
weight: 50
tags:
- scaleinstall
- scalemigrate
- scaleshares
---

{{< toc >}}

After setting up storage on your TrueNAS, it is time to begin sharing data!
There are several sharing solutions available on SCALE, but in this article we discuss the most common. 

## Sharing Data Methods
TrueNAS SCALE provides four types of sharing methods, but this article only discusses three:

* SMB for Windows
* NFS for Unix-like sharing
* ISCSi block shares

## Setting UP SMB for Windows

To set up SMB sharing:

1. Create a dataset with **Share Type** set to **SMB**. Go to **Storage > Pools** 

   a. Go to **Storage > Pools** and click on the <i class="fa fa-ellipsis-v" aria-hidden="true" title="Options"></i> and click **Add Dataset**.

   b. Enter a name and select **SMB** in the **Share Type** field.

   c. Click **Save**.

2. Create the TrueNAS user accounts with **Samba Authentication** set.

   a. Go to **Credentials > Local Users** and click **Add** to create users. 
      
      ![LocalUserAddUser](/images/SCALE/22.02/LocalUserAddUser.png "Local User Add User")
          
   b. Enter the values in each required field, and then verify the checkmark for **Samba Authentication** exists.

      ![LocalUserAddUser2](/images/SCALE/22.02/LocalUserAddUser2.png "Local User Verify Samba Authentication")
    
   c. Click **Save**.

3. Edit the dataset permissions to set the **Select an ACL Preset** to **Open**.

   a. Go to **Storage > Pools** and click on the <i class="fa fa-ellipsis-v" aria-hidden="true" title="Options"></i> for the dataset, and select **View Permissions**. 
      The **View Permissions** widget for the selected dataset displays on the right side of the screen.
      
      ![ViewDatasetPermissionsWidgett](/images/SCALE/22.02/ViewDatasetPermissionsWidget.png "View Dataset Permissions Widget")

   b. Click on the <span class="material-icons">edit</span> edit icon to display the **Edit ACL** screen. 
      
      ![EditACLScreen](/images/SCALE/22.02/EditACLScreen.png "EditACLScreen")
   
   c. Select **Use ACL Preset**. The **Select a preset ACL** dialog displays. Select **NFS4_OPEN** from the dropdown list and then click **Continue**.
      
      ![SelectPresetACLNFS4OPEN](/images/SCALE/22.02/SelectPresetACLNFS4OPEN.png "Select Preset ACL NFS4_OPEN")

   d. Click **Save Access Control List**.

4. Create the new SMB share. Go to **Shares > Windows (SMB) Shares** and click **Add**.

   a. Select the dataset you created for the share in the **Path** field. 
      You can click on the <i class="fa fa-caret-right" aria-hidden="true"></i> to the left of **mnt**, and then at the pool to expand the options, and then click on the dataset to populate the field with the full path.
   
      ![AddSMBPath](/images/SCALE/22.02/AddSMBPath.png "Add SMB Path")

   b. Enter a name for the share.

   c. Click **Save**.

5. Turn the SMB service on. 
   Click the <i class="fa fa-ellipsis-v" aria-hidden="true" title="Options"></i> for the share and select **Turn On Service** from the **Sharing** screen.
   
   ![SMBShareOptions](/images/SCALE/22.02/SMBShareOptions.png "SMB Share Options")

6. Connect to the share. On a Windows 10 system, open the **File Browsers** and then:

   a. In the navigation bar, enter `\\` and the TruNAS system name or IP address. A login or credentials dialog displays.

   b. Enter the TrueNAS user account credentials you created on the TrueNAS system. 
      
      ![FileExplorerEnterSMBCredentials](/images/SCALE/22.02/FileExplorerEnterSMBCredentials.png "File Explorer Enter SMB Credentials")

   c. Begin browsing the dataset.

## Setting UP NFS for Unix-Like Share

To set up NFS sharing:

1. Create a dataset with **Share Type** set to **Generic**. Go to **Storage > Pools** 

   a. Go to **Storage > Pools** and click on the <i class="fa fa-ellipsis-v" aria-hidden="true" title="Options"></i> and click **Add Dataset**.

   b. Enter a name and select **Generic** in the **Share Type** field.

   c. Click **Save**.

2. Add additional packages like `nfs-common` to any client systems that require them.

3. Create the NFS share. Go to **Shares > UNIX (NFS) Share Targets** and click **Add**. The **Add NFS** configuration form displays.

   a. Select the dataset you created for the share in the **Path** field. 
      You can click on the <i class="fa fa-caret-right" aria-hidden="true"></i> to the left of **mnt**, and then at the pool to expand the options, and then click on the dataset to populate the field with the full path.
   
      ![AddNFSPath](/images/SCALE/22.02/AddNFSPath.png "Add NFS Path")

   b. Click **Save**.

4. Access the dataset. On a Unix-like system, open a command line and enter command `showmount -e *`IPADDRESS`* where *`IPADDRESS`* is your TrueNAS system address.
   
   ```
   tmoore@ChimaeraPrime:~$ showmount -e 10.238.15.194
   Export list for 10.238.15.194:
   /mnt/pool1/testds (everyone)
   ```

5. Make a local directory for the NFS mount. Enter command `sudo mkdir nfstemp/`
   
   ```
   tmoore@ChimaeraPrime:~$ sudo mkdir nfstemp/
   ```

6. Mount the shared directory. 
   Enter command `sudo mount -t nfs *`IPADDRESS:dataset path`* where *`IPADDRESS`* is your system IP address and *`:dataset path`* is the full path displayed in step 3.a. above.

   ```
   tmoore@ChimaeraPrime:~$ sudo mount -t nfs 10.238.15.194:/mnt/pool1/testds nfstemp/
   ```

7. From here, `cd` into the local directory and view or modify the files as needed.

## Setting Up an ISCSi Block Share

Setting up block sharing is a complicated scenario that requires detailed configuration steps and knowledge of your network environment.
A simple configuration is beyond the scop of this getting started guide, but detailed articles are available in the UI Reference section under Shares.

With simple sharing now set up, you can back up your configuration and set up data backup.

{{< taglist tag="scaleinstall" limit="10" >}}
{{< taglist tag="scaleshares" limit="10" title="Related Shares Articles" >}}
