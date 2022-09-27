---
title: "Managing Users"
description: "This article provides instructions on adding and managing local user accounts."
weight: 10
alias: /scale/scaleuireference/credentials/localusers/
tags:
 - scaleusers
---

{{< toc >}}

In TrueNAS, user accounts allow flexibility for accessing shared data.
Typically, administrators create users and assign them to [groups]({{< relref "ManageLocalGroups.md" >}}).
Doing so makes tuning permissions for large numbers of users more efficient.

{{< hint warning >}}
Only the **root** user account can log in to the TrueNAS web interface until the root user creates an admin user with the same permissions.

As part of security hardening and to comply with Federal Information Processing standards (FIPS), iXsystems plans to completely disable root login in a future release.
When this occurs, the sign-in screen prompts first-time users to create a new administration account they used in place of the root user.
System administrators should create and begin using a new root-level user before this function goes away.
{{< /hint >}}

When the network uses a directory service, import the existing account information using the instructions in [Directory Services]({{< relref "/content/SCALE/SCALEUIReference/Credentials/DirectoryServices/_index.md" >}}).

Using [Active Directory]({{< relref "/content/SCALE/SCALEUIReference/Credentials/DirectoryServices/_index.md" >}}) requires setting Windows user passwords in Windows.

To see user accounts, go to **Credentials > Local Users**.

![LocalUsersSCALE](/images/SCALE/22.02/LocalUsersSCALE.png "List of Local User Accounts") 

TrueNAS hides all built-in users (except root) by default. Click **Toggle Built-In Users**, then click **SHOW** to see all built-in users.

## Creating User Accounts

{{< expand "Tutorial Video" "v" >}}
This short video demonstrates adding a local user.
{{< embed-video name="scaleangelfishlocalusers" >}}
{{< /expand >}} 

To create a new user, click **Add**.

TrueNAS lets users configure four different user account traits (settings). 

### Configuring User Identification Settings

![AddUserIdentificationSettings](/images/SCALE/22.02/AddUserIdentificationSettings.png "Add User Identification Settings") 

Enter the user full name in **Full Name**.
TrueNAS suggests a simplified name in **Username** derived from the **Full Name**, but you can override it with your own choice.

You can also assign a user account email address in the **Email** field.

Set and confirm a password.

### Configuring User ID and Groups Settings

![AddUserUserIDAndGroupsSettings](/images/SCALE/22.02/AddUserUserIDAndGroupsSettings.png "Add User User Id an Groups Settings") 

Next, you must set a user ID.
TrueNAS suggests a user ID starting at **1000**, but you can change it if you wish.
We recommend using an ID of 1000 or greater for non-built-in users.

By default, TrueNAS creates a new primary group with the same name as the user.
To add the user to an existing primary group instead, clear the **New Primary Group** checkbox and select a group from the **Primary Group** drop-down list.
You can add the user to more groups using the **Auxiliary Groups** drop-down list.

### Configuring Directories and Permissions Settings

![AddUserDirPermsAuthSettings](/images/SCALE/22.02/AddUserDirPermsAuthSettings.png "Add User Directories, Permissions and Authentication Settings") 

When creating a user, the home directory path is set to <file>/nonexistent</file>, which does not create a home directory for the user.
To set a user home directory, select a path using the file browser.
If the directory exists and matches the user name, TrueNAS sets it as the user home directory.
When the path does not end with a sub-directory matching the user name, TrueNAS creates a new sub-directory.
TrueNAS shows the path to the user home directory when editing a user.

You can set the home directory permissions directly under the file browser. 
You cannot change TrueNAS default user account permissions.

### Configuring Authentication Settings

![AddUserDirPermsAuthSettings](/images/SCALE/22.02/AddUserDirPermsAuthSettings.png "Add User Directories, Permissions and Authentication Settings") 

You can assign a public SSH key to a user for key-based authentication by pasting the *public* key into the **SSH Public Key** field.
If you are using an SSH public key, always keep a backup of the key.
Click **Download SSH Public Key** to download the pasted key as a <file>.txt</file> file.

By default, **Disable Password** is **No**.

Setting **Disable Password** to **Yes** disables several options: 
* The **Password** field becomes unavailable, and TrueNAS removes any existing password from the account.
* The **Lock User** and **Permit Sudo** options disappear.
* The account is restricted from password-based logins for services like SMB shares and SSH sessions.

You can set a specific [shell]({{< relref "UseScaleShell.md" >}}) for the user from the **Shell** dropdown options:

| Shell | Description |
|-------|-------------|
| bash	| [Bourne Again shell](https://www.gnu.org/software/bash/manual/bash.html) for the GNU operating system. |
| rbash	| [Restricted bash](https://www.gnu.org/software/bash/manual/html_node/The-Restricted-Shell.html) |
| dash | [Debian Almquist shell](https://man7.org/linux/man-pages/man1/dash.1.html) |
| sh	| [Bourne shell](https://www.in-ulm.de/~mascheck/bourne/v7/) |
| zsh	| [Z shell](http://zsh.sourceforge.net/) |
| tmux | [terminal multiplexer](https://man7.org/linux/man-pages/man1/tmux.1.html)  |
| nologin | Use when creating a system account or to create a user account that can authenticate with shares but that cannot log in to the TrueNAS system using `ssh`.

Selecting **Lock User** disables all password-based functionality for the account until you clear the checkbox.

**Permit Sudo** allows the account to act as the system administrator using the `sudo` command. Leave it disabled for better security.

If the user accesses TrueNAS data using Windows 8 or newer, select **Microsoft Account** to enable those systems' additional authentication methods.

By default, **Samba Authentication** is enabled.
This allows using the account credentials to access data shared with [SMB]({{< relref "/content/SCALE/SCALEUIReference/Shares/_index.md" >}}).

## Editing User Accounts

To edit an existing user account, go to **Credentials > Local Users**, expand the user entry, and click <i class="material-icons" aria-hidden="true" title="Configure">edit</i> **Edit** to open the **Edit User** configuration screen. See [Local User Screens]({{< relref "LocalUsersScreensScale.md" >}}) for details on all settings.

{{< taglist tag="scaleusers" limit="10" >}}