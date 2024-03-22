# Lab 4: Access the Published Applications and Desktop using Browser

## **Scenario**

Contoso wants to provide employees with flexible access to their Azure Virtual Desktop environment. In this lab you will help Contoso test access to Azure Virtual Desktop sessions using a browser. 

## **Overview**

In this exercise, we will access the Desktop and RemoteApps assigned to us in lab 3 using a browser. 

## Exercise 1: Access the Published Application

1. Open the following URL in a new browser tab in the JumpVM. This URL will lead us to the Remote Desktop Web Client.

   ``` 
   aka.ms/wvdarmweb 
   ``` 

   >**Note:**  If you are already logged in to your user account, jump to step 3 else continue with the next step i.e., Step 2.

1. To login, enter the lab credentials below:

   - Username: *Paste your username* **<inject key="AzureAdUserEmail" />** *and then click on **Next**.*
   
   ![ws name.](media/95.png)

   - Password: *Paste the password* **<inject key="AzureAdUserPassword" />** *and click on **Sign in**.*

   ![ws name.](media/96.png)

   >**Note:** If there's a dialog box saying ***Help us protect your account***, then select the **Skip for now** option.

   ![](media/login.png)

1. The AVD dashboard will launch. Click on **Word** to access it.  

   ![ws name.](media-2/word.png)

1. Select **Allow** on the prompt asking permission to *Access local resources*.

   ![ws name.](media/Accessallowres-v2.png)

1. Enter the lab credentials to access the application and click on **Submit**.

   - Username: **<inject key="AzureAdUserEmail" />** 
  
   - Password: **<inject key="AzureAdUserPassword" />**

   ![ws name.](media/89.png)
      
1. The Word application will launch and look similar to the screenshot below. Click on **Sign in**.

   ![ws name.](media/ch9.png)
   
   >**Note:**  If you see a Blank Screen while launching the application, restart the AVD Session Hosts. To do so; follow the below steps:
   > - Navigate back to the Azure Portal and search for **Virtual Machines** from search bar.
   > - Select the two AVD VMs and then click on the **RESTART** button from the top ribbon menu.
   > - After a minute or two; once the AVD Session host VMs are restarted; try the step again.

1. Enter username **<inject key="AzureAdUserEmail" />** on *Activate Office* window and click on **Next**.

   ![ws name.](media/ch6.png)

   >**Note:** If you get a popup saying *Move Text in and out of Remote Desktop*, click on the ***Don't show again*** checkbox and then click on the ***Got it button***.
   
   ![ws name.](media/uiupdate06.png)

1. Enter password **<inject key="AzureAdUserPassword" />** and click on **Sign in**.

   ![ws name.](media/ch7.png)

   >**Note:** If there's a dialog box saying ***Help us protect your account***, then select the **Skip for now** option.
 
   ![](media/login.png)

1. Click on the **Close** button on the window asking *Your privacy option*.

   ![ws name.](media/ch19.png)

1. Once signed in, the application will look like the screenshot below.

   ![ws name.](media/ch8.png)

## Exercise 2: Access the published Desktop

1. On the top-left side of Remote Desktop Web Client, click on **All Resources**.
   
   ![ws name.](media-1/L4E2S1.png)
      
1. We will land on the AVD dashboard again. Click on the tile named **Session Desktop** to launch the desktop.

   ![ws name.](media-2/sessiondesktop.png)

1. Select **Allow** on the prompt asking permission to *Access local resources*.

   ![ws name.](media/Accessallowres-v2.png)

1. Enter the lab credentials to access the application and click on **Submit**.

   - Username: **<inject key="AzureAdUserEmail" />** 
  
   - Password: **<inject key="AzureAdUserPassword" />**

   ![ws name.](media/89.png)

1. The virtual desktop will launch and look similar to the screenshot below. 

   ![ws name.](../Azure-Virtual-Desktop-v3/media/sessiondesktop.png)
   
   > **Note:** If you see a black screen while launching the session desktop, please re-start the session desktop by re-performing the lab from step 2.
   
1. Return back to the Azure Portal, search for *Azure virtual desktop* in the search bar, and select **Azure Virtual Desktop** from the suggestions.

   ![ws name.](media/w1.png)

1. Click on **Users** under *Manage* blade, then paste **<inject key="AzureAdUserEmail" />** in the search bar and click on your user to open it.

   ![ws name.](media/AVD-users.png)

1. Click on the **Sessions (1)** tab, select both Host pools by clicking on the checkbox **(2)** and then click on the **Log off (3)** button.

   ![ws name.](media-2/session.png)

1. Click on **OK** to *Log off user from VMs*.

   ![ws name.](media/jvm9.png)

1. Click on the **Refresh** button and make sure no results are displayed under the Host pool.

   ![ws name.](media-1/Ex4-task2-step10.png)

1. Click on the **Next** button present in the bottom-right corner of this lab guide. 
