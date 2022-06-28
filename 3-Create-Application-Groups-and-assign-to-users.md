# Lab 3: Create Application Groups and assign them to users

## **Scenario**

Contoso wants to restrict the access to the applications used by different teams in the organization. With Azure Virtual Desktop, admins can create unique application groups for users that require access to a specific set of applications. In this lab you’ll help Contoso to configure and create an application group and add applications to it.

## **Overview**

As explained in the General Hierarchy section, an Application Group is a logical grouping of applications installed on session hosts in the host pool. There are two types of application groups: 

1. RemoteApp 
2. Desktop 

### Exercise 1: Create Application Group

An application group of type ‘Desktop’, was created automatically while creating the Session Host in the previous exercise. In this task, we will create a new application group of type ‘*RemoteApp*’ and publish two applications in it. Also, we will assign users to both the application groups.

1. Navigate to the Azure portal,  and search for Azure Virtual Desktop in the search bar and select **Azure Virtual Desktop** from the search results.
   ![ws name.](media/w1.png)

2. You will be directed towards the **Azure Virtual Desktop** management window.  

   ![ws name.](media/64.png)

3. Click on the **Application Groups** tab and you will see the default Application Group there. 

   ![ws name.](media/2avd81.png)
   
4. Click on the **EB-AVD-HP-DAG** application group.

   ![ws name.](media/2avd82.png)
      
5. Under **Manage** blade, open **Assignments (1)** and then click on **+ Add (2)**. 

   ![ws name.](media/avd-assignments-add.png)   
 
6. Now in the search bar, copy and paste your username **<inject key="AzureAdUserEmail" /> (1)**. Then under the search bar **(2)**, click on your username to select it.

   ![ws name.](media/w7.png)
   
7. At last, click on the **Select** button. 
 
   ![ws name.](media/w6.png) 
 
8. We will now create a new Application Group of type ‘RemoteApp’. To do this, navigate back to the **Application groups** and click on the **+ Create** button. 

   ![ws name.](media/2avd84.png)

9. In the *Basics* tab, do the following configuration: 

   i. Leave the following parameters to default:
   
      - *Subscription*
      - *Location*
         
   ii. Fill in the remaining parameters below:  
   
      - Resource Group: *Select* **AVD-Hostpool-RG-avd** *from the dropdown*.
      - Host Pool: *Select* **EB-AVD-HP** *Host pool from the dropdown*.
      - Application Group Type: **RemoteApp** 
      - Application Group Name: **AVD-AG-01**
      - Click on **Next: Applications >**

      ![ws name.](media/gsu4.png)

10. On the *Applications* tab, click on **Add Applications** to add applications to this application group.

    ![ws name.](media/ag1.png)

11. In this window, choose the parameters mentioned below: 

    - Application Source: **Start Menu** *(choose from the dropdown)*  
    - Application: **Excel** *(choose from the dropdown)* 
    - Display Name: **Excel**
    - Leave the rest of the parameters as default and click on **Save**.
   
    ![ws name.](media/2avd29.png)
 
12. Click on **Add Applications** again. 

    ![ws name.](media/ag2.png)

13. Choose the parameters as mentioned below: 

    - Application Source: **Start Menu** *(choose from the dropdown)*   
    - Application: **Word** *(choose from the dropdown)*
    - Display Name: **Word**    
    - Leave rest of the parameters to default and click on **Save**.  
   
    ![ws name.](media/2avd30.png)

14. Click on **Next: Assignments >**.

    ![ws name.](media/ag3.png)

15. Click on the **+Add Azure AD users or user groups (1)**, then copy and paste your username **<inject key="AzureAdUserEmail" />** **(2)** in the search bar. When your username appears under the search bar, select it, and then click on the **Select (3)** button. This will give you access to the application group.
 
    ![ws name.](media/ag5.png)

16. Click on **Next: Workspace >**.

    ![ws name.](media/ag6.png)

17. On the *Workspace* tab, choose the parameters as mentioned below:  

    - Register Application Group: **Yes**
    - Register Application Group: Leave the value to default

    ![ws name.](media/gsu3.png)

18. Click on **Review + Create**.

    ![ws name.](media/review.png)

19. The last window helps us to verify if the parameters we filled in are correct. Wait for validation to pass, then click on **Create** to initiate the deployment. 

    ![ws name.](media/create%20AG-V2.png)

    >**Note:** The deployment will take about a minute to succeed.

20. Once the deployment is complete, open notifications and click on **Go to Resource**. 

    ![ws name.](media/81.png)

21. In the Application Group Window, click on **Applications** under the **Manage** section of settings and you will see that the applications are published in the new application Group. 

    ![ws name.](media/uiupdate04.png)

22. Click on the **Next** button present in the bottom-right corner of this lab guide. 
