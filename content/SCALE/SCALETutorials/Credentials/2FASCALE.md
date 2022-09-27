---
title: "Using 2FA (Two-Factor Authentication)"
description: "This article provides information on SCALE two-factor authentication, setting it up and logging in with it enabled."
weight: 60
alias:
tags:
 - scale2fa
 - scalessh
 - scalecredentials
---


{{< toc >}}

Two-factor authentication (2FA) is great for increasing security.

TrueNAS offers 2FA to ensure that entities cannot use a compromised administrator root password to access the administrator interface.
## About SCALE 2FA
To use 2FA, you need a mobile device with the current time and date, and that has Google Authenticator installed.
Other authenticator applications can be used, but you will need to confirm the settings and QR codes generated in TrueNAS are compatible with your particular app before permanently activating 2FA.

{{< hint warning >}}
Two-factor authentication is time-based and requires a correct system time setting. 
Make sure Network Time Protocol (NTP) is functional before enabling is strongly recommended!
{{< /hint >}}

{{< expand "What is 2FA and why should I enable it?" "v" >}}
2FA adds an extra layer of security to your system to prevent someone from logging in, even if they have your password. 
2FA requires you to verify your identity using a randomized 6-digit code that regenerates every 30 seconds (unless modified) to use when you log in.
{{< /expand >}}
### Benefits of 2FA

Unauthorized users cannot log in since they do not have the randomized 6-digit code.

Authorized employees can securely access systems from any device or location without jeopardizing sensitive information.

Internet access on the TrueNAS system is not required to use 2FA.

### Drawbacks of 2FA

2FA requires an app to generate the 2FA code.

If the 2FA code is not working or users cannot get it, the system is inaccessible through the UI and SSH (if enabled). You can bypass or [unlock 2FA](#disabling-or-bypassing-2fa) using the CLI.

## Enabling 2FA

{{< expand "Video Tutorial" "v" >}}
This short video demonstrates adding 2FA. 
{{< embed-video name="scale2fasetup" >}}
{{< /expand >}}

{{< hint danger >}}
Set up a second 2FA device as a backup before proceeding.
{{< /hint >}}

Before you begin, download Google Authenticator to your mobile device.

1 Go to **Credentials > 2FA** to open the **Two-Factor Auth** screen and scroll down to the bottom.
  
  ![2FASystemGeneratedSettings](/images/SCALE/22.02/2FASystemGeneratedSettings.png "2FA System Generated Settings")

2 Click **Enable Two Factor Authentication**. The **Enable Two-Factor Authentication** confirmation dialog opens. Click **Confirm**.
  
  ![Enable2FAConfirmationDialog](/images/SCALE/22.02/Enable2FAConfirmationDialog.png "Enable 2FA")

  **Disable Two-Factor Authentication** displays next to **Save** to turn 2FA off.

3 Click **Show QR**. A QR code dialog opens.
   
   ![2FAQRCodeDialog](/images/SCALE/22.02/2FAQRCodeDialog.png "2FA QR Code")

4 Start Google Authenticator on the mobile device and scan the QR code. After scanning the code click **Close** to close the dialog on the **Two-Factor Auth** screen.

### Disabling or Bypassing 2FA

Go to **Credentials > 2FA** to open the **Two-Factor Auth** screen and scroll down to the bottom. Click **Disable Two-Factor Authentication**.
{{< hint info >}}
If the device with the 2FA app is not available, you can use the system CLI to bypass 2FA with administrative IPMI or by physically accessing the system. 

To unlock 2FA in the CLI, enter:  `midclt call auth.twofactor.update '{ "enabled":false }'`
{{< /hint >}}

### Reactivating 2FA

After disabling 2FA, if you want to enable it again at some point in the future, go to **Credentials > 2FA** to open the **Two-Factor Auth** screen and scroll down to the bottom. 
Click **Enable Two-Factor Authentication**.

To change the system-generated **Secret** and **Provisioning URI** values, click **Renew Secret**. 
If you want to save these values in a text file, click the <span class="material-icons">visibility_off</span> icon in the field to display the alphanumeric string and either enter or copy/paste the value into a text file.
Keep all login codes in protected and backed up location.

## Using 2FA to Log in to TrueNAS

Enabling 2FA changes the login process for both the TrueNAS web interface and SSH logins.

### Logging In Using the Web Interface
The login screen adds another field for the randomized authenticator code. If this field is not immediately visible, try refreshing the browser.

Enter the code from the mobile device (without the space) in the login window and use the root User name and password.

![2FALoginSCALE](/images/SCALE/2FALoginSCALE.png "2FA Login")

### Logging In Using SSH

1. Confirm that you set **Enable Two-Factor Auth for SSH** in **Credentials > 2FA**.

2. Go to **System Settings > Services** and edit the **SSH** service.

   a. Set **Log in as Root with Password**, then click **Save**.

   b. Click the **SSH** toggle and wait for the service status to show that it is running.

3.  Open the Google Authentication app on your mobile device.

4. Open a terminal and SSH into the system using its host name or IP address, the root account user name and password, and the 2FA code.
   
   ![2FALogin](/images/SCALE/22.02/2FALogin.png "2FA SSH Connection")

{{< taglist tag="scale2fa" limit="10" >}}
