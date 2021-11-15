# Lab 7: Load Balancing methods

Azure Virtual Desktop supports two load-balancing methods. Each method determines which session host will host a user's session when they connect to a resource in a host pool.
While configuring  a host pool, we can select load balancing methods as per the needs.

The following load-balancing methods are available in Azure Virtual Desktop:

 **1. Breadth-first**: Breadth-first load balancing distributes new user sessions across all available session hosts in the host pool. 

 **2. Depth-first**:  Depth-first load balancing distributes new user sessions to an available session host with the highest number of connections but has not reached its maximum session limit threshold.


## Exercise 1: Add new users to Azure Active Directory

1. In Azure Portal, click on the **Show portals menu** button and select **Azure Active Directory**.

   ![ws name.](media/lb34.png)

1. Click on **Users** under *Manage* blade.

   ![ws name.](media/2avd104.png)

1. Click on **+ New user** to add a new user.

   ![ws name.](media/2avd105.png)

1. Add the following configurations and leave rest to default:

   - User name: **AVDUser01**
   - Name: **AVDUser01**
   - Click on **Create**.

   ![ws name.](media/2avd106.png)

1. Click on **+ New user** to add one more user, then add the following configurations and leave rest to default.

   - User name: **AVDUser02**
   - Name: **AVDUser02**
   - Click on **Create**
   
   ![ws name.](media/2avd107.png)

1. Both the newly created users will show up similarly as shown below. Copy the **user principal name** of both users and paste in a text editor so that we can use it further.

   ![ws name.](media/user-v2.png)

1. Click on **AVDUser01** to open it. Then click on **Groups** under *Manage* blade and select **+ Add memberships**.

   ![ws name.](media/lb12.png)

1. Click on the **permission - fslogixcontainer** group and then click on **Select**.

   ![ws name.](media/2avd43.png)

1. Click on **AVDUser02** to open it. Then click on **Groups** under *Manage* blade and select **+ Add memberships**.

   ![ws name.](media/im31.png)

1. Click on the **permission - fslogixcontainer** group and then click on **Select**.

   ![ws name.](media/2avd43.png)

1. Navigate to the host pool *EB-AVD-HP* and open **Application groups** present under *Manage* blade. Two application groups will be listed there.

    ![ws name.](media/2avd87.png)

1. Open application group **EB-AVD-HP-DAG** and click on **Assignments** under *Manage* blade.

    ![ws name.](media/2avd89.png)
   
1. Click on **+ Add**, then in the search bar, type *AVDUser* and select both **AVDUser01** & **AVDUser02** that we created earlier. At last, click on **Select** button.

    ![ws name.](media/2avd109.png)

1. Once done, the users assigned to the Application group will look similar to the image given below.

    ![ws name.](media/2avd93.png)
     
## Exercise 2: Update Passwords for the new users

Here, we will use Azure Cloud Shell to run a script that will change the passwords for the users created, as user needs to reset password after registering to AADDS. 

1. In Azure portal, click on the **Cloud Shell** icon.

   ![ws name.](media/a105.png)
   
2. In the Cloud Shell window that opens at the bottom of your browser window, select **PowerShell**.

   ![ws name.](media/wvd10.png)

3. Click on **Show Advanced Settings**.

   ![ws name.](media/wvd11.png)

4. Use exisiting resource group - **AVD-RG** from the drop down and for:

   >**Note:** **UniqueID** is the numerical value present in your username. 
   >For example, if your username is *odl_user_258996@azurehol1004.onmicrosoft.com*, the *UniqueID* will be 258996.

   - Storage Account: Select **Create new** and enter **sa{uniqueid}**, where **uniqueid** is the numerical value present in your username. 
   - File Share: Select **Create new** and enter **fs{uniqueid}**, where **uniqueid** is the numerical value present in your username.

   ![ws name.](media/wvd12.png)

5. After the terminal launches it will look like this.

   ![ws name.](media/40.png)

6. Copy and paste the following script and hit **Enter**.

   ```
   $domain = ((Get-AzADUser | where {$_.Type -eq "Member"}).UserPrincipalName.Split('@'))[1]
   $password= ConvertTo-SecureString "Azure1234567" -AsPlainText -Force
   $users = @("AVDUser01@$domain","AVDUser02@$domain")
   $users | foreach{
       Update-AzADUser -UserPrincipalName $_ -Password $password
   }
   ```
 
   ![ws name.](media/pu2.png)
 
