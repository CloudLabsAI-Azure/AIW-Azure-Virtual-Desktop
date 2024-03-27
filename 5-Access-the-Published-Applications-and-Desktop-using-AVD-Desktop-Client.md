# Lab 5: Access the Published Applications and Desktop using the AVD Desktop Client

## **Scenario**

Contoso wants their AVD environment to be flexible in terms of accessing the sessions by their employees. You will help Contoso to test the access to the AVD session using the AVD Client application using your local computer.

## **Overview**

In this exercise, we will access the Desktop and RemoteApps assigned to us in the previous exercise using the AVD Desktop client.

>#### **Note:** You have to perform this exercise in **Your Own PC/computer/workstation.** Do not perform this exercise within the JumpVM.

## Exercise 1: Access the Published Applications

1. Open a browser in **Your Own PC/computer/workstation** (not within the JumpVM), copy and paste the following URL in that browser tab.

   ```
   https://docs.microsoft.com/en-us/azure/virtual-desktop/connect-windows-7-10#install-the-windows-desktop-client
   ```

   > **Note:** To download *AVD Mac Client* on **macOS**, use the link given below:
   >
   > ```
   > https://docs.microsoft.com/en-us/azure/virtual-desktop/connect-macos
   > ```

1. Under **Download and install the Remote Desktop Client (MSI)**, click on **Windows 64-bit**. This will download the **Remote Desktop Client** on **Your Own PC/computer/workstation**.
   
   ![ws name.](media/lab5-1.png)
      
1. After the download completes, open the setup to run it. Then on the Welcome page of setup click on **Next**.

1. Check the agreement box and click on **Next**.

1. On the **Installation scope** window, select **Install just for you** and then click on **Install**.

   ![ws name.](media/wvd41.png)

1. After installation, on your PC go to **Start** and search for **Remote desktop** and open the remote desktop application with the exact icon as shown below.

   ![ws name.](media/137.png)
   
1. Once the application opens, click on **Subscribe**.

   ![ws name.](media/a49.png)
  
1. Enter your **credentials** to access the workspace.

   - Username: *Paste your username* **<inject key="AzureAdUserEmail" />** *and then click on **Next**.*
   
   ![ws name.](media/95.png)

   - Password: *Paste the password* **<inject key="AzureAdUserPassword" />** *and click on **Sign in**.*

   ![ws name.](media/96.png)
   
   >**Note:** If there's a popup entitled **Help us protect your account**, click **Skip for now (14 days until this is required)**

   ![](media/skipfornow.png)

1. Make sure to **uncheck** *Allow my organization to manage my device* and click on **No, sign in to this app only**.

   ![ws name.](media/ex4t1s9.png)
      
1. The AVD dashboard will launch, then double-click on the **Excel** application to access it.

   ![ws name.](media-2/rd-excel.png)
   
1. A window saying *Starting your app*, will appear. Wait for a few seconds, then enter your password to access the Application.

    - Password: **<inject key="AzureAdUserPassword" />**
   
   ![ws name.](media/ch14.png)

1. Wait for the Application to connect.

   ![ws name.](media/58.png)
    
   >**Note:** If you get stuck while initiating the application, navigate back to the Azure portal restart the session host VMs and re-perform Exercise-1
   
1. The Excel application will launch and look similar to the screenshot below.

   ![ws name.](media/ch15.png) 
    
1. You can exit from the window of the Excel Application by clicking on **X *i.e., the close button***.

   ![ws name.](media/ch16.png)

1. Return back to the Azure Portal, search for *Azure virtual desktop* in the search bar, and select **Azure Virtual Desktop** from the suggestions.

   ![ws name.](media/w1.png)

1. Click on **User** under *Manage* blade, then paste **<inject key="AzureAdUserEmail" />** in the search bar and click on your user to open it.

   ![ws name.](media/AVD-users.png)

1. Click on the **Sessions (1)** tab, select both Host pools by clicking on the checkbox **(2)** and then click on the **Log off (3)** button.

   ![ws name.](media-2/hplogoff.png)

1. Click on **OK** to *Log off user from VMs*.

   ![ws name.](media/jvm9.png)

1. Click on the **Refresh** button and make sure *No results* is displayed under Host pool.

   ![ws name.](media-1/Ex5-task1-step19.png)
   
## Exercise 2: Access the Virtual Desktop

1. Return to AVD client application. On the AVD dashboard, click on the tile named **Session Desktop** to launch the desktop.

   ![ws name.](media-2/sessiondesktop.png)
   
1. A window saying *Connecting to: Session Desktop* will appear. Wait for a few seconds, then enter your password to access the Desktop.

   - Password: **<inject key="AzureAdUserPassword" />**
   
   ![ws name.](media/ch14.png)
   
   >**Note:** If there's a dialog box saying ***Help us protect your account***, then select the **Skip for now** option.
   
   ![](media/login.png)

1. Wait for the Session Desktop to connect.

   ![ws name.](media/ex4t2s4.png)

1. Your virtual desktop will launch and look similar to the screenshot below. You can exit from the window by clicking on **X *i.e., the close button***. 
        
   ![ws name.](../Azure-Virtual-Desktop-v3/media/sessiondesktop1.1.png)   
     
1. Click on the **Next** button present in the bottom-right corner of this lab guide. 
