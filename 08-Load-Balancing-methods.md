# **Exercise 7: Load Balancing methods**

Windows Virtual Desktop supports two load-balancing methods. Each method determines which session host will host a user's session when they connect to a resource in a host pool.
While configuring  a host pool, we can select load balancing methods as per the needs.

The following load-balancing methods are available in Windows Virtual Desktop:

 **1. Breadth-first**: Breadth-first load balancing distributes new user sessions across all available session hosts in the host pool. 

 **2. Depth-first**:  Depth-first load balancing distributes new user sessions to an available session host with the highest number of connections but has not reached its maximum session limit threshold.


### **Task 1: Add new users to Azure Active Directory**

1. In Azure Portal, click on the **Show portals menu** button and select **Azure Active Directory**.

   ![ws name.](media/lb34.png)

2. Click on **Users** under *Manage* blade.

   ![ws name.](media/lb6.png)

3. Click on **+ New user** to add a new user.

   ![ws name.](media/lb5.png)

4. Add the following configurations and leave rest to default:

   - User name: **WVDUser01**
   - Name: **WVDUser01**
   - Click on **Create**.

   ![ws name.](media/lb8.png)

5. Click on **+ New user** to add one more user, then add the following configurations and leave rest to default.

   - User name: **WVDUser02**
   - Name: **WVDUser02**
   - Click on **Create**
   
   ![ws name.](media/lb7.png)

6. Both the newly created users will show up similarly as shown below. Copy the **user principal name** of both users and paste in a text editor so that we can use it further.

   ![ws name.](media/lb11.png)

7. Click on **WVDUser01** to open it. Then click on **Groups** under *Manage* blade and select **+ Add memberships**.

   ![ws name.](media/lb12.png)

8. Click on the **AAD DC Administrators** group and then click on **Select**.

   ![ws name.](media/lb13.png)

9. Click on **WVDUser02** to open it. Then click on **Groups** under *Manage* blade and select **+ Add memberships**.

   ![ws name.](media/im31.png)

10. Click on the **AAD DC Administrators** group and then click on **Select**.

   ![ws name.](media/lb13.png)

11. Navigate to the host pool *WVD-HP-01* and open **Application groups** present under *Manage* blade. Two application groups will be listed there.

   ![ws name.](media/lb40.png)

12. Open application group **WVD-HP-01-DAG** and click on **Assignments** under *Manage* blade.

   ![ws name.](media/lb41.png)
   
13. Click on **+ Add**, then in the search bar, type *WVDUser* and select both **WVDUser01** & **WVDUser02** that we created earlier. At last, click on **Select** button.

   ![ws name.](media/lb42.png)

14. Once done, the users assigned to the Application group will look similar to the image given below.

   ![ws name.](media/lb45.png)
   
   
### **Task 2: Update Passwords for the new users**

Here, we will use Azure Cloud Shell to run a script that will change the passwords for the users created, as user needs to reset password after registering to AADDS. 

1. In Azure portal, click on the **Cloud Shell** icon.

   ![ws name.](media/a105.png)
   
2. In the Cloud Shell window that opens at the bottom of your browser window, select **PowerShell**.

   ![ws name.](media/wvd10.png)

3. Click on **Show Advanced Settings**.

   ![ws name.](media/wvd11.png)

4. Use exisiting resource group - **WVD-RG** from the drop down and for:

    - Storage Account: Select **Create new** and enter **sa{uniqueid}**
    - File Share: Select **Create new** and enter **fs{uniqueid}**

> **Note:** **UniqueID** is the numerical value present in your username. 
> For example, your username is *odl_user_258996@azurehol1004.onmicrosoft.com*; so your UniqueID will be 258996.

   ![ws name.](media/wvd12.png)

5. After the terminal launches it will look like this.

   ![ws name.](media/40.png)

6. Copy and paste the following script and hit **Enter**.

   ```
   $domain = ((Get-AzADUser | where {$_.Type -eq "Member"}).UserPrincipalName.Split('@'))[1]
   $password= ConvertTo-SecureString "Azure1234567" -AsPlainText -Force
   $users = @("WVDUser01@$domain","WVDUser02@$domain")
   $users | foreach{
       Update-AzADUser -UserPrincipalName $_ -Password $password
   }
   ```
 
   ![ws name.](media/pu2.png)
 