7. Output of the script will be similar to the one shown below. The password for both **AVDUser01** and **AVDUser02** is reset to **Azure1234567**.

   ![ws name.](media/pu1.png)

   >**Note**: ***Username*** and ***Password*** for ***AVDUser01*** and ***AVDUser02*** is present in Environment Details tab.

## Exercise 3: Change and experience Load Balancing methods

**A**. **Breadth-first**
   
While creating EB-AVD-HP host pool, we selected load balancing method as *Breadth-first*.  Now we are going to log in to Desktop App created on EB-AVD-HP with both users simultaneously and see the user distribution.

1. Paste the below mentioned link in your browser in the **JumpVM** and enter your **credentials** to login. 

   ```
   aka.ms/wvdarmweb
   ```

   - Username: *Paste the username*  **<inject key="Avd User 01" />** then click on **Next**.*
   
   ![ws name.](media/username.png)

   - Password: *Paste the password*  **<inject key="AVD User Password" />** *and click on* **Sign in**.

   ![ws name.](media/password.png)

   >**Note:** If there's a dialog box saying ***Help us protect your account***, then select **Skip for now** option.

   ![](media/login1.png)

1. Now in the AVD dashboard, click on the **Session Desktop** to access it. 

   ![ws name.](media/desktp-v2.png)

1. Select **Allow** on the prompt asking permission to *Access local resources*.

   ![ws name.](media/Accessallowres-v2.png)

1. Enter your **credentials** to access the application and click on **Submit**.

   - Username: *Paste the username*  **<inject key="Avd User 01" />** then click on **Next**.*
   
   - Password: *Paste the password*  **<inject key="AVD User Password" />** *and click on* **Sign in**.
   
   ![ws name.](media/lb52.png)

1. The virtual Desktop will launch as shown below. 

   ![ws name.](media/newrd2.png)
   
1. Navigate to **Your Own PC/computer/workstation**, go to **Start** and search for **Remote desktop** and open the application with the exact icon as shown below.

   ![ws name.](media/137.png)
   
1. Click on the *ellipses* and select **Unsubscribe**. Click on **Yes** for any warning.

   ![ws name.](media/lb16.png)

   >**Note:** We need to unsubscribe from the feed, because in Exercise 4 we subscribed to AVD feed using a different user.

1. Click on **Subscribe** button.

   ![ws name.](media/a49.png)

1. Enter the user credentials to access the workspace.

   - Username: *Paste the username*  **<inject key="Avd User 02" />** *then click on* **Next**.
   
   - Password: *Paste the password*  **<inject key="AVD User Password" />** *and click on* **Sign in**.

   ![ws name.](media/password2.png)

   >**Note:** If there's a dialog box saying ***Help us protect your account***, then select **Skip for now** option.

   ![](media/login2.png)
    
1. Make sure to **uncheck** *Allow my organization to manage my device* and click on **No, sign in to this app only**.

   ![ws name.](media/ex4t1s9.png)

1. In AVD client, double click on the **Session Desktop** to access it. 

   ![ws name.](media/desktp-v2.png)

1. Enter your **credentials** to access the application and click on **Submit**.

   - Username: *Paste the username*  **<inject key="Avd User 02" />** then click on **Next**.*
   - Password: *Paste the* **<inject key="AVD User Password" />** *and click on* **OK**.* 
   
   ![ws name.](media/lb37.png)
  
1. The virtual Desktop will launch as shown below. 

   ![ws name.](media/newrd3.png) 

1. Return to the Azure portal in your browser inside the **JumpVM**, search for *host pools* and click on **Host pool** from the suggestion to open it.

   ![ws name.](media/lb38.png)
   
1. Now click on **EB-AVD-HP** host pool to access it.

   ![ws name.](media/2avd91.png)
 
1. Under Manage blade, click on **Session hosts**.

   ![ws name.](media/2avd92.png)
   
