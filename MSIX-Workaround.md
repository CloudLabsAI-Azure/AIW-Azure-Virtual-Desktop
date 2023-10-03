# Lab 11: MSIX App Attach

## **Scenario**

Contoso wants a few applications to be installed in all the session's hosts. So Contoso had decided to implement the MSIX app attached in order to install the application across the session hosts and users should be able to access them. You will help Contoso to install one of the applications that is, the 7-Zip file manager, using the MSIX app attach feature.

## **Overview**

In this exercise, We'll be implementing MSIX App Attach for AVD. MSIX app attachment is a way to deliver MSIX applications to both physical and virtual machines. However, the MSIX app attached is different from regular MSIX because it's made especially for Azure Virtual Desktop. MSIX removes the need for repackaging when delivering applications dynamically.
Refer to this link ``https://docs.microsoft.com/en-us/azure/virtual-desktop/what-is-app-attach`` for more information.

## Exercise 1: Configuring AVD for MSIX App Attach

1. Search for **Storage accounts** in the search bar and select the **<inject key="Storage Account Name" />** account which was created in **Exercise 5: Setup FSLogix**.

1. In the right pane, click on **File shares (1)** present under *Data Storage* blade and click on **+File Share (2)**.

    ![ws name.](media/2avd123-new.png)
 
1. Enter the following name for your file share.
    
    - Name: **msixfile**   
    - Tier: **Transaction Optimized**
    - Click on **Create**, this will create the file share.
    
    ![ws name.](media/msix1.png)
    
1. Go to the **msixfile** file share which you just created and select **upload**.
   
   ![ws name.](media/msix3.png)
   
1. Browse the files go to ``C:\LabFiles``. Select **7-Zip.vhd**, **msix.cer** files and Click on **Open** then select **Upload**.

   ![ws name.](media/2avd125.png)
   
1. Select **Access Control(IAM) (1)** from the side blade. Click on **Add (2)** and select **Add Role Assignment (3)**.

   ![ws name.](media/updmsix5.png)
   
1. Select the following options and click **Save**

   - Role: Search and select **Storage File Data SMB share Contributor** role, then click on **Next**

     ![](media/role%20assignemnt-v2.png)
     
   - Under **Members**, enter the below details:
  
      - Assign access to **User, group, or service principal (1)**

      - Click on **+ Select members (2)**
      
      - Select: Search and select **<inject key="AzureAdUserEmail" />** user (3).

      - Click on **Select (4)**
   
   ![ws name.](media/members1-v2.png)
   
   - Select **Review + assign**
   
1. Search for **Storage accounts** in the search bar and select the **<inject key="Storage Account Name" />** account.

   ![ws name.](media/stacc-v2.png)
   
1. Under **Data storage**, select **File Shares (1)** and click on **msixfile (2)**.

   ![ws name.](media/2avd57.png) 
   
1. In **msixfile** file share and click on **Connect**.

   ![ws name.](media/msix7.png)
   
1. Under the **Windows** tab. Select **Storage account key** and **copy** the code from the window.

   ![ws name.](media/msix8.png)
   
1. Go to the home page and search for **virtual machine** in the search bar. Select **AVD-HP01-SH-0**.

   ![ws name.](media/2avd127.png)
   
1. Under the **Operations** blade, Select Run Command. Select **RunPowerShellScript**.
    
   ![ws name.](media/msix10.png)
  
1. **Paste** the **code** which you copied earlier into the window and select **Run**. Once the execution is completed, Output will be displayed as mentioned in the screenshot below.

   ![ws name.](media/msix11.png)
   
   >**NOTE**: **This step is required for this lab only**. In the production environment, this is not required. You will use Microsoft Entra ID and Access control(IAM) to control access to the MSIX VHD file. For more information refer to `` https://docs.microsoft.com/en-us/azure/virtual-desktop/app-attach-azure-portal ``.
   
1. Go to the home page and search for **virtual machine** in the search bar. Select **AVD-HP01-SH-1** VM.

   ![ws name.](media/2avd128.png)
   
1. Under the **Operations** blade, Select Run Command. Select **RunPowerShellScript**.
    
   ![ws name.](media/msix13.png)
  
1. **Paste** the **code** which you copied earlier into the window and select **Run**. Once the execution is completed, Output will be displayed as mentioned in the screenshot below.

   ![ws name.](media/msix11.png)
   
