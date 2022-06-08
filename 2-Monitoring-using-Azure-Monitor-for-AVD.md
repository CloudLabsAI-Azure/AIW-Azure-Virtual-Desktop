# Lab 2(A) : Monitoring using Log Analytics


## **Scenario**

Contoso is interested in setting up an operation center focused on monitoring the host pools, user access, and many more. You will help Contoso to set up a  monitoring solution with the help of features available in Azure virtual desktop and Azure monitoring resource. You will create a Log analytics workspace and map it to the AVD environment using Azure Insights.

## **Overview**

Azure Virtual Desktop uses Azure Monitor for monitoring and alerts like many other Azure services. This lets admins identify issues through a single interface. The service creates activity logs for both user and administrative actions.

## Exercise 1: Create Log Analytics

1. On the Azure portal, click on **Create a resource** given under *Azure services*.

   ![ws name.](media/wiw.png)

1. Type *Log Analytics Workspace* in the search bar and click on **Log Analytics Workspace** from the suggestions.

   ![ws name.](media/wiw1.png)

1. On the Log Analytics Workspace page, click on **Create**.

   ![ws name.](media/wiw2.png)

1. Now add the following configurations:

   - Subscription: Leave it to ***default***
  
   - Resource group: *Select **AVD-Hostpool-RG-avd** from the drop down.*
  
   - Name: **<inject key="Log Analytics Workspace Name	" />**
  
   - Region: Select **<inject key="Region" />** from the drop-down list
  
   - Click on **Review + Create**

   ![ws name.](media/LAW-V2.png)

1. The last window helps us to verify if the parameters we filled are correct. Wait for validation to pass, then click on **Create** to initiate the deployment.

   ![ws name.](media/Create%20LAW-V2.png)

1. Once the deployment gets succeeded, it will look similar to the image shown below.

   ![ws name.](media/lb60.png)
   

## Exercise 2: Enable diagnostics for Workspace
 
1. On **Azure portal** search for **Azure Virtual Desktop (1)** in the search bar and select **Azure Virtual Desktop** **(2)** from the suggestions.

   ![ws name.](media/avd1.png) 

1. You will get directed towards the Azure Virtual Desktop (hereafter referred to as AVD) management window. Select **Insights** under **Monitoring** blade.

   ![ws name.](media/mon2.png)
   
1. On the **Insights** page, Select the following values and click on **Open Configuration Workbook**.
   
   - Subscription: **Choose the default subscription**.
   - Resource group: **avd-hotpool-rg-avd**.
   - Host Pool: **EB-AVD-HP**
   - Time range: **Leave it to default**.

   ![ws name.](media/2avd21.png)

1. In the **Check Configuration** page, Select the **<inject key="Log Analytics Workspace Name" enableCopy="false" /> (1)** workspace from the drop-down Under **Resource diagnostic settings** and Click on **Configure host pool (2)**.

   ![ws name.](media/mon4.png)
   
1. On the **Deploy template** page, The diagnostic settings for the host pool are automated using a template. Look through the categories select and click on **deploy**.

   ![ws name.](media/mon5.png)
   
1. Once the deployment is successful, **Refresh** the **Check Configuration** page. You'll be able to see the settings applied to the host pool.

   ![ws name.](media/2avd22.png)
   
1. Scroll down on the same page and click on **Configure workspace**.

   ![ws name.](media/mon7.png)
   
1. On the **Deploy template** page, The diagnostic settings for the workspace are automated using a template. Look through the categories select and click on **deploy**.

   ![ws name.](media/mon8.png) 

1. Once the deployment is successful, **Refresh** the **Check Configuration** page. You'll be able to see the settings applied to the workspace.

   ![ws name.](media/2avd22.png)
   
1. On **Check Configuration** page, Select **Session host data settings (1)**. Select the **<inject key="Log Analytics Workspace Name	" /> (2)** analytics workspace.

   ![ws name.](media/gsu2.png)
   
1. On Check Configuration page click on **Add hosts to workspace** in **Session hosts** window.

   ![ws name.](media/monu1.png)
   
1. On the **Deploy template** page, The required session hosts configuration will be added to the Log Analytics workspace. Click on **Deploy**.

   ![ws name.](media/monu2.png)
   
1. On the **Check Configuration** page click on **configure performance counters** in the **performance counter** window.

   ![ws name.](media/mon14-new.png)
   
1. On the **Deploy template** page, The required performance counters will be added to the Log Analytics workspace. Click on **Apply Config**

   ![ws name.](media/mon15.png)
   
1. Once the deployment is successful, **Refresh** the **Check Configuration** page. You'll see that all the performance counters will be configured.

   ![ws name.](media/2avd24.png)
   
1. On the same **Check Configuration** page, scroll down and click on **Configure events** in **Windows event logs** window.

   ![ws name.](media/mon17.png)
   
1. On the **Deploy template** page, The required events will be added to the Log Analytics workspace. Click on **Deploy**.

   ![ws name.](media/mon18.png)
   
1. Once the deployment is completed, **Refresh** the **Check Configuration** page. You'll see that all the required events will be configured.
   
   ![ws name.](media/mon19.png)
   
1. Click on the **Next** button present in the bottom-right corner of this lab guide.

 
