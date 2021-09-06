
# Monitoring using Log Analytics

Azure Virtual Desktop uses Azure Monitor for monitoring and alerts like many other Azure services. This lets admins identify issues through a single interface. The service creates activity logs for both user and administrative actions.

### **Task 1: Create Log Analytics**

1. On the Azure portal, click on **Create a resource** given under *Azure services*.

   ![ws name.](media/wiw.png)

1. Type *Log Analytics Workspace* in the search bar and click on **Log Analytics Workspace** from the suggestions.

   ![ws name.](media/wiw1.png)

1. On the Log Analytics Workspace page, click on **Create**.

   ![ws name.](media/wiw2.png)

1. Now add the following configurations:

   - Subscription: *Choose the default subscription.*
  
   - Resource group: *Select **AVD-RG** from the drop down.*
  
   - Name: **<inject key="Log Analytics Workspace Name	" />**
  
   - Region: **East US**, *basically this should be same as the region of your resource group.*
  
   - Click on **Review + Create**

   ![ws name.](media/wiw3.png)

1. The last window helps us to verify if the parameters we filled are correct. Wait for validation to pass, then click on **Create** to initiate the deployment.

   ![ws name.](media/wiw18.png)

1. Once the deployment gets succeeded, it will look similar to the image shown below.

   ![ws name.](media/lb60.png)
   
   ### **Task 2: Enable diagnostics for Workspace**
 
 1. 