1. Search for **Stoarage accounts** in the search bar and select the **<inject key="Storage Account Name" />** account.

   ![ws name.](media/stacc-v2.png)
 
1. Under **Data storage**, select **File Shares** and click on **msixfile**.

   ![ws name.](media/2avd57.png) 
   
3. In **msixfile** file share, Click on **msix.cer (1)** file and copy the **URL (2)** and save it in **notepad**.
   
   ![ws name.](media/2avd58.png)
   
1. Go to the home page and search for **virtual machine** in the search bar. Select **AVD-HP01-SH-0**.

   ![ws name.](media/2avd75.png)
   
1. Under the **Operations** blade, Select Run Command. Select **RunPowerShellScript**.
    
   ![ws name.](media/msix10.png)
   
1. **Copy** the code mentioned below and paste the same into the window. **DO NOT** run the command as the **CERTIFICATE PATH** should be updated.   

   ```
   
   Import-Certificate -FilePath <CERTIFICATE PATH> -CertStoreLocation Cert:\LocalMachine\TrustedPeople
   
   ```
   
   ![ws name.](media/2avd59.png)
   
   >**NOTE**: This script will install the certificate in the AVD-HP01-SH-0 session host.

1. **Replace** the **CERTIFICATE PATH** with **msix.cer** file URL which you had copied earlier and follow the next step.

