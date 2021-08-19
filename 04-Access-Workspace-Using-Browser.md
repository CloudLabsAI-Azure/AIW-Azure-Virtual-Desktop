# Exercise 3: Access the Published Applications and Desktop using Browser


## **Task 1: Access the Published Application**

In this exercise, we will access the Desktop and RemoteApps assigned to us in the previous exercise using browser.

1. Open the following URL in a new browser tab in the JumpVM. This URL will lead us to the Remote Desktop Web Client.

   ```aka.ms/wvdarmweb``` 

   >**Note:** If you are already logged in through your user, then jump to step 3 else continue with the next step i.e., Step 2.

2. Now to login, enter the lab credentials as mentioned below:

   - Username: *Paste your username* **<inject key="AzureAdUserEmail" />** *and then click on **Next**.*
   
   ![ws name.](media/95.png)

   - Password: *Paste the password* **<inject key="AzureAdUserPassword" />** *and click on **Sign in**.*

   ![ws name.](media/96.png)

   >**Note:** If there's a dialog box saying ***Help us protect your account***, then select **Skip for now** option.

   ![](media/login.png)

3. The AVD dashboard will launch, then click on **Word** application to access it. 

   ![ws name.](media/word.png)

4. Select **Allow** on the prompt asking permission to *Access local resources*.

   ![ws name.](media/allow.png)

5. Enter the lab credentials to access the application and click on **Submit**.

   - Username: **<inject key="AzureAdUserEmail" />** 
  
   - Password: **<inject key="AzureAdUserPassword" />**

   ![ws name.](media/89.png)
      
6. The Word application will launch and look similar to the screenshot below. Click on **Sign in**.

   ![ws name.](media/ch9.png)

7. Enter username **<inject key="AzureAdUserEmail" />** on *Activate Office* window and click on **Next**.

   ![ws name.](media/ch6.png)

   >**Note:** If you get a popup saying *Move Text in and out of Remote Desktop*, click on the ***Don't show again*** checkbox and then click on ***Got it*** button.
   
   ![ws name.](media/uiupdate06.png)

8. Enter password **<inject key="AzureAdUserPassword" />** and click on **Sign in**.

   ![ws name.](media/ch7.png)

   >**Note:** If there's a dialog box saying ***Help us protect your account***, then select **Skip for now** option.
 
   ![](media/login.png)

9. Click on **Close** button on the window asking *Your privacy option*.

   ![ws name.](media/ch19.png)

10. Once signed in, the application will look similar to the screenshot below 

    ![ws name.](media/ch8.png)

## **Task 2: Access the published Desktop**

1. On the top-left side of Remote Desktop Web Client, click on **All Resources**.
   
   ![ws name.](media/w12.png)
      
2. We will land on the AVD dashboard again. Click on the tile named *Session Desktop* to launch the desktop.

   ![ws name.](media/session.png)

3. Select **Allow** on the prompt asking permission to *Access local resources*.

   ![ws name.](media/allow.png)

4. Enter the lab credentials to access the application and click on **Submit**.

   - Username: **<inject key="AzureAdUserEmail" />** 
  
   - Password: **<inject key="AzureAdUserPassword" />**

   ![ws name.](media/89.png)

5. The virtual desktop will launch and look similar to the screenshot below. 

   ![ws name.](media/ex3t2s5.png)
   
6. Return back to the Azure Portal, search for *Azure virtual desktop* in the search bar and select **Azure Virtual Desktop** from the suggestions.

   ![ws name.](media/w1.png)

7. Click on **User** under *Manage* blade, then paste **<inject key="AzureAdUserEmail" />** in the search bar and click on your user to open it.

   ![ws name.](media/jvm7.png)

8. Click on **Sessions** tab, select both Host pools by clicking on the checkbox and then click on **Log off** button.

   ![ws name.](media/numbering.png)

9. Click on **OK** to *Log off user from VMs*.

   ![ws name.](media/jvm9.png)

10. Click on **Refresh** button and make sure *No results* is displayed under Host pool.

    ![ws name.](media/jvm10.png)

11. Click on the **Next** button present in the bottom-right corner of this lab guide. 
