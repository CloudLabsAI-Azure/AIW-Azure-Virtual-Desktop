
> **Note:** This section doesn’t cover the Azure Monitor for Azure Virtual Desktop announcement from today. 

Azure Virtual Desktop uses Azure Monitor for monitoring and alerts like many other Azure services. This lets admins identify issues through a single interface. The service creates activity logs for both user and administrative actions.


### **Task 1: Create Log Analytics**

1. On the Azure portal, click on **Create a resource** given under *Azure services*.

   ![ws name.](media/wiw.png)

2. Type *Log Analytics Workspace* in the search bar and click on **Log Analytics Workspace** from the suggestions.

   ![ws name.](media/wiw1.png)

3. On the Log Analytics Workspace page, click on **Create**.

   ![ws name.](media/wiw2.png)

4. Now add the following configurations:

   - Subscription: *Choose the default subscription.*
  
   - Resource group: *Select **AVD-RG** from the drop down.*
  
   - Name: **<inject key="Log Analytics Workspace Name	" />**
  
   - Region: **East US**, *basically this should be same as the region of your resource group.*
  
   - Click on **Review + Create**

   ![ws name.](media/wiw3.png)

5. The last window helps us to verify if the parameters we filled are correct. Wait for validation to pass, then click on **Create** to initiate the deployment.

   ![ws name.](media/wiw18.png)

6. Once the deployment gets succeeded, it will look similar to the image shown below.

   ![ws name.](media/lb60.png)
   
   ### **Task 2: Enable diagnostics for Workspace**
 
1. Navigate back to Azure Virtual Desktop and open **Workspaces**.

   ![ws name.](media/wiw9.png)
   
2. Click on **AVD-WS-01**. Then select **Diagnostic settings** present under *Monitoring* blade and click on **+Add diagnostic setting**.    
   
   ![ws name.](media/wiw11.png)
 
3. Add the following configurations:

   - Diagnostic settings name: **WorkspaceMonitoring**
   - Category details: *Check all the boxes present under logs i.e.,* **Checkpoint, Error, Management and Feed.** 
   - Destination details: *Check the box for* **Send to Log Analytics**
   - Subscription: *Choose the default subscription.*
   - Log Analytics Workspace: *Select the log analytics workpsace from the drop down, that we just created.*
   - At last, click on **Save**.  
   
   ![ws name.](media/wiw13.png)

4. Once saved, it will look similar to the image shown below.

   ![ws name.](media/lb64.png)
