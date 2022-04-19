# Lab 10: MS Teams Optimized Experience

## **Scenario**

Contoso is an IT-based consulting service company. One of the major challenges faced by employees who are working from home is communication. Contoso wants to implement Azure Virtual Desktop's Optimized Audio Video Experience for their Teams Users. AVD's Teams Optimized experience ensures better QoS of the Audio/Video while attending Teams Online meetings. You will help Contoso to configure and set up Microsoft Teams for Azure virtual desktop.

## **Overview**

In this lab, We'll be implementing MS Teams for AVD. Microsoft Teams on Azure Virtual Desktop supports chat and collaboration. With media optimizations, it also supports calling and meeting functionality. With media optimization for Microsoft Teams, the Remote Desktop client handles audio and video locally for Teams calls and meetings.

## Exercise 1: Configuring Session host for implementing MS Teams

#### NOTE: Make sure that both the session hosts are running.
   
1. In your Azure portal search for *Virtual machines* in the search bar and click on **Virtual Machines** from the suggestions.

   ![ws name.](media/up11.png)
      
1. Click on **AVD-HP01-SH-0**.

   ![ws name.](media/fs4.png)
   
1. Make sure that the **Status** of the virtual machine is in **Running** state.

   ![ws name.](media/2avd79.png)
 
1. Under **Operations** (1) blade, Select **Run Command** (2). Select **RunPowerShellScript** (3).

   ![ws name.](media/teams18.png)
   
1. Paste the following commands into the Powershell script window and select **Run**. Once the execution is completed, **The operation completed successfully** message will be displayed in the output window

   >**NOTE**: The below-mentioned script downloads WebRTC and MS Teams which are specially meant for AVD.

   ```
   
   reg add "HKLM\SOFTWARE\Microsoft\Teams" /v IsWVDEnvironment /t REG_DWORD /d 1 /f

   $WebClient = New-Object System.Net.WebClient
   $WebClient.DownloadFile("https://github.com/CloudLabsAI-Azure/AIW-Azure-Virtual-Desktop/raw/Azure-Virtual-Desktop-v2/LabFiles/RTC.msi","C:\RTC.msi")

   msiexec /i C:\RTC.msi /qn

   Write-Output "The script is executed successfully"
   
   ```

   ![ws name.](media/2avd56.png)

   >**NOTE**: Wait for 3 minutes as the Session VM will take time to restart. If you see any error in the output window, Please ignore the error and continue with next steps.

1. Similarly, Navigate to virtual machines and click on **AVD-HP01-SH-1**.

    ![ws name.](media/fs8.png)
    
1. Make sure that the **Status** of the virtual machine is in **Running** state.

   ![ws name.](media/2avd80.png)    

1. Under **Operations** blade, Select **Run Command**. Select **RunPowerShellScript**.

   ![ws name.](media/teams18.png)
   
1. Paste the following commands into the Powershell script window and select **Run**. Once the execution is completed, **The operation completed successfully** message will be displayed in the output window.

   >**NOTE**: The below-mentioned script downloads WebRTC and MS Teams which are specially meant for AVD.
   
   ```
   
   reg add "HKLM\SOFTWARE\Microsoft\Teams" /v IsWVDEnvironment /t REG_DWORD /d 1 /f

   $WebClient = New-Object System.Net.WebClient
   $WebClient.DownloadFile("https://github.com/CloudLabsAI-Azure/AIW-Azure-Virtual-Desktop/raw/Azure-Virtual-Desktop-v2/LabFiles/RTC.msi","C:\RTC.msi")

   msiexec /i C:\RTC.msi /qn

   Write-Output "The script is executed successfully"
   
   ```

   ![ws name.](media/2avd56.png)

   >**NOTE**: Wait for 3 minutes as the Session VM will take time to restart. If you see any error in the output window, Please ignore the error and continue with next steps.

1. Navigate to the Azure portal, then search for Azure Virtual Desktop in the search bar and select Azure Virtual Desktop from the suggestions.

   ![ws name.](media/w1.png)
   
1. Select **Host pools** from the side blade and select **EB-AVD-HP**.

   ![ws name.](media/2avd120.png)
   