7. Output of the script will be similar to the one shown below. The password for both **WVDUser01** and **WVDUser02** is reset to **Azure1234567**.

   ![ws name.](media/pu1.png)

> **Note:** Make sure you have noted down the ***Username*** and ***Password*** for ***WVDUser01*** and ***WVDUser02***.


### **Task 3: Change and experience Load Balancing methods**


**A**. **Breadth-first**
   
While creating WVD-HP-01 host pool, we selected load balancing method as *Breadth-first*.  Now we are going to log in to Desktop App created on WVD-HP-01 with both users simultaneously and see the user distribution.


1. Paste this link ```aka.ms/wvdarmweb``` in your browser in the **JumpVM** and enter your **credentials** to login. 

   - Username: *Paste username* **WVDUser01** *which you copied earlier and then click on **Next**.*
   
   ![ws name.](media/username.png)

   - Password: *Paste the password **Azure1234567** and click on **Sign in**.

   ![ws name.](media/password.png)
 

2. Now in the WVD dashboard, click on the **Default Desktop** to access it. 

   ![ws name.](media/im29.png)

3. Select **Allow** on the prompt asking permission to *Access local resources*.

   ![ws name.](media/lb27.png)

4. Enter your **credentials** to access the application and click on **Submit**.

   - Username: *Paste username of* **WVDUser01** *which you copied earlier(for example: **WVDUser01@azurehol1055.onmicrosoft.com**)*
   
   - Password: *Paste the password* **Azure1234567**
   
   ![ws name.](media/lb52.png)


6. The virtual Desktop will launch as shown below. 

   ![ws name.](media/lb57.png)
   
7. Navigate to **Your Own PC/computer/workstation**, go to **Start** and search for **Remote desktop** and open the application with the exact icon as shown below.

   ![ws name.](media/137.png)
   
8. Click on the *ellipses* and select **Unsubscribe**. Click on **Yes** for any warning.

   ![ws name.](media/lb16.png)

> **Note:** We need to unsubscribe from the feed, because in Exercise 4 we subscribed to WVD feed using a different user.

9. Click on **Subscribe** button.

   ![ws name.](media/a49.png)

10. Enter the user credentials to access the workspace.

   - Username: *Paste username of* **WVDUser02** *which you copied earlier(for example: **WVDUser02@azurehol1055.onmicrosoft.com**), then click on **Next**.*
   
   - Password: *Paste the password* **Azure1234567**.

   ![ws name.](media/password2.png)

11. In WVD client, double click on the **Default Desktop** to access it. 

   ![ws name.](media/im30.png)

12. Enter your **credentials** to access the application and click on **Submit**.

   - Username: *Paste username of* **WVDUser02** *which you copied earlier(for example: **WVDUser02@azurehol1055.onmicrosoft.com**)*
   - Password: *Paste the **Azure1234567** and click on **OK**.* 
   
   ![ws name.](media/lb37.png)
  

13. The virtual Desktop will launch as shown below. 

   ![ws name.](media/lb55.png) 


14. Return to the Azure portal in your browser inside the **JumpVM**, search for *host pools* and click on **Host pool** from the suggestion to open it.

   ![ws name.](media/lb38.png)
   
   
15. Now click on **WVD-HP-01** host pool to access it.

   ![ws name.](media/lb39.png)
   
   
16. Under Manage blade, click on **Session hosts**.

   ![ws name.](media/lb24.png)
   
   
17. You can see that both session hosts have one Active sessions each.

   ![ws name.](media/lb47.png)
   
