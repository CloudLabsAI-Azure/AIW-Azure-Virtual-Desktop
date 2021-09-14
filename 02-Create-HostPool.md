# Exercise 1: Create Host Pool from Azure Portal

 A Host Pool is a collection of Azure virtual machines that register to Azure Virtual Desktop as session hosts when you run the Azure Virtual Desktop agent. All session host virtual machines in a host pool should be sourced from the same image for a consistent user experience. To start with, we will login to the Azure portal. 
 
### Getting Started with Lab	

1. Once you launch the lab, a virtual machine (JumpVM) on the left and lab guide on the right will get loaded in your browser. Use this virtual machine throughout the workshop to perform the lab.	

   ![](media/jumpvm.png)	

2. To get lab environment details, click on the **Environment Details** tab located next to the *Lab Guide* tab. 	

   ![](media/environmentdetails.png)	

### **Task 1: Log in to Azure Portal**

1. In the JumpVM, double click on the **Azure portal shortcut** on the desktop.

   ![azure portal.](media/portal_avd.png)  

2. Login to Azure with the username **<inject key="AzureAdUserEmail" />** and click on **Next**.

   ![](media/w24.png)

3. Enter password **<inject key="AzureAdUserPassword" />** and click on **Sign in**.

   ![](media/w25.png)

   >**Note:** If there's a popup entitled **Stay signed in?** with buttons for **No** and **Yes** - Choose **No**.
   
    ![](media/w26.png)
      
   >**Note:** If there's another popup entitled **Welcome to Microsoft Azure** with buttons for **Start Tour** and **Maybe Later** - Choose **Maybe Later**.
   
    ![](media/wvd.png) 
   
   >**Note:** If there's another popup entitled **Help us protect your account** click **Skip for now (14 days intil this is required)**
   
    ![](media/skipfornow.png)

4. Now in the Azure portal, click on **Resource Groups** present under *Navigate*.

   ![](media/jvm3.png)

5. You will see a list of resource groups as show in the image below. Click on **AVD-RG** to open it.

   ![](media/jvm4.png)
   
   >**Note:** You will be using ***AVD-RG*** throughout the lab. Other two resource groups listed in the portal are not to be used in the lab.


### **Task 2: Create Host Pool**

In this exercise, we will create a Host Pool named *AVD-HP-01* of pooled type, then add two session hosts (virtual machines) i.e. *AVD-HP01-SH-0* and *AVD-HP01-SH-1*  and register the default desktop application group from this hostpool to a new workspace named *AVD-WS-01*.

1. On **Azure portal** search for *Azure Virtual Desktop* in the search bar (1) and select **Azure Virtual Desktop** (2) from the suggestions.

   ![ws name.](media/avd1.png) 

2. You will get directed towards the Azure Virtual Desktop (here after referred to as AVD) management window. Select **Host pools** under **Manage** blade

   ![ws name.](media/avd2.png)

3. Now, click on **+ Create** to add create new Host Pool.

   ![ws name.](media/avd3.png)

4. In this step, we will provide the details required to create a Host Pool. For your convenience, this step is divided into two sections as follows:

   **Project Details – (A)** Defines the Host Pool environment 

   - Subscription: *Choose the default subscription*.
   - Resource Group: *Select **AVD-RG** from the drop down*.
   - Host Pool Name: **AVD-HP-01**
   - Location: **East US**, *basically this should be same as the region of your resource group*.      
   - Validation environmet: **No**
      
   >**Note:** Validation host pools let you monitor service updates before rolling them out to your production environment.
            
   **Host Pool Type – (B)** Defines the type of host pool. 

   - Host pool type: **Pooled** 
        
   > **Note:** Host Pools are of 2 types: Pooled and Personal.  
   > - **Pooled**, where session hosts can accept connections from any user authorized to an app group within the host pool.
   > - **Personal**, where each session host is assigned to individual users.
     
   - Load Balancing Algorithm: **Breadth First**
   
   > **Note:** Load Balancing Algorithm is of two types: *Breadth-first* and *Depth-first*. 
   > - **Breadth-first** load balancing allows you to evenly distribute user sessions across the session hosts in a host pool. 
   > - **Depth-first** load balancing allows you to saturate a session host with user sessions in a host pool. 

   - Max session Limit: **5**   
      
   > **Note:** Max session Limit limits the simultaneous number of users on the same session host.
   
   - Then click on **Next:Virtual Machines**.
   
   ![ws name.](media/avd4.png)  
   
5. In the Virtual machines tab, select **Yes** against **Add virtual machines**. By doing this, we are stepping towards adding Virtual machines to the host pool. 

   ![ws name.](media/66.png)

