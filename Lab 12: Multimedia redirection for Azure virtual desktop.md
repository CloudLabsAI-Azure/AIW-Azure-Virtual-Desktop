# Lab 12: Multimedia redirection for Azure virtual desktop



1. On your PC go to **Start** and search for **Remote desktop** and open the remote desktop application with the exact icon as shown below.

   ![ws name.](media/137.png)
   
1. Once the application opens, click on **Subscribe**.

   ![ws name.](media/a49.png)
  
1. Enter your **credentials** to access the workspace.

   - Username: *Paste your username* **<inject key="AzureAdUserEmail" />** *and then click on **Next**.*
   
   ![ws name.](media/95.png)

   - Password: *Paste the password* **<inject key="AzureAdUserPassword" />** *and click on **Sign in**.*

   ![ws name.](media/96.png)
   
1. You'll see a dialog box to authenticate your login which is the indication of MFA implementation. Authenticate the login according to the authentication menthod you have chosen in lab 9, exercise 1 to complete the verification.

   ![ws name.](media/2avd54.png)
   
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
