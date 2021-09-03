# MSIX App Attach(Optional)

1. Search for **Stoarage accounts** in the search bar and select the **<inject key="Storage Account Name" />** account which was created in **Exercise 5: Setup FSLogix**.
1. 11. In the right pane, click on **File shares** present under *Data Storage* blade.

    ![ws name.](media/uiupdate10.png)
 
1. Enter the following name for your file share.
    
    - Name: **msixfile**   
    - Tier: **Transaction Optimized**
    - Click on **Create**, this will create the file share.
    
    ![ws name.](media/msix1.png)
    
1. Go to **msixfile** file share and select **upload**.

   ![ws name.](media/msix2.png)
   
   ![ws name.](media/msix3.png)
   
1. Browse the files go to ``C:\LabFiles``. Select **7-Zip.vhd**, **msix.cer** files and Click on **Open**.

   ![ws name.](media/msix4.png)
   
1. Select **Access Control(IAM)** from the side blade. Click on **Add** and select **Add Role Assignment**.

   ![ws name.](media/msix5.png)
   
1. Select the following options and click **Save**

   -Role: Search and select **Storage File Data SMB share Contributor** role.
   -Assign access to: **User, groups, or service principal**.
   -Select: Search and select **<inject key="AzureAdUserEmail" />** user.
   
   ![ws name.](media/msix6.png)
   
1. Search for **Stoarage accounts** in the search bar and select the **<inject key="Storage Account Name" />** account.

   ![ws name.](media/uiupdate10.png)
 
1. Go to **msixfile** file share and click on **Connect**.

   ![ws name.](media/msix7.png)
   
1. Under **Windows** tab. Select **Storage account key** and **copy** the code from the window.

   ![ws name.](media/msix8.png)
   
1. Go to home page, Search for **virtual machine** in the search bar. Select **AVD-HP01-SH-0**.

   ![ws name.](media/msix9.png)
   
1. Under **Operations** blade, Select Run Command. Select **RunPowerShellScript**.
    
   ![ws name.](media/msix10.png)
  
1. **Paste** the **code** which you copied earlier into the window and select **Run**. Once the execution is completed, Output will be displayed as mentioned in the screenshot below.

   ![ws name.](media/msix11.png)
   
   >**NOTE**: **This step is only required for this lab only. In the production environment, this is not required. You will use Azure active directory and Acess control(IAM) to control access to MSIX VHD file. For more information refer to ***Link yet to be Searched***.
   
1. Go to home page, Search for **virtual machine** in the search bar. Select **AVD-HP01-SH-1** VM.

   ![ws name.](media/msix12.png)
   
1. Under **Operations** blade, Select Run Command. Select **RunPowerShellScript**.
    
   ![ws name.](media/msix13.png)
  
1. **Paste** the **code** which you copied earlier into the window and select **Run**. Once the execution is completed, Output will be displayed as mentioned in the screenshot below.

   ![ws name.](media/msix11.png)
   
# ADD STEPS TO INSTALL CERTIFICATE INTO THE SESSION VM.

1. Go to **msixfile** file share and select the **7-Zip** file. **Copy** the **URL**.

   ![ws name.](media/msix15.png)

1. Navigate to Azure portal, then search for *Azure Virtual Desktop* in search bar and select **Azure Virtual Desktop** from the suggestions.

   ![ws name.](media/w1.png)

1. You will be directed towards the Azure Virtual Desktop management window.  

   ![ws name.](media/64.png)

1. Under **Manage** blade, Select the **MSIX** tab and click on **Add**.

   ![ws name.](media/msix17.png)
   
1. Paste the **URL** and follow the below mentioned steps to create **UNC** path.

   - **Remove** ``https://`` from the URL. Add ``\\`` to the starting of the link.
   - **Replace** all the ``/`` (front slash) with ``\`` (back slash0. 
   - The final UNC path should look like this ``\\fslogixprofilestg448267.file.core.windows.net\msixfile\7-Zip.vhd``.

   ![ws name.](media/msix16.png)

   Click on **Add*.
   
1. For **Display name**, provide **7-Zip** as the value and click on **Add**.

   ![ws name.](media/msix18.png)
   
1. Under **Manage** blade, Select the **Application groups** tab and click on **AVD-AG-01**.

   ![ws name.](media/msix19.png)
