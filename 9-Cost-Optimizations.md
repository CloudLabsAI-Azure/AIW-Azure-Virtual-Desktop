# Lab 8: Cost Optimizations

In this lab, We'll be enabling the Start Virtual Machine (VM) on Connect feature which lets you save costs by allowing users to turn on their VMs only when they need them.

## Exercise 1: Enable Start Virtual Machine on Connect

### Task 1: Create a custom role for Start VM on Connect

1. In your JumpVM launch browser and go to Aure Portal (https://portal.azure.com).

1. Now in the Azure portal search for **Subscription* and click on the search result.

   ![](media/avdv219.png)

1. On the Subscription page, click on the name of your subscription.

   ![](media/avdv220.png)
  
1. Now from the left-hand side blade, Click on **Access Control (IAM)** and then click on **+ Add** and select **Add custom role**.

   ![](media/avdv221.png)

1. On the create a custom role page, Provide **Custom role name** as **start VM on connect** *(1)* and click on **Next** *(2)*.

   ![](media/2avd16.png)

1. Under the Permissions tab, click on **+ Add Permissions**.

   ![](media/avdv223.png)

1. In Add Permissions search for **Virtual Machines** *(1)* and select **Microsoft Compute** from the search results *(2)*.

   ![](media/avdv224.png)

1. From the list of permissions search for **Microsoft.Compute/virtualMachines** then select **Read : Get Virtual MAchine** *(1)* and **Other : Start Virtual Machine** *(2)* and click on **Add** *(3)*.

   ![](media/avdv225.png)
  
1. Now click on **Review + Create** to publish the roles.

   ![](media/avdv226.png)
  
1. Review the configuration and click on **Create**.

   ![](media/2avd110.png)

1. In **Access Control (IAM)** click on **+ Add**  and select **Add role assignment** .
  
   - Under Role, search and select **start VM on connect**, then click on **Next**.

     ![](media/startvm-v2.png)
     
   - Under **Members** tab,enter the below mentioned details:

      - Assign access to: 	**User, group, or service principal (1)**
  
      - Click on **+ Select members (2)**
     
      - Under Select, search for **Windows Virtual desktop and select it **(3)**
      
      - Click on **Select (4)**.

    ![](media/roleass-v2.png)

## Exercise 2: Configure the Start VM on Connect feature

### Task 1: Configuring Host pool Properties

1. In the Azure portal search for **Azure Virtual Desktop** and click on it.

   ![](media/avdv229.png)
  
1. On the left-hand side blade click on **Host pools** *(1)* and select the **host pool** *(2)* we want to configure.

   ![](media/2avd112.png)
  
1. On the left-hand side blade of the Host pool page. Click on **Properties** *(1)*

   ![](media/2avd114.png)
  
   - Toggle Start VM on connect to **Yes** *(2)*.
   - Click on **Save** *(3)*.

## Exercise 3: Experience VM start on connect

### Task 1: Stop the Session host VMs

1. In Azure Portal search for **Virtual Machines** and click on it.

   ![](media/avdv232.png)

1. Select the **session host VMs** *(1)* and click on **Stop** *(2)*.

   ![](media/2avd115.png)
  
1. On a prompt saying "Do you want to stop the selected Virtual Machines" click on **Yes**.

   ![](media/2avd116.png)
  
### Task 2: Access the Session host desktop

1. Return to AVD client application. On the AVD dashboard, click on the tile named **Session Desktop** to launch the desktop.

   ![ws name.](media/ex4t2s2.png)
   
1. A window saying *Connecting to: Session Desktop* will appear. Wait for few seconds, then enter your password to access the Desktop.

   - Password: **<inject key="AzureAdUserPassword" />**
   
   ![ws name.](media/ch14.png)
   
   >**Note:** If there's a dialog box saying ***Help us protect your account***, then select **Skip for now** option.
   
   ![](media/login.png)

1. While the Session Desktop is connecting, we can see a message saying **Starting remote PC**.

   ![ws name.](media/avdv235.png)

1. Your virtual desktop will launch and look similar to the screenshot below. You can exit from the window by clicking on **X *i.e., the close button***. 
        
   ![ws name.](media/ex4t2s5.png)   
     
1. Return to the Azure portal and click on **refresh** *(1)* to get the updated status of Virtual Machines. Here we can see the session hosts VM in the **Running** state and has started automatically when the session desktop was launched.

   ![](media/2avd117.png)
   
1. Click on the Next button present in the bottom-right corner of this lab guide.
  
  
  