6. In this step, we will provide the details of the VMs to be created as session Hosts. For your convenience, this step is divided into three sections as follows:

   **A**. Session Host Specifications:     

   - Resource Group: *Select **AVD-RG** from the drop down*.
   - Name prefix: **AVD-HP01-SH** 
   - Virtual machine location: **East US**, *location should be same as location of your resource group*.
   - Availability options: _Select_ **No infrastructure redundancy required** _from the drop down_.
   - Image type: **Gallery**
   - Image: **Windows 10 Enterprise multi-session, version 1909 + Microsoft 365 Apps** *(choose from dropdown)*
   - Virtual machine size: **Standard D4s_v3**. *Click on **Change Size**, then select **D4s_v3** and click on **Select** as shown below*
   
   ![ws name.](media/ch1.png)

   - Number of VMs: **2**
   - OS disk type: **Standard SSD**
   - Use managed disks: *Leave to default*
   - Boot Diagnostics: **Disable**
   
   ![ws name.](media/uiupdate02.png)
    
   **B**. Network and Security:
    
   Leave all values to default, except:
    
   - Virtual network: **aadds-vnet** *(choose from dropdown)*
   - Subnet: **sessionhosts-subnet(10.0.1.0/24)** *(choose from dropdown)*
   - Public inbound ports: **No**
 
   ![ws name.](media/network-security.png)
 
   **C**. Domain Administrator Account:
  
   - Select which directory you would like to join: Choose **Azure Directory** from dropdown
   - AD domain join UPN: *Paste your username* **<inject key="AzureAdUserEmail" />**
   - Password: *Paste the password* **<inject key="AzureAdUserPassword" />**
   - Specify Domain or Unit: **No**
   
   ![ws name.](media/domainjoin.png)

   > **Note:** This Administrator Account details will be used for domain joining the virtual machines to the Windows AD domain we created using AADDS.

   **D**. Virtual Machine Administrator Account:
  
   - Username: **hostadmin**
   - Password: *Paste the password* **<inject key="AzureAdUserPassword" />**
   - Confirm Password: *Paste the password* **<inject key="AzureAdUserPassword" />** *again.*
   - Click on **Next: Workspace** to proceed. 
   
   ![ws name.](media/ex1t2s6c.png)
   
7. In the Workspace section, we need to specify if we need to register the default application group to a workspace. 

   - Register desktop app group: *Choose* **Yes** 
   - To this workspace: *Click on* **Create new**

   ![ws name.](media/67.png)
   
8. Once you click on **Create new**, a small window pops up, where you can specify the Workspace name you are going to create.  

   - Workspace name: **AVD-WS-01** 
   - Click on **OK**
     
   ![ws name.](media/68.png) 

9. Now click on **Review + create** on the bottom left corner. 

   ![ws name.](media/69.png)


10. The last window helps us to verify if the parameters we filled are correct. Wait for validation to pass, then click on **Create** to initiate the deployment. 

    ![ws name.](media/ch4.png)

    > **Note:** The deployment will take about 15 minutes to succeed.

11. Once the deployment is succeeded, open notifications and click on **Go to Resource**.  

    ![ws name.](media/71.png)

    > # **[Optional]**
    >
    > ## Note: In case the previous deployment for Host Pool fails, follow the below steps. Else, continue from step 13:
    >
    >i. Go to the **AVD-RG** resource group and click on **Overview**.
    >
    > ![ws name.](media/w15.png)
    > 
    >ii. Select the resources highlighted in the image below, then click on ellipsis in the top-right corner and click on delete. Make sure you **DO NOT** delete any other resources other than the ones shown in screenshot below.
    >
    > ![ws name.](media/w27.png)
    >
    >iii. Now under *Confirm delete* type **yes** in the bar and click on **Delete**.
    > 
    > ![ws name.](media/w28.png)
    >
    >iv. Once the resources get deleted, then perform Task 1 from Step 1 to Step 11 to create the Host Pool again.
    >
    >v. Now wait for the deployment to succeed. When it gets succeeded, open the notifications and click on **Go to Resource**.  
    >
    > ![ws name.](media/71.png) 

12. You will see that the host pool **AVD-HP-01** is created with two session hosts in it and a default application group (of type Desktop).  

    ![ws name.](media/ex1t2s14.png)

13. Now click on **Session Hosts** present under **Manage** blade. Here you can view the session hosts created. 

    ![ws name.](media/86.png)

14. Click on the **Next** button present in the bottom-right corner of this lab guide.  
