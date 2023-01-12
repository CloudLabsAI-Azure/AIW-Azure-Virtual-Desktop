# Lab 13: App Masking (Optional)


### Overview

Application Masking is used to manage user access to installed components. Application Masking may be used in both physical and virtual environments. Application Masking is most often applied to manage non-persistent, virtual environments, such as Virtual Desktops.

##  Exercise 1: App Masking (Read-Only)

In this exercise, you will creating the rule set in **FSLogix Apps RuleEditor** to disable the access to the application in the session hosts.


1. In your JumpVM,  go to Start and search for **FSLogix Apps RuleEditor** and open the FSLogix Apps RuleEditor application from the search results

    ![](../Azure-Virtual-Desktop-v3/media/selectRE.png)
    
2. On the FSLogix Apps RuleEditor application, click on **New**.

    ![](../Azure-Virtual-Desktop-v3/media/new.png)

3. Provide a name for the Rule Set as **hidechrome (1)** and click on **Enter file name (2)**.

    ![](media-1/hidechrome.png)

4. On the **Rule Set : hidechrome** window, follow the below instructions:

    - Select ***Choose from installed programs (1)***
    - Select on ***Google Chrome (2)***
    -  Click on ***Scan (3)***

      ![](media-1/scan.png)


5. After Scan completes successfully, click on ***Ok***.

     ![](media-1/clickok.png)
    
     
6. Now you have created the hiding rules to hide the PowerShell application. Click on **Apply Rules to System** to apply the created rule in your JumpVM.

     ![](media-1/applyrule.png)
     
7. Now in your JumpVM,  go to Start and search for **Chrome (1)** and double click on **Google Chrome (2)** to open the application. Here you will not be able to open the app due to the hiding rule applied to your VM. 

     ![](media-1/googlechrome.png)
     
    **Note:** In the same way, you can apply the hiding rule to the session desktop in the remote desktop from your JumpVM.
    
8. Navigate back to FSLogix App Rule Editor and click on **Manage Assignments**.

    ![](media-1/manageassig.png)
    
9. On the Assignments tab, click on **Add**.

    ![](../Azure-Virtual-Desktop-v3/media/add.png)
    
10. Click on **User**.

    ![](../Azure-Virtual-Desktop-v3/media/user.png)
    
11. On the **Select User** dialog box, follow the below instructions:

    - **User** : Paste the username  **<inject key="Avd User 01" /> (1)**
    - Click on **Ok (2)**

    ![](../Azure-Virtual-Desktop-v3/media/adduser.png)
    
12. After adding the User, click on **Apply (1)** and **Ok (2)**.

    ![](../Azure-Virtual-Desktop-v3/media/applyandadd.png)
    
13. Now you have added the User to the same hiding rules to hide the PowerShell application. Click on **Apply Rules to System** to apply the created rule in your Session host on the Remote desktop.

     ![](media-1/applyrule.png)
     
