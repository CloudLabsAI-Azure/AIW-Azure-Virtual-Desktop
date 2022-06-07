
# Lab 8: Auto Scaling


### Overview

 Azure Virtual Desktop uses Autoscale which let's scale your session virtual machines (VMs) in a host pool up or down to optimize deployment costs. You can create a scaling plan based on:

   - Time of day
   - Specific days of the week
   - Session limits per session host


## Exercise 1: Create a Scaling Plan

1. In the Azure Portal, search for **Subscriptions** and select it from the search result.

    ![](../Azure-Virtual-Desktop-v3/media/subscriptions.png)
    
2. Select your **Subscription** from **Subscriptions** page.

   ![](../Azure-Virtual-Desktop-v3/media/sybname.png)
   
3. Now select **Access Control (IAM) (1)** and click on **+ Add (2)** then select **Add custom role (3)**.

    ![](../Azure-Virtual-Desktop-v3/media/customrole1.png)
    
4. On the **Basics** tab, follow the below instrucions:

    - Custom role name :  Enter **Azure Virtual Desktop Autoscale (1)**
    - Baseline permissions : Select **Start from JSON (2)**
    - Click on **Folder icon (3)** to select the JSON file.

     ![](../Azure-Virtual-Desktop-v3/media/basicsCR.png)
     
5. Navigate to the path **C:\LabFiles**, right click on **AzureVirtualDesktopAutoscale.json (1)** and click on **Open with (2)**.

    ![](../Azure-Virtual-Desktop-v3/media/openwith.png)
    
 6. If you get a pop-out stating **Windows can't open this type of file**, click on **Try an app on this PC**.

    ![](../Azure-Virtual-Desktop-v3/media/tryanotherapp.png)
    
7. Choose **Notepad (1)** from the list and click on **OK (2)**.

    ![](../Azure-Virtual-Desktop-v3/media/notepad.png)
    
8. In the JSON file, replace the subscription ID with and save the changes.

    ![](../Azure-Virtual-Desktop-v3/media/subid.png)
    
9. After saving the changes, close the file and click on **Open** on the File Explorer.

    ![](../Azure-Virtual-Desktop-v3/media/open.png)
    
10. On the **Basics** tab, click on **Next**.

    ![](../Azure-Virtual-Desktop-v3/media/nextbasics.png)
    
11. On **Permissions**, review the permissions you have assigned using JSON file and click on **Review + create**.

     ![](../Azure-Virtual-Desktop-v3/media/permissionsreview.png)
     
12. Review the changes and click on **Create**.

    ![](../Azure-Virtual-Desktop-v3/media/createCR.png)

3. Now select **Access Control (IAM) (1)** and click on **+ Add (2)** then select **Add role assignment (3)**.

   ![](../Azure-Virtual-Desktop-v3/media/IAM.png)
   
4. On **Add Role Assignment** page, search for **Azure Virtual Desktop Autoscale** and select it, then click on **Next**.

   ![](../Azure-Virtual-Desktop-v3/media/AVDrole.png)
   
   >**Note :** If you don't find the role, wait for 2-3 min and re-perform the above step.
   
5. Under **Members** tab, click on **+ Select members**.

   ![](../Azure-Virtual-Desktop-v3/media/selectmem.png)
   
6. On **Select members** tab, search for **Windows Virtual Desktop** and select it then click on **Select**.

    ![](../Azure-Virtual-Desktop-v3/media/WVD.png)
    
7. After adding members, review the configuration and click on **Review + assign**.

   ![](../Azure-Virtual-Desktop-v3/media/review%2Bassign.png)

4. From the Azure Portal menu, search for **Azure Virtual Desktop** and select it.

    ![](../Azure-Virtual-Desktop-v3/media/avd2.png)
   
2. On the **Azure Virtual Desktop** page, click on **Scaling plans (1)** under *Manage* blade and select **Create a scaling plan (2)**.

    ![](../Azure-Virtual-Desktop-v3/media/csp.png)
   
3. On the **Basics** tab of **Create a scaling plan** page, enter the below instructions:

    - Subscription : Leave it to **default (1)**
    - Resource group : Select **AVD-HostPool-RG-avd (2)**
    - Name:Enter **AVD-SP-01 (3)**
    - Location : Select **<inject key="Region" />** from the drop-down list **(4)**
    - Friendly name: Enter **AVD-SP-01 (5)**
    - Time zone : Select your **Time Zone (6)**
    - Click on **Next : Schedules > (7)**

    ![](../Azure-Virtual-Desktop-v3/media/schedulee.png)

4. On the **Schedules** tab, click on **+ Add Schedule**

    ![](../Azure-Virtual-Desktop-v3/media/addschedule1.png)
   
5. On the **General** tab of **Add a schedule** page, observe the values and leave everything as default, then click on **Next**.

    ![](../Azure-Virtual-Desktop-v3/media/general1.png)
   
6. On the **Ramp-up** tab, follow the below instructions:

    - Start time (24 hour system) : Enter your **Start time (1)**
    - Load Balancing Algorithm : Choose **Breadth-first (2)**
    - Minimum percentage of hosts (%) : **20 (3)**
    - Capacity threshold (%) : **60 (4)**
    - Click on **Next (5)**
    
    ![](../Azure-Virtual-Desktop-v3/media/rmap.png)
   
7. On the **Peak hours** tab, follow the below instructions:

    - Start time (24 hour system) : Enter your **Start time (1)**
    - Load Balancing Algorithm : Choose **Depth-first (2)**
    - Click on **Next (3)**
    
    ![](../Azure-Virtual-Desktop-v3/media/peakhours1.png)
   
8. On the **Ramp-down** tab, follow the below instructions:

     - Start time (24 hour system) : Enter your **Start time (1)**
     - Load Balancing Algorithm : Choose **Depth-first (2)**
     - Minimum percentage of hosts (%) : Enter **10 (3)**
     - Capacity threshold (%) : **90 (4)**
     - Force logoff users : Choose **Yes (5)**
     - Delay time before logging out users and shutting down VMs (min) : Enter **30 (6)**
     - Click on **Next (7)**

     ![](../Azure-Virtual-Desktop-v3/media/rampdown1.png)
   
9. On the **Off-peak hours** tab, follow the below instructions:

     - Start time (24 hour system) : Enter your **Start time (1)**
     - Load Balancing Algorithm : Choose **Depth-first (2)**
     - Click on **Add (3)**

     ![](../Azure-Virtual-Desktop-v3/media/offpeakhours1.png)
  
10. After adding the schedule, click on **Next: Host pool assignments >**

     ![](../Azure-Virtual-Desktop-v3/media/hpa1.png)
    
11. On **Host pool assignments** tab, select **EB-AVD-HP (1)** from the drop-down and click on **Review + create (2)**.

     ![](../Azure-Virtual-Desktop-v3/media/rc.png)
     
12. Review the changes and click on **Create**.

     ![](../Azure-Virtual-Desktop-v3/media/spcreate.png)
     
13. After the successful deployment, click on **Go to resource**.

     ![](../Azure-Virtual-Desktop-v3/media/GTR.png)
 
 14. Now you will navigate to the **Overview** page of the Scaling Plan **AVD-SP-01**.

     ![](../Azure-Virtual-Desktop-v3/media/overviewsp.png)


