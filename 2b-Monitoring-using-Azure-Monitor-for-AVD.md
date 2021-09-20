# Lab 2: Monitoring using Azure Monitor for AVD(Part 2)

1. In your PC go to **Start** and search for **Remote desktop** and open the remote desktop application with exact icon as shown below.

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
      
1. The WVD dashboard will launch, then double click on **Excel** application to access it.

    ![ws name.](media/remotedesktop.png)
   
1. A window saying *Starting your app*, will appear. Wait for few seconds, then enter your password to access the Application.

    - Password: **<inject key="AzureAdUserPassword" />**
   
    ![ws name.](media/ch14.png)

1. Wait for the Application to connect.

    ![ws name.](media/58.png)
   
1. The Excel application will launch and look similar to the screenshot below.

    ![ws name.](media/ch15.png) 
    
   >**NOTE**: Keep the application open and do not close the Remote Desktop client.
   
1. Paste the below mentioned link in your browser in the **JumpVM** and enter your **credentials** to login. 

   ```
   aka.ms/wvdarmweb
   ```

   - Username: *Copy* **AVDUser01** *username from the **Environment Details tab** and paste it then click on **Next**.*
   
   ![ws name.](media/username.png)

   - Password: *Paste the password* **Azure1234567** *and click on* **Sign in**.

   ![ws name.](media/password.png)

   >**Note:** If there's a dialog box saying ***Help us protect your account***, then select **Skip for now** option.

   ![](media/login1.png)

1. Now in the AVD dashboard, click on the **Session Desktop** to access it. 

   ![ws name.](media/newrd1.png)

1. Select **Allow** on the prompt asking permission to *Access local resources*.

   ![ws name.](media/2avd31.png)

1. Enter your **credentials** to access the application and click on **Submit**.

   - Username: *Paste the username*  **<inject key="Avd User 01" />**
   
   - Password: *Paste the password*  **<inject key="AVD User Password" />**
   
   ![ws name.](media/lb52.png)

1. The virtual Desktop will launch as shown below. 

   ![ws name.](media/newrd2.png)
   
1. Now, Navigate to Azure Virtusl Desktop and select **Insights** under **Monitoring** blade in the Azure Portal.

   ![ws name.](media/mon2.png)
