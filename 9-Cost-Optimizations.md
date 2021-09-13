# **Lab 9: Cost Optimizations**

## **Exercise 1: Enable Start Virtual Machine on Connect**

### **Task 1: Create a custom role for Start VM on Connect**

1. In your JumpVM launch browser and go to Aure Portal (https://portal.azure.com).

2. Now in the Azure portal search for **Subscription* and click on the search result.

   ![](media/avdv219.png)

3. On the Subscription page, click on the name of your subscription.

   ![](media/avdv220.png)
  
4. Now from the left-hand side blade, Click on **Access Control (IAM)** and then click on **+ Add** and select **Add custom role**.

   ![](media/avdv221.png)

5. On the create a custom role page, Provide **Custom role name** as **start VM on connect** *(1)* and click on **Next** *(2)*.

   ![](media/2AVD14.png)

6. Under the Permissions tab, click on **+ Add Permissions**.

   ![](media/avdv223.png)

7. In Add Permissions search for **Virtual Machines** *(1)* and select **Microsoft Compute** from the search results *(2)*.

   ![](media/avdv224.png)

8. From the list of permissions search for **Microsoft.Compute/virtualMachines** then select **Read : Get Virtual MAchine** *(1)* and **Other : Start Virtual Machine** *(2)* and click on **Add** *(3)*.

   ![](media/avdv225.png)
  
9. Now click on **Review + Create** to publish the roles.

   ![](media/avdv226.png)
  
6. Review the configuration and click on **Create**.

   ![](media/avdv227.png)

1. In **Access Control (IAM)** click on **+ Add** *(1)* and select **Add role assignment** *(2)*.

   ![](media/avdv228.png)
  
   - Under Role, search and select **start VM on connect** *(3)*.
   - Under Select, search for **Windows Virtual desktop** **(4)** and select it *(5)*
   - Click on **Save** *(6)*.

## Exercise 2: Configure the Start VM on Connect feature

### **Task 1: Configuring Host pool Properties**

1. In the Azure portal search for **Azure Virtual Desktop** and click on it.

   ![](media/avdv229.png)
  
2. On the left-hand side blade click on **Host pools** *(1)* and select the **host pool** *(2)* we want to configure.

   ![](media/avdv230.png)
  
3. On the left-hand side blade of the Host pool page. Click on **Properties** *(1)*

   ![](media/avdv231.png)
  
   - Toggle Start VM on connect to **Yes** *(2)*.
   - Click on **Save** *(3)*.

## **Exercise 2: Experience VM start on connect**

### **Task 1: Stop the Session host VMs**

1. In Azure Portal search for **Virtual Machines** and click on it.

   ![](media/avdv232.png)

2. Select the **session host VMs** *(1)* and click on **Stop** *(2)*.

   ![](media/avdv233.png)
  
3. On a prompt saying "Do you want to stop the selected Virtual Machines" click on **Yes**.

   ![](media/avdv234.png)
  
### Task 2: Access the Session host desktop

1. Return to WVD client application. On the AVD dashboard, click on the tile named **Session Desktop** to launch the desktop.

   ![ws name.](media/ex4t2s2.png)
   
2. A window saying *Connecting to: Session Desktop* will appear. Wait for few seconds, then enter your password to access the Desktop.

   - Password: **<inject key="AzureAdUserPassword" />**
   
   ![ws name.](media/ch14.png)
   
   >**Note:** If there's a dialog box saying ***Help us protect your account***, then select **Skip for now** option.
   
   ![](media/login.png)

3. While the Session Desktop is connecting, we can see a message saying **Starting remote PC**.

   ![ws name.](media/avdv235.png)

4. Your virtual desktop will launch and look similar to the screenshot below. You can exit from the window by clicking on **X *i.e., the close button***. 
        
   ![ws name.](media/ex4t2s5.png)   
     
5. Return to the Azure portal and click on **refresh** *(1)* to get the updated status of Virtual Machines. Here we can see the session hosts VM in the **Running** state and has started automatically when the session desktop was launched.

   ![](media/avdv236.png)
  
  
  
