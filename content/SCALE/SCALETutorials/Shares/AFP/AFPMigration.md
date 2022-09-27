---
title: "AFP Migration"
description: "This article provides information on migrating AFP shares from CORE to SCALE."
weight: 40
aliases: /scale/scaleuireference/shares/afpmigration/
tags:
 - scaleshares
 - scaleafp
 - scalemigrate
---

{{< toc >}}

Since the Apple Filing Protocol (AFP) for shares is deprecated and no longer receives updates, it is not included in TrueNAS SCALE.

However, users can sidegrade a TrueNAS CORE configuration into SCALE, so TrueNAS SCALE migrates previously-saved AFP configurations into SMB configurations.

To prevent data corruption that could result from the sidegrade operation, in SCALE go to **Windows (SMB) Shares** select the <span class="material-icons">more_vert</span> for the share, and then select **Edit** to open the **Edit SMB** screen. 
Click **Advanced Options** and scroll down to the **Other Options** section. 
Select **Legacy AFP Compatibility** to enable compatibility for AFP shares migrated to SMB shares. 
Do not select this option if you want a pure SMB share with no AFP relation.

![AFPCompatibilityCheckbox](/images/SCALE/AFPCompatibilityCheckbox.png "AFP Compatibility Checkbox")

{{< hint warning >}}
Netatalk service was removed in SCALE version 21.06. 
AFP shares are automatically migrated to SMB shares with the **Legacy AFP Compatibility** option selected. 
Do not clear the **Legacy AFP Compatibility** checkbox as it impacts how data is written to and read from shares. 
Any other shares created to access these paths after the migration must also have **Legacy AFP Compatibility** selected.
{{< /hint >}}

Once you have [sidegraded from CORE to SCALE]({{< relref "MigratingFromCore.md" >}}), you can find your migrated AFP configuration in **Shares >** **Windows Shares (SMB)** with the prefix **AFP_**.
To make the migrated AFP share accessible, start the SMB service.

![MigratedAFPShareSCALE](/images/SCALE/MigratedAFPShareSCALE.png "Migrated AFP Share")

{{< taglist tag="scalesmb" limit="10" >}}
{{< taglist tag="scalemigrate" limit="10" title="Related Migration Articles" >}}