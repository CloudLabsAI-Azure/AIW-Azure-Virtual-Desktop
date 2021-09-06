# Optional Lab: MS Teams Optimized Experience

1. Navigate to Azure portal, then search for Azure Virtual Desktop in search bar and select Azure Virtual Desktop from the suggestions.

   ![ws name.](media/w1.png)

1. You will be directed towards the Azure Virtual Desktop management window.  

   ![ws name.](media/64.png)
   
1. Click on the Session host tab and you will see two session hosts. Select **AVD-HP01-SH-0.azurehol1047.onmicrosoft.com** session host.

   ![ws name.](media/teams1.png)
   
1. Click on **AVD-HP01-SH-0.azurehol1047.onmicrosoft.com**.

   ![ws name.](media/teams2.png)
 
1. Under **Operations** blade, Select **Run Command**. Select **RunPowerShellScript**.

   ![ws name.](media/teams4.png)
   
1. Paste the following commands into the Powershell script window and select **Run**. Once the execution is completed, **The operation completed successfully** message wil be displayed in output window

   ```
   reg add "HKLM\SOFTWARE\Microsoft\Teams" /v IsWVDEnvironment /t REG_DWORD /d 1 /f

   $WebClient = New-Object System.Net.WebClient
   $WebClient.DownloadFile("https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RWFYsj","C:\WebSocketService.msi")

   msiexec /i C:\WebSocketService.msi /qn

   $WebClient = New-Object System.Net.WebClient
   $WebClient.DownloadFile("https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&arch=x64&managedInstaller=true&download=true","C:\Teams_windows_x64.msi")

   msiexec /i C:\Teams_windows_x64.msi ALLUSER=1

   Restart-Computer -Force
   
   ```

   ![ws name.](media/teams5.png)

   >**NOTE**: Wait for 3 minutes as the Session VM will take time to restart.

1. Navigate to Azure portal, then search for Azure Virtual Desktop in search bar and select Azure Virtual Desktop from the suggestions.

   ![ws name.](media/w1.png)
   
1. Select **Host pools** from the side blade and select **AVD-HP-01**.

   ![ws name.](media/teams7.png)
   
1. Under Settings, Select **RDP Properties** and select **Device redirection**. Make sure for **Audio output location** option, **Play sounds on the local computer** is selected.

   ![ws name.](media/teams8.png)
   
1. Select **Application groups** from the side blade. You will see two application groups, Select the **AVD-AG-01** application group.

   ![ws name.](media/teams6.png)
   
1. Under Manage, select **Applications** and select **Add**.

   ![ws name.](media/teams9.png)
   
1. In **Add Application** tab, select the following options and click on **Save**.
   
   - **Application Source**: Start menu.
   - **Application**: Search for **Microsoft Teams** and select the same from dropdown.
   - **Leave** the other option as **defaults**.
   
   ![ws name.](media/teams10.png)

1. After installation, in your PC go to **Start** and search for **Remote desktop** and open the remote desktop application with exact icon as shown below.

   ![ws name.](media/137.png)
   
1. Once the application opens, click on **Subscribe**.

   ![ws name.](media/a49.png)
  
1. Enter your **credentials** to access the workspace.

   - Username: *Paste your username* **<inject key="AzureAdUserEmail" />** *and then click on **Next**.*
   
   ![ws name.](media/95.png)

   - Password: *Paste the password* **<inject key="AzureAdUserPassword" />** *and click on **Sign in**.*

   ![ws name.](media/96.png)
   
   >**Note:** If there's a popup entitled **Help us protect your account** click **Skip for now (14 days intil this is required)**

   ![](media/skipfornow.png)

1. Make sure to **uncheck** *Allow my organization to manage my device* and click on **No, sign in to this app only**.

   ![ws name.](media/ex4t1s9.png)
  
1. The WVD dashboard will launch, then double click on Teams application to access it.

   ![ws name.](media/teams12.png)
   
1. A window saying *Starting your app*, will appear. Wait for few seconds, then enter your password to access the Application.

    - Password: **<inject key="AzureAdUserPassword" />**
   
    ![ws name.](media/ch14.png)
    
1. Teams application will start loading.

   ![ws name.](media/avdv214.png)
   
1. After the Teams application is launched, click on the **three dots** *(1)* then **About** *(2)* and click on **Version** *(3)*.

   ![ws name.](media/avdv215.png)

1. Now we will get a message on top of the teams application saying **The Teams Version 1.x.x.. is WVD Media Optimised**.

   ![ws name.](media/avdv216.png)
   
1. Again click on the **three dots** *(1)* on the top and select **Settings** *(2)*.

   ![ws name.](media/avdv217.png)
   
1. Now under Settings, click on **Devices** and explore the media devices connected to your local desktop.

   ![ws name.](media/avdv218.png)
   
1. Now, Close the settings tab and go to **calendar** which is located in the side blade. Select **Meet now**.

   ![ws name.](media/teams13.png)
   
1. Leave the **Meeting name** as default and click on **Start meeting**.

   ![ws name.](media/teams14.png)
   
1. Make sure both Video(1), and audio(2) are enabled. Click on **Join now(3)**.

   ![ws name.](media/teams15.png)
   
1. Click on **Allow access** on Windows Security Alert prompt.

   ![ws name.](media/teams16.png)
   
   >**NOTE**: If **Invite others** prompt appears, Close the tab and continue.
  
1. Now, You should be able to see yourself as the video is On.