> **Note:** This shows how users are distributed among different session hosts under *Breadth-first load balancing method*. The breadth-first method first queries session hosts that allow new connections. The method then selects a session host randomly from half the set of session hosts with the least number of sessions. 
> 
> Please follow [Breadth-first Load-Balancing Method](https://docs.microsoft.com/en-us/azure/virtual-desktop/host-pool-load-balancing#breadth-first-load-balancing-method) to learn more about it.


18. Open **WVD-HP01-SH-0** session host, there you can see the user logged in to that session host. Now click on **Log off all active users** button and select **Yes** to the prompt asking *Do you want to Log off active users of the virtual machine*.

   ![ws name.](media/lb50.png)

19. Navigate back to *Session hosts* and open **WVD-HP01-SH-1** session host, there you can see the user logged in to that session host. Now click on **Log off all active users** button and select **Yes** to the prompt asking *Do you want to Log off active users of the virtual machine*.

   ![ws name.](media/lb56.png)

>**Note:** We need to log off the users from session hosts so that when the users login again, connection is made based on the *Depth-first load balancing method*.
   

**B**. **Depth first**

Here we will change the load balancing method of *WVD-HP-01* host pool to *Depth first* and see how user distribution changes in the Host pool.

> **Note:** If previous session is closed, visit to  `aka.ms/wvdarmweb`, then click on *Default Desktop* and login with *WVDUser01* credentials.

1. In *WVD-HP-01* host pool, click on **Properties** under *Settings* blade.

   ![ws name.](media/lb25.png)
   
   
2. Change the load balancing algorithm to **Depth-first** then click on **Save icon**.

   ![ws name.](media/lb26.png)
   
3. Now paste this link ```aka.ms/wvdarmweb``` in your browser inside the **JumpVM**, and enter your **credentials** to login. 

   - Username: *Paste username of* **WVDUser01** *which you copied earlier(for example: **WVDUser01@azurehol1055.onmicrosoft.com**)* and then click on **Next**.
   
   ![ws name.](media/username.png)

   - Password: *Paste the password **Azure1234567** and click on **Sign in**.*

   ![ws name.](media/password.png)
 

4. In the WVD dashboard, click on the **Default Desktop** to access it. 

   ![ws name.](media/im29.png)

5. Select **Allow** on the prompt asking permission to *Access local resources*.

   ![ws name.](media/lb27.png)

6. Enter your **credentials** to access the application and click on **Submit**.

   - Username: *Paste username of* **WVDUser01** *which you copied earlier(for example: **WVDUser01@azurehol1055.onmicrosoft.com**)*
   
   - Password: *Paste the password* **Azure1234567**
   
   ![ws name.](media/lb52.png)


7. The virtual Desktop will launch as shown below. 

   ![ws name.](media/lb57.png)
   
   
8. In **Your Own PC/computer/workstation**, go to **Start** and search for **Remote desktop** and open the application.

   ![ws name.](media/137.png)
   

9. Now in the WVD client double click on the **Default Desktop** to access it. 

   ![ws name.](media/im30.png)

10. Enter your **credentials** to access the desktop and click on **Submit**.

   - Username: *Paste username of* **WVDUser02** *which you copied earlier(for example: **WVDUser02@azurehol1055.onmicrosoft.com**).*
   - Password: *Paste the password* **Azure1234567**
   

   ![ws name.](media/lb51.png)
   

11. The virtual Desktop will launch as shown below. 

   ![ws name.](media/lb55.png) 


12. Return back to the Azure portal in the **JumpVM**, navigate to **WVD-HP-01** host pool and open **Session Hosts** present under *Manage* blade.

   ![ws name.](media/lb24.png)
   
   
13. Here one of the session hosts, either *WVD-HP01-SH-0* or *WVD-HP01-SH-1* will have 2 Active sessions. Click on that session host to open it.

   ![ws name.](media/lb21.png)
   
> **Note:** The depth-first method first queries session hosts that allow new connections and haven't gone over their maximum session limit. The method then selects the session host with highest number of sessions. If there's a tie, the method selects the first session host in the query.
>
> Please follow [Depth-first Load-Balancing Method](https://docs.microsoft.com/en-us/azure/virtual-desktop/host-pool-load-balancing#depth-first-load-balancing-method) to learn more about it.
   
14. Verify that both users have been assigned to the particular session host. 

   ![ws name.](media/lb22.png)



> **[Optional]**
>
> **Scale session hosts using Azure Automation**
>
> Here, you will learn about the scaling tool built with the Azure Automation account and Azure Logic App that automatically scales session host VMs in your Windows Virtual Desktop environment. 
>
> Please follow the link given below to learn more about this feature. 
>
> ```https://docs.microsoft.com/en-us/azure/virtual-desktop/set-up-scaling-script```
>

Click on the **Next** button present in the bottom-right corner of this lab guide.

