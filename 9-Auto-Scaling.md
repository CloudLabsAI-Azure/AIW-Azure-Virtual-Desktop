
# Lab 9: Auto Scaling


### Overview

 Azure Virtual Desktop uses Autoscale which let's scale your session virtual machines (VMs) in a host pool up or down to optimize deployment costs. You can create a scaling plan based on:

   - Time of day
   - Specific days of the week
   - Session limits per session host


## Exercise 1: Create a Scaling Plan

1. From the Azure Portal menu, search for **Subscription** and select it

    ![](../Azure-Virtual-Desktop-v3/media/subscriptions.png)
    
2. Select your **Subscription** from **Subscriptions** page.

   ![](../Azure-Virtual-Desktop-v3/media/sybname.png)

3. Now select **Access Control (1)** and click on **Add (2)** then select **Add role assignment (3)**.

   ![](../Azure-Virtual-Desktop-v3/media/IAM.png)
   
4. On **Add Role Assignemnt** page, search for **Azure Virtual Desktop Autoscale** and select it, then click on **Next**.

   ![](../Azure-Virtual-Desktop-v3/media/AVDrole.png)
   
5. Under **Members** tab, click on **+ Select members**.

   ![](../Azure-Virtual-Desktop-v3/media/selectmem.png)
   
6. On **Select members** tab, search for **Windows Virtual Desktop** and select it then click on **Select**.

    ![](../Azure-Virtual-Desktop-v3/media/searchmem.png)
    
7. After adding members, review the configuration and click on **Review + assign**.

   ![](../Azure-Virtual-Desktop-v3/media/review%2Bassign.png)

4. From the Azure Portal menu, search for **Azure Virtual Desktop** and select it.

    ![](../Azure-Virtual-Desktop-v3/media/avd2.png)
   
2. On the **Azure Virtual Desktop** page, click on **Scaling plans (1)** under *Manage* blade and select **Create a scaling plan (2)**.

    ![](../Azure-Virtual-Desktop-v3/media/csp.png)
   
3. On the **Basics** tab of **Create a scaling plan** page, enter the below instructions:

    - Subscription : Select your ***Subscription (1)*** from frop-down list
    - Resource group : Select ***AVD-HostPool-RG-avd (2)***
    - Name:Enter ***AVD-SP-01 (3)***
    - Location : Select the location same as the Resource group ***(4)***
    - Friendly name: Enter ***AVD-SP-01 (5)***
    - Time zone : Select your ***Time Zone (6)***
    - Click on ***Next : Schedules > (7)***

    ![](../Azure-Virtual-Desktop-v3/media/schedulee.png)

4. On **Schedules** tab, click on **+ Add Schedule**

    ![](../Azure-Virtual-Desktop-v3/media/addschedule1.png)
   
5. On the **General** tab of **Add a schedule** page, observe the vaules and leave everything as default, then click on **Next**.

    ![](../Azure-Virtual-Desktop-v3/media/general1.png)
   
6. On the **Ramp-up** tab, follow the below instructions:

    - Start time (24 hour system) : Enter your ***Start time (1)***
    - Load Balancing Algorithm : Choose ***Breadth-first (2)***
    - Minimum percentage of hosts (%) : ***20 (3)***
    - Capacity threshold (%) : ***60 (4)***
    - Click on ***Next (5)***
    
    ![](../Azure-Virtual-Desktop-v3/media/rmap.png)
   
7. On the **Peak hours** tab, follow the below instructions:

    - Start time (24 hour system) : Enter your ***Start time (1)***
    - Load Balancing Algorithm : Choose ***Depth-first (2)***
    - Click on ***Next (3)***
    
    ![](../Azure-Virtual-Desktop-v3/media/peakhours1.png)
   
8. On the **Ramp-down** tab, follow the below instructions:

     - Start time (24 hour system) : Enter your ***Start time (1)***
     - Load Balancing Algorithm : Choose ***Depth-first (2)***
     - Minimum percentage of hosts (%) : Enter ***10 (3)***
     - Capacity threshold (%) : ***90 (4)***
     - Force logoff users : Choose ***Yes (5)***
     - Delay time before logging out users and shutting down VMs (min) : Enter ***30 (6)***
     - Click on ***Next (7)***

     ![](../Azure-Virtual-Desktop-v3/media/rampdown1.png)
   
9. On the **Off-peak hours** tab, follow the below instructions:

     - Start time (24 hour system) : Enter your ***Start time (1)***
     - Load Balancing Algorithm : Choose ***Depth-first (2)***
     - Click on ***Add (3)***

     ![](../Azure-Virtual-Desktop-v3/media/offpeakhours1.png)
  
10. After adding the schedule,click on **Next: Host pool assignments >**

     ![](../Azure-Virtual-Desktop-v3/media/hpa1.png)
    
11. On **Host pool assignments** tab, select **EB-AVD-HP (1)** from the drop-down and click on **Review + create (2)**.

     ![](../Azure-Virtual-Desktop-v3/media/rc.png)
     
12. Review the changes and click on **Create**.

     ![](../Azure-Virtual-Desktop-v3/media/spcreate.png)
     
13. After the  successful deployment, click on **Go to resource**.

     ![](../Azure-Virtual-Desktop-v3/media/GTR.png)
 
 14. Now you will navigate to the **Overview** page of the Scaling Plan **AVD-SP-01**.

     ![](../Azure-Virtual-Desktop-v3/media/overviewsp.png)


