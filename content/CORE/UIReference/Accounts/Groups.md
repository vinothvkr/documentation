---
title: "Groups"
weight: 10
---

{{< toc >}}

The **Groups** screen lets you create and manage UNIX-style groups.

## Groups List

![UIRefGroupsList](/images/CORE/13.0/UIRefGroupsList.png "Accounts Groups List")

| Name | Description |
|------|------|
| Filter Groups | Filters groups by keyword. |
| COLUMNS | Lets users display/hide list columns. |
| ADD | Opens the **Group Configuration** form  |
| <span class="iconify" data-icon="mdi:cog"></span> | Displays/hides built-in groups |
| Group | Group name. |
| GID | Group ID number. |
| Builtin | Whether or not the group is built-in. |
| Permit Sudo | Whether or not the group has PErmit Sudo enabled. |
| Samba Authentication | Whether or not the group has Samba Authentication enabled. |

## Groups Configuration

![UIRefGroupsAdd](/images/CORE/13.0/UIRefGroupsAdd.png "Accounts Groups Add")

| Name | Description |
|------|------|
| GID | A unique number used to identify a Unix group. |
| Name | Descriptive name for the group. |
| Permit Sudo | Allows group members to use sudo. Group members are prompted for their password when using sudo. |
| Samba Authentication | Allows group to be used for Samba permissions and authentication. |
| Allow Duplicate GIDs | Allows more than one group to have the same group ID. |