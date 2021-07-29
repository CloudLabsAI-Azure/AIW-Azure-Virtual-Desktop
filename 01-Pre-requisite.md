# **Pre-requisites for this Azure Virtual Desktop workshop**

## **Task 1: Configure Lab environment (VM)**

In this task, you will setup the Lab environment respective to your region

1. Default Browser - Make sure Edge is the default browser by navigating to Start>Settings>Default Apps as shown below

   ![Find Default Apps](media/DefaultApps.png "Find Default Apps")

   ![Edge as default browser](media/Edge-DefaultBrowser.png "Set Edge as Default Browser")

1. Within settings, set the Region and Language to the required setting as shown below

   ![Change Region](media/RegionChange.png "set Region")

   ![Change Language](media/LanguageChange.png "Set Language")

## **Task 2: Log in to Azure Portal**

1. In the JumpVM, double click on the **Azure portal shortcut** on the desktop.

   ![azure portal.](media/labinst15.png)  

2. Login to Azure with the username **<inject key="AzureAdUserEmail" />** and click on **Next**.

   ![](media/w24.png)

3. Enter password **<inject key="AzureAdUserPassword" />** and click on **Sign in**.

   ![](media/w25.png)

    > **Note:** If there's a popup entitled **Stay signed in?** with buttons for **No** and **Yes** - Choose **No**.
    >
    >    ![](media/w26.png)
    >   
    > **Note:** If there's another popup entitled **Welcome to Microsoft Azure** with buttons for **Start Tour** and **Maybe Later** - Choose **Maybe Later**.
    >
    >    ![](media/wvd4.png) 

4. Now in the Azure portal, click on **Resource Groups** present under *Navigate*.

   ![](media/jvm3.png)

5. You will see a list of resource groups as show in the image below. Click on **AVD-RG** to open it.

   ![](media/jvm4.png)

> **Note:** You will be using ***AVD-RG*** throughout the lab. Other two resource groups listed in the portal are not to be used in the lab.

## **Task 3: Create Log Analytics**

1. On the Azure portal, click on **Create a resource** given under *Azure services*.

   ![ws name.](media/wiw.png)

2. Type *Log Analytics Workspace* in the search bar and click on **Log Analytics Workspace** from the suggestions.

   ![ws name.](media/wiw1.png)

3. On the Log Analytics Workspace page, click on **Create**.

   ![ws name.](media/wiw2.png)

4. Now add the following configurations:

  - Subscription: *Choose the default subscription.*
  - Resource group: *Select **AVD-RG** from the drop down.*
  - Name: *Go to Lab Environment tab, copy the* **Log Analytics Workspace Name** *and paste it here in Name box.*
  
   ![ws name.](media/up12.png)

  - Region: **(region)**, *basically this should be same as the region of your resource group.for e.g. East US*
  - Click on **Review + Create**

   ![ws name.](media/wiw3.png)

5. The last window helps us to verify if the parameters we filled are correct. Wait for validation to pass, then click on **Create** to initiate the deployment.

   ![ws name.](media/wiw18.png)

6. Once the deployment gets succeeded, it will look similar to the image shown below.

   ![ws name.](media/lb60.png)

## **Task 4: Azure Active Directory Domain Services (AADDS)**

- To deploy Azure Virtual Desktop environment, we need a Windows Active Directory (for example: contoso.com). This can be achieved using one of the following ways:

    1. Azure Active Directory Domain Services(AADDS)
    2. Windows Active Directory

- In this lab, we have used AADDS and it is pre-provisioned. 

  ![ws name.](media/w30.png)

- The domain name will be the suffix of your lab user account (for example: If your lab user account is ***odl_user_189588@azurehol1057.onmicrosoft.com***, the domain will be ***azurehol1057.onmicrosoft.com***.)

- When you provision Azure ADDS, it creates a group named "AAD DC Administrators" in Azure Active Directory. Members of this group are allowed to be able to join AVD Sessions Hosts to Azure ADDS.  Your lab account is already a member of this group. 


Click on the **Next** button present in the bottom-right corner of this lab guide.  