1. You can see that both session hosts have one Active sessions each.

   ![ws name.](media/2avd101.png)
   
   >**Note:** This shows how users are distributed among different session hosts under *Breadth-first load balancing method*. The breadth-first method first queries session hosts that allow new connections. The method then selects a session host randomly from half the set of session hosts with the least number of sessions. 
   > 
   >Please follow [Breadth-first Load-Balancing Method](https://docs.microsoft.com/en-us/azure/virtual-desktop/host-pool-load-balancing#breadth-first-load-balancing-method) to learn more about it.

1. Open **AVD-HP01-SH-0** session host, there you can see the user logged in to that session host. Now select the user and click on **Log off all active users** button and select **Yes** to the prompt asking *Do you want to Log off active users of the virtual machine*.

   ![ws name.](media/2avd99.png)

1. Navigate back to *Session hosts* and open **AVD-HP01-SH-1** session host, there you can see the user logged in to that session host. Now select the user and click on **Log off all active users** button and select **Yes** to the prompt asking *Do you want to Log off active users of the virtual machine*.

   ![ws name.](media/2avd100.png)

   >**Note:** We need to log off the users from session hosts so that when the users login again, connection is made based on the *Depth-first load balancing method*.
  
**B**. **Depth first**
   
   Here we will change the load balancing method of *EB-AVD-HP* host pool to *Depth first* and see how user distribution changes in the Host pool.

   >**Note:** If previous session is closed, visit to  `aka.ms/wvdarmweb`, then click on *Default Desktop* and login with *AVDUser01* credentials.

1. In *EB-AVD-HP* host pool, click on **Properties** under *Settings* blade.

   ![ws name.](media/2avd95.png)
   
1. Change the load balancing algorithm to **Depth-first** then click on **Save icon**.

   ![ws name.](media/2avd102.png)
   
1. Paste the below mentioned link in your browser in the **JumpVM** and enter your **credentials** to login. 

   ```
   aka.ms/wvdarmweb
   ```
   
   >**NOTE**: If the session desktop is disconnected. Close the tab and perform the next step.
   
1. In the AVD dashboard, click on the **Session Desktop** to access it. 

   ![ws name.](media/desktp-v2.png)

1. Select **Allow** on the prompt asking permission to *Access local resources*.

   ![ws name.](media/Accessallowres-v2.png)

1. Enter your **credentials** to access the application and click on **Submit**.

   - Username: *Paste the username*  **<inject key="Avd User 01" />** then click on **Next**.*
   
   - Password: *Paste the password* **<inject key="AVD User Password" />**.
   
   ![ws name.](media/lb52.png)

1. The virtual Desktop will launch as shown below. 

   ![ws name.](media/newrd2.png)
    
1. Navigate to **Your Own PC/computer/workstation**, go to **Start** and search for **Remote desktop** and open the application with the exact icon as shown below.

   ![ws name.](media/137.png)

1. In AVD client, double click on the **Session Desktop** to access it. 

   ![ws name.](media/desktp-v2.png)

1. Enter your **credentials** to access the application and click on **Submit**.

   - Username: *Paste the username*  **<inject key="Avd User 02" />** *then click on **Next**.*
   - Password: *Paste the* **<inject key="AVD User Password" />** *and click on **OK**.* 
   
   ![ws name.](media/lb37.png)
  
1. The virtual Desktop will launch as shown below. 

   ![ws name.](media/newrd3.png) 

1. Return back to the Azure portal in the **JumpVM**, navigate to **EB-AVD-HP** host pool and open **Session Hosts** present under *Manage* blade.

    ![ws name.](media/2avd103.png)
   
1. Here one of the session hosts, either *AVD-HP01-SH-0* or *AVD-HP01-SH-1* will have 2 Active sessions. Click on that session host to open it.

    ![ws name.](media/lb21.png)
   
    >**Note:** The depth-first method first queries session hosts that allow new connections and haven't gone over their maximum session limit. The method then selects the session host with highest number of sessions. If there's a tie, the method selects the first session host in the query.
    >
    >Please follow [Depth-first Load-Balancing Method](https://docs.microsoft.com/en-us/azure/virtual-desktop/host-pool-load-balancing#depth-first-load-balancing-method) to learn more about it.
   
1. Verify that both users have been assigned to the particular session host. 

    ![ws name.](media/uiupdate16.png)

    >**[Optional]**
    >
    >**Scale session hosts using Azure Automation**
    >
    >Here, you will learn about the scaling tool built with the Azure Automation account and Azure Logic App that automatically scales session host VMs in your Azure Virtual Desktop environment. 
    >
    >Please follow the link given below to learn more about this feature. 
    >
    >```https://docs.microsoft.com/en-us/azure/virtual-desktop/set-up-scaling-script```

Click on the **Next** button present in the bottom-right corner of this lab guide.
