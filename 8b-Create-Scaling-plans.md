
# Lab 8b: Create Scaling plans


### Overview

 Azure Virtual Desktop uses Autoscale which let's scale your session virtual machines (VMs) in a host pool up or down to optimize deployment costs. You can create a scaling plan based on:

   - Time of day
   - Specific days of the week
   - Session limits per session host


## Exercise 1: Create a Scaling Plan


1. From the Azure Portal menu, search for **Azure Virtual Desktop** and select it.

    ![](../Azure-Virtual-Desktop-v3/media/AVD.png)
   
2. On the **Azure Virtual Desktop** page, click on **Scaling plans (1)** under *Manage* blade and select **Create a scaling plan (2)**.

    ![](../Azure-Virtual-Desktop-v3/media/scaling%20plans.png)
   
3. On the **Basics** tab of **Create a scaling plan** page, enter the below instructions:

    - Subscription : Select your **Subscription (1)** from frop-down list
    - Resource group : Select **AVD-HostPool-RG-avd (2)**
    - Name:Enter **AVD-SP-01 (3)**
    - Location : Select the location same as the Resource group **(4)**
    - Friendly name: Enter **AVD-SP-01 (5)**
    - Time zone : Select your **Time Zone (6)**
    - Click on **Next : Schedules > (7)**

    ![](../Azure-Virtual-Desktop-v3/media/sp-basics.png)

4. On **Schedules** tab, click on **Add Schedule**

    ![](../Azure-Virtual-Desktop-v3/media/add%20schedule.png)
   
5. On the **General** tab of **Add a schedule** page, observe the vaules and leave everything as default, then click on **Next**.

    ![](../Azure-Virtual-Desktop-v3/media/general%20schedule.png)
   
6. On the **Ramp-up** tab, observe the vaules and leave everything as default then click on **Next**.

    ![](../Azure-Virtual-Desktop-v3/media/ramp-up.png)
   
7. On the **Peak hours** tab, observe the vaules and leave everything as default then click on **Next**.

    ![](../Azure-Virtual-Desktop-v3/media/peakhours.png)
   
8. On the **Ramp-down** tab, observe the vaules and leave everything as default then click on **Next**.

    ![](../Azure-Virtual-Desktop-v3/media/rampdown.png)
   
9. On the **Off-peak hours** tab, observe the vaules and leave everything as default then click on **Add**.

    ![](../Azure-Virtual-Desktop-v3/media/offpeakhours.png)
  
10. After adding the schedule,click on **Next: Host pool assignments >**

     ![](../Azure-Virtual-Desktop-v3/media/nextHPS.png)
    
11. On **Host pool assignments** tab, select **EB-AVD-HP** from the drop-down and click on **Review + create**.

     ![](../Azure-Virtual-Desktop-v3/media/review%2Bcrete.png)
     
12. Review the changes and click on **Create**.

     ![](../Azure-Virtual-Desktop-v3/media/crearesp.png)
     
13. After the  successful deployment, click on **Go to resource**.

     ![](../Azure-Virtual-Desktop-v3/media/gotoresourcee.png)
    