1. For **CERTIFICATE PATH** to be in the correct format, Follow the below-mentioned steps to create the path.

   - **Remove** ``https://`` from the URL. Add ``\\`` to the start of the link.
   - **Replace** all the ``/`` (front slash) with ``\`` (back slash0. 
   - The final UNC path should look like this ``\\fslogixprofilestgxxxxxx.file.core.windows.net\msixfile\msix.cer``.

   ![ws name.](media/2avd60.png)

1. Click on **Run**   
   
1. Once the execution is completed, you'll be able to see similar output as mentioned below.

   ![ws name.](media/msix27.png)

1. Go to the home page and search for **virtual machine** in the search bar. Select **AVD-HP01-SH-1** VM.

   ![ws name.](media/2avd76.png)
   
1. Under the **Operations** blade, Select Run Command. Select **RunPowerShellScript**.
    
   ![ws name.](media/msix13.png)

1. **Copy** the code mentioned below and paste the same into the window. **DO NOT** run the command as the **CERTIFICATE PATH** should be updated.   

   ```
   
   Import-Certificate -FilePath <CERTIFICATE PATH> -CertStoreLocation Cert:\LocalMachine\TrustedPeople
   
   ```
   
   ![ws name.](media/2avd59.png)
   
   >**NOTE**: This script will install the certificate in the AVD-HP01-SH-0 session host.

1. **Replace** the **CERTIFICATE PATH** with **msix.cer** file URL which you had copied earlier and follow the next step.

1. For **CERTIFICATE PATH** to be in the correct format, Follow the below-mentioned steps to create the path.

   - **Remove** ``https://`` from the URL. Add ``\\`` to the start of the link.
   - **Replace** all the ``/`` (front slash) with ``\`` (back slash0. 
   - The final UNC path should look like this ``\\fslogixprofilestgxxxxxx.file.core.windows.net\msixfile\msix.cer``.

   ![ws name.](media/2avd60.png)

1. Click on **Run**   
   
1. Once the execution is completed, you'll be able to see similar output as mentioned below.

   ![ws name.](media/msix27.png)
   
## Exercise 2: Creating MSIX Package in AVD environment
   
1. Go to **msixfile** file share and select the **7-Zip** file. **Copy** the **URL**.

   >**NOTE**: We'll be using this URL in further steps. Make sure you **Save** it in Notepad.

   ![ws name.](media/2avd77.png)

1. Navigate to the Azure portal, then search for *Azure Virtual Desktop* in the search bar and select **Azure Virtual Desktop** from the suggestions.

   ![ws name.](media/w1.png)

1. You will be directed towards the Azure Virtual Desktop management window.  

   ![ws name.](media/64.png)
   
1. Select **Host pools** from the side blade and **select** the **EB-AVD-HP** host pool.

   ![ws name.](media/2avd120.png)

1. Under **Manage** blade, Select the **MSIX packages (1)** tab and click on **Add (2)**.

   ![ws name.](media/2avd124.png)
   
1. Paste the **URL** and follow the below-mentioned steps to create **UNC** path.

   - **Remove** ``https://`` from the URL. Add ``\\`` to the start of the link.
   - **Replace** all the ``/`` (front slash) with ``\`` (back slash0. 
   - The final UNC path should look like this ``\\fslogixprofilestg448267.file.core.windows.net\msixfile\7-Zip.vhd``.

   ![ws name.](media/msix16.png)

   Click on **Add**.
   
1. For **Display name**, provide **7-Zip** as the value and enable state as **Active**. Click on **Add**.

   ![ws name.](media/msix-package-01.png)
   
1. Under **Manage** blade, Select the **Application groups** tab and click on **AVD-AG-01**.

   ![ws name.](media/msix19.png)

1. Under **Manage** blade, Select the **Applications (1)** tab and click on **Add (2)**.

   ![ws name.](media/addappli-v2.png)
   
1. In **Add Application** tab, 

   - For **Application Source**, select **MSIX Package** from the drop-down. 
   - For **Application name**, provide **7-Zip** as the value.
   - CLick on **save**.

   ![ws name.](media/msix23.png)
   
   Now, The MSIX implementation is completed. We'll check the working of it.
    
1. On your PC go to **Start** and search for **Remote desktop** and open the remote desktop application with the exact icon as shown below.

   ![ws name.](media/137.png)
   
1. Once the application opens, click on **Subscribe**.

   ![ws name.](media/a49.png)
  
1. Enter your **credentials** to access the workspace.

   - Username: *Paste your username* **<inject key="AzureAdUserEmail" />** *and then click on **Next**.*
   
   ![ws name.](media/95.png)

   - Password: *Paste the password* **<inject key="AzureAdUserPassword" />** *and click on **Sign in**.*

   ![ws name.](media/96.png)
   
   >**Note:** If there's a popup entitled **Help us protect your account** click **Skip for now (14 days until this is required)**

   ![](media/skipfornow.png)

1. Make sure to **uncheck** *Allow my organization to manage my device* and click on **No, sign in to this app only**.

   ![ws name.](media/ex4t1s9.png)
      
1. The AVD dashboard will launch, then double-click on the **SessionDesktop** application to access it.

   ![ws name.](media/7-zip.png)
   
1. A window saying *Connecting to: Session Desktop* will appear. Wait for a few seconds, then enter your password to access the Desktop.

   - Password: **<inject key="AzureAdUserPassword" />**
   
   ![ws name.](media/ch14.png)
   
   >**Note:** If there's a dialog box saying ***Help us protect your account***, then select the **Skip for now** option.
   
   ![](media/login.png)

1. Wait for the Session Desktop to connect.

   ![ws name.](media/ex4t2s4.png)

1. Once connected, In the **start menu** search for **7-Zip File Manager** and you'll be able to see that the application is present in the session desktop.

   ![](media/2avd63.png)
   
   > **Note:** If you don't see the app in the Session Desktop, follow the below steps:
   >
   >  - In the **Search bar**, search for **Control Panel** and click on it to open.
   >
   >     ![](media/2avd68.png)
   >   
   >  - On Computer Settings page, click on **View new network status and tasks**
   >
   >      ![](media/view%20network%20status.png)
   >      
   >  - On **Network and Sharing center** page, click on **Change advanced sharing settings**.
   >
   >       ![](media/change%20advanced.png)
   >    
   >  - On **Advanced sharing settings** page, check the box next to **Turn on network discovery (1)** under Network Discovery and click on **Save changes (2)**
   >
   >      ![](media/turn%20on%20nd.png)
   >     
   >  - Restart the session desktop and continue with the next steps

1. In the **start menu** search for **Apps & features** and click on it to open.

   ![](media/2avd64.png)

1. In **Search bar**, Search for **7-Zip File Manager** and you'll able to see the application.

   ![](media/2avd65.png)

  
1. In the **start menu** search for **Control Panel** and click on it to open.

   ![](media/2avd68.png)

1. In the Control Panel, Click on **Uninstall a program**.

   ![](media/2avd69.png)

1. Here, you'll notice that **7-Zip File Manager** is not present as an application.

   ![](media/2avd70.png) 

1. In the **start menu** search for **Computer Management** and click on it to open.

   ![](media/2avd66.png)

1. In Computer Management page, Under **Storage** select **Disk Management**. Here you'll see that VHD has been mounted. This is where the **7-ZIP File Manager** is present and has been assigned to the session desktop dynamically. This confirms the implementation of MSIX App Attach.

   ![](media/2avd67.png)

1. Click on the Next button present in the bottom-right corner of this lab guide.
