# Lab 2b: Monitoring using Azure Monitor for AVD


   ![ws name.](media/lb16.png)

   >**Note:** We need to unsubscribe from the feed, because in Exercise 4 we subscribed to AVD feed using a different user.

1. Click on **Subscribe** button.

   ![ws name.](media/a49.png)

1. Enter the user credentials to access the workspace.

   - Username: *Paste the username*  **<inject key="Avd User 02" />** *then click on* **Next**.
   
   - Password: *Paste the password*  **<inject key="AVD User Password" />** *and click on* **Sign in**.

   ![ws name.](media/password2.png)

   >**Note**: If there's a dialog box saying ***Help us protect your account***, then select **Skip for now** option.

   ![](media/login2.png)
    
1. Make sure to **uncheck** *Allow my organization to manage my device* and click on **No, sign in to this app only**.

   ![ws name.](media/ex4t1s9.png)

1. In AVD client, double click on the **Session Desktop** to access it. 

   ![ws name.](media/newrd.png)

1. Enter your **credentials** to access the application and click on **Submit**.
   
   ![ws name.](media/lb37.png)
  
1. The virtual Desktop will launch as shown below. 

   ![ws name.](media/newrd3.png)

1. The virtual Desktop will launch as shown below. 

   ![ws name.](media/newrd2.png)

   ![ws name.](media/mon2.png)
   
1. In **Insights** page, **Click** on **Overview** tab *(1)*. Here **expand** *(2)* the **EB-AVD-HP** host pool. You'll be able to monitor the status and health of the session hosts (3).

   ![ws name.](media/mon21.png)
   
1. **Click** on **Users** *(1)* tab, In **UPN to search for** blank paste **<inject key="Avd User 01" />** *(2)* and wait for the data to load. This tab gives overview of the user's usage. Scroll down and explore different information loaded.

   ![ws name.](media/mon23.png)
   
1. **Click** on **Utilization** tab, This tab gives information about sessions summary, cores info, and more information about the utilization of resources.

   ![ws name.](media/mon24.png)
   
1. **Click** on **Clients** *(1)* tab, Here you'll be able monitor the number of users connected to AVD using browser and remote client application.

   ![ws name.](media/mon22.png)
   
1. Spend some time on the page to explore different monitoring abilities offered by Azure Insights.

1. Click on the Next button present in the bottom-right corner of this lab guide.
   
