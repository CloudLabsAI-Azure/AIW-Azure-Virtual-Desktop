# Exercise 4: Access the Published Applications and Desktop using WVD Desktop Client

In this exercise, we will access the Desktop and RemoteApps assigned to us in the previous exercise using WVD Desktop client.

> **Note:** You have to perform this exercise in **Your Own PC/computer/workstation.** Do not perform this exercise within the JumpVM.


## **Task 1: Access the Published Applications**

1. Open a browser in **Your Own PC/computer/workstation** (not within the JumpVM), copy and paste the following URL in that browser tab.

   ```https://docs.microsoft.com/en-us/azure/virtual-desktop/connect-windows-7-10#install-the-windows-desktop-client```

   > **Note:** To download *WVD Mac Client* on **macOS**, use the link given below:
   >
   > ```https://docs.microsoft.com/en-us/azure/virtual-desktop/connect-macos```

2. Under *Install the Windows Desktop Client*, click on **Windows 64-bit**. This will download the **WVD Desktop Client** on **Your Own PC/computer/workstation**.
   
   ![ws name.](media/a48.png)
      
3. After the download completes, open the setup to run it. Then on the Welcome page of setup click on **Next**.

4. Check the agreement box and click on **Next**.

5. On **Installation scope** window select **Install just for you** and then click on **Install**.

   ![ws name.](media/wvd41.png)

6. After installation, in your PC go to **Start** and search for **Remote desktop** and open the remote desktop application with exact icon as shown below.

   ![ws name.](media/137.png)
   
7. Once the application opens, click on **Subscribe**.

   ![ws name.](media/a49.png)
  
8. Enter your **credentials** to access the workspace.

   - Username: *Paste your username* **<inject key="AzureAdUserEmail" />** *and then click on **Next**.*
   
   ![ws name.](media/95.png)

   - Password: *Paste the password* **<inject key="AzureAdUserPassword" />** *and click on **Sign in**.*

   ![ws name.](media/96.png)
   
   >**Note:** If there's a popup entitled **Help us protect your account** click **Skip for now (14 days intil this is required)**

   ![](media/skipfornow.png)

9. Make sure to **uncheck** *Allow my organization to manage my device* and click on **No, sign in to this app only**.

   ![ws name.](media/ex4t1s9.png)
      
10. The WVD dashboard will launch, then double click on **Excel** application to access it.

    ![ws name.](media/remotedesktop.png)
   
11. A window saying *Starting your app*, will appear. Wait for few seconds, then enter your password to access the Application.

    - Password: **<inject key="AzureAdUserPassword" />**
   
    ![ws name.](media/ch14.png)

12. Wait for the Application to connect.

    ![ws name.](media/58.png)
   
13. The Excel application will launch and look similar to the screenshot below.

    ![ws name.](media/ch15.png) 
    
14. You can exit from the window of Excel Application by clicking on **X *i.e., the close button***.

    ![ws name.](media/ch16.png)

15. Return back to the Azure Portal, search for *Windows virtual desktop* in the search bar and select **Windows Virtual Desktop** from the suggestions.

    ![ws name.](media/w1.png)

16. Click on **User** under *Manage* blade, then paste **<inject key="AzureAdUserEmail" />** in the search bar and click on your user to open it.

    ![ws name.](media/jvm7.png)

17. Click on **Sessions** tab, select both Host pools by clicking on the checkbox and then click on **Log off** button.

    ![ws name.](media/jvm8.png)

18. Click on **OK** to *Log off user from VMs*.

    ![ws name.](media/jvm9.png)

19. Click on **Refresh** button and make sure *No results* is displayed under Host pool.

    ![ws name.](media/jvm10.png)
   
## **Task 2: Access the Virtual Desktop**

1. Return to WVD client application. On WVD dashboard, click on the tile named **Session Desktop** to launch the desktop.

   ![ws name.](media/ex4t2s2.png)
   
2. A window saying *Connecting to: Session Desktop* will appear. Wait for few seconds, then enter your password to access the Desktop.

   - Password: **<inject key="AzureAdUserPassword" />**
   
   ![ws name.](media/ch14.png)
   
   >**Note:** If there's a dialog box saying ***Help us protect your account***, then select **Skip for now** option.
   
   ![](media/login.png)

3. Wait for the Session Desktop to connect.

   ![ws name.](media/ex4t2s4.png)

4. Your virtual desktop will launch and look similar to the screenshot below. You can exit from the window by clicking on **X *i.e., the close button***. 
        
   ![ws name.](media/ex4t2s5.png)   
     
5. Click on the **Next** button present in the bottom-right corner of this lab guide. 