1. Under Settings, Select **RDP Properties** (1) and select **Device redirection** (2). Select the following options.
   
   - Microphone redirection: Select **Enable audio capture from the local devices and redirection to an audio application in the remote session** (3) from the dropdown.
   - Audio output location: Select **Play sounds on the remote computer** (4) from the dropdown
   - Camera redirection: Select **Redirect cameras** (5) from the dropdown.
   - Leave the rest properties as **defaults**.
   - click on **Save** (6).

   ![ws name.](media/2avd121.png)
   
1. Select **Application groups** from the side blade. You will see two application groups, Select the **AVD-AG-01** application group.

   ![ws name.](media/2avd122.png)
   
1. Under Manage, select **Applications** and select **Add**.

   ![ws name.](media/teams9.png)
   
1. In the **Add Application** tab, select the following options and click on **Save**.
   
   - **Application Source**: Start menu.
   - **Application**: Search for **Microsoft Teams** and select the same from dropdown.
   - **Display name**: Microsoft Teams.
   - **Leave** the other options as **defaults**.
   
   ![ws name.](media/2avd49.png)
   
## Exercise 2: Accessing MS Teams using Remote Desktop Application

1. On your PC go to **Start** and search for **Remote desktop** and open the remote desktop application with the exact icon as shown below.

   ![ws name.](media/137.png)
   
1. Once the application opens, click on **Subscribe**.

   ![ws name.](media/a49.png)
  
1. Enter your **credentials** to access the workspace.

   - Username: *Paste your username* **<inject key="AzureAdUserEmail" />** *and then click on **Next**.*
   
   ![ws name.](media/95.png)

   - Password: *Paste the password* **<inject key="AzureAdUserPassword" />** *and click on **Sign in**.*

   ![ws name.](media/96.png)
   
1. You'll see a dialog box to authenticate your login which is the indication of MFA implementation. Enter the 6 verification code to complete the verification.

   ![ws name.](media/MFA4.png)
   
   >**Note:** If there's a popup entitled **Help us protect your account** click **Skip for now (14 days until this is required)**

   ![](media/skipfornow.png)

1. Make sure to **uncheck** *Allow my organization to manage my device* and click on **No, sign in to this app only**.

   ![ws name.](media/ex4t1s9.png)
  
1. The AVD dashboard will launch, then double click on the Teams application to access it.

   ![ws name.](media/teams12.png)
   
1. A window saying *Starting your app*, will appear. Wait for a few seconds, then enter your password to access the Application.

    - Password: **<inject key="AzureAdUserPassword" />**
   
    ![ws name.](media/ch14.png)
    
1. Teams application will start loading.

   ![ws name.](media/avdv214.png)
   
1. After the Teams application is launched, click on the **three dots** (1) then **About** (2) and click on **Version** (3).

   ![ws name.](media/avdv215.png)

1. Now we will get a message on top of the Teams application saying **The Teams Version 1.x.x.. is WVD Media Optimised**.

   ![ws name.](media/avdv216.png)
   
   >**Note**: If you see a message saying **AVD Media not connected**. Please skip the step and continue with the lab.
   
1. Again click on the **three dots** (1) on the top and select **Settings** (2).

   ![ws name.](media/avdv217.png)
   
1. Now under Settings, click on **Devices** and explore the media devices connected to your local desktop.

   ![ws name.](media/avdv218.png)
   
   >**Note**: If you are not able to select other audio devices. Please skip the step and continue with the lab.
   
1. Now, Close the settings tab and go to **calendar** (1) which is located in the side blade. Select **Meet now** (2).

   ![ws name.](media/teams13.png)
   
1. Leave the **Meeting name** as default and click on **Start meeting**.

   ![ws name.](media/teams14.png)
   
1. Make sure both Video (1), and Audio (2) are enabled. Click on **Join now** (3).

   ![ws name.](media/teams15.png)
   
   >**Note**: If the audio is not working. Please skip the step and continue with the lab as this is an expected issue.
   
1. Click on **Allow access** on the Windows Security alert prompt.

   ![ws name.](media/teams16.png)
   
   >**NOTE**: If the **Invite others** prompt appears, Close the tab and continue.
  
1. Now, You should be able to see yourself as the video is On.

1. Click on the Next button present in the bottom-right corner of this lab guide.
