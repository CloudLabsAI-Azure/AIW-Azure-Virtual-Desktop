# Lab 13: App Masking (Optional)


### Overview

Application Masking is used to manage user access to installed components. Application Masking may be used in both physical and virtual environments. Application Masking is most often applied to manage non-persistent, virtual environments, such as Virtual Desktops.

##  Exercise 1: Create Rule Set using FSLogix Apps RuleEditor (Read-Only)

In this exercise, you go through the steps to create rule set in **FSLogix Apps RuleEditor** to disable the access to the application in the session hosts.


1. In your JumpVM,  go to Start and search for **FSLogix Apps RuleEditor** and open the FSLogix Apps RuleEditor application from the search results

    ![](../Azure-Virtual-Desktop-v3/media/selectRE.png)
    
2. On the FSLogix Apps RuleEditor application, click on **New**.

    ![](../Azure-Virtual-Desktop-v3/media/new.png)

3. Provide a name for the Rule Set as **hiderule (1)** and click on **Enter file name (2)**.

    ![](media-1/hiderule.png)

1. On the **Rule Set : hiderule** window, choose **Blank Rule Set (1)** and click on **Ok (2)**.

   ![](media-1/blankrule.png)
   
1. On **FSLogix Apps RuleEditor**, click on **+ New Rule**.

    ![](media-1/newrule.png)
    
1. Click on **Browse (1)** and select **File (2)**.

    ![](media-1/file.png)
    
1. Navigate to the path **C:\Program Files\Microsoft Office\root\Office16 (1)**, select **MSAccess (2)** and click on **Open (3)**

   ![](media-1/msaccess.png)
   
1. After selecting the application, click on **Ok**.

   ![](media-1/clickok.png)
   
  > **Note :** The rule sets are already created as part of pre-requists.


##  Exercise 2: App Masking

In this task, you will downlaod the pre-created rule sets into session host using a PowerShell script.

1. In your Azure portal search for Virtual machines in the search bar and click on Virtual Machines from the suggestions.

   ![image](https://user-images.githubusercontent.com/83349577/175346152-3f8dce30-9412-49c7-a974-6b2b0c9d1479.png)

2. Click on AVD-HP01-SH-0.

   ![image](https://user-images.githubusercontent.com/83349577/175346345-4afff1e0-2259-4b8c-9f7e-4b1ed6a55287.png)
   
3. Then click on Run command under Operations.

   ![image](https://user-images.githubusercontent.com/83349577/175346507-01f314bb-1fd0-4ce6-bfc4-f94dcd86e62a.png)

4. Now select RunPowerShellScript.
 
   ![image](https://user-images.githubusercontent.com/83349577/175346633-755b0351-9aa1-4632-af15-66412246ea55.png)

5.	A similar window as that of the below image will appear.

   ![image](https://user-images.githubusercontent.com/83349577/175346718-bf993fb4-06b8-4bca-8f61-7750c7f46c11.png)

6.	Copy the script given below and paste it by using Ctrl + V in the Powershell window.

   ```
   $WebClient = New-Object System.Net.WebClient
   $WebClient.DownloadFile("https://raw.githubusercontent.com/CloudLabsAI-Azure/AIW-Azure-Virtual-Desktop/Azure-Virtual-Desktop-v3/LabFiles/hiderule.fxa","C:\Program Files\FSLogix\Apps\Rules\hiderule.fxa")

  $WebClient = New-Object System.Net.WebClient
  $WebClient.DownloadFile("https://raw.githubusercontent.com/CloudLabsAI-Azure/AIW-Azure-Virtual-Desktop/Azure-Virtual-Desktop-v3/LabFiles/hiderule.fxr","C:\Program Files\FSLogix\Apps\Rules\hiderule.fxr")
  #Display script completion in the console
   Write-Host "Script Executed successfully"
  ```

  ![](media-1/script.png)
  
7.	Then click on **Run** to execute the script.


8.	Wait for some time for the script to execute. Once done, it will show an output saying **Script Executed successfully**.

   ![image](media-1/scriptexecuted.png)

   Note: It will take around 1-2 minutes for the script to execute.
   
9. Navigate to virtual machines and click on **AVD-HP01-SH-1**.

    ![image](https://user-images.githubusercontent.com/83349577/175347379-ac20a82e-8ead-4523-a4d8-f75a927a55be.png)

10. Click on **Run command (1)** under Operations. Then select **RunPowerShellScript (2)**.

    ![image](https://user-images.githubusercontent.com/83349577/175347558-bda31f12-5470-4e1d-be5d-a4e67b94729c.png)

11. Copy the script given below and paste it by using Ctrl + V in the Powershell window.

  

   ```
   $WebClient = New-Object System.Net.WebClient
   $WebClient.DownloadFile("https://raw.githubusercontent.com/CloudLabsAI-Azure/AIW-Azure-Virtual-Desktop/Azure-Virtual-Desktop-v3/LabFiles/hiderule.fxa","C:\Program Files\FSLogix\Apps\Rules\hiderule.fxa")

   $WebClient = New-Object System.Net.WebClient
   $WebClient.DownloadFile("https://raw.githubusercontent.com/CloudLabsAI-Azure/AIW-Azure-Virtual-Desktop/Azure-Virtual-Desktop-v3/LabFiles/hiderule.fxr","C:\Program Files\FSLogix\Apps\Rules\hiderule.fxr")
   #Display script completion in the console
   Write-Host "Script Executed successfully"
   ```
![image](media-1/script.png)



12. Then click on Run to execute the script.

13. Wait for some time for the script to execute. Once done, it will show an output saying Script Executed successfully.

   ![image](media-1/scriptexecuted.png)

   > **Note:** It will take around 1-2 minutes for the script to execute.

14. Paste the below-mentioned link in your browser in the **JumpVM** and enter your **credentials** to log in. 

     ```
     aka.ms/wvdarmweb
     ```

   - Username: *Enter the username*  **<inject key="Avd User 01" />** then click on **Next**.
   
     ![ws name.](media/username.png)

   - Password: *Paste the password*  **<inject key="AVD User Password" />** *and click on* **Sign in**.

     ![ws name.](media/password.png)

     >**Note:** If there's a dialog box saying ***Help us protect your account***, then select the **Skip for now** option.

      ![](media/login1.png)

15. Now in the AVD dashboard, click on the **Session Desktop** to access it. 

    ![ws name.](media/desktp-v2.png)

16. Select **Allow** on the prompt asking permission to *Access local resources*.

    ![ws name.](media/Accessallowres-v2.png)

17. Enter your **credentials** to access the application and click on **Submit**.

   - Username: *Paste the username*  **<inject key="Avd User 01" />** then click on **Next**.
   
   - Password: *Paste the password*  **<inject key="AVD User Password" />** *and click on* **Sign in**.
   
     ![ws name.](media/lb52.png)
     
18. Within the session desktop, go to Start and search for **Acess (1)** and double click on **Access (2)** to open the application. Here you will not be able to open the app due to the hiding rule applied to your session desktop through JumpVM. 

     ![](media-1/accessblock.png)

19. You have successfully added the hiding rule through App Masking for both the JumpVM and Session host.

20. Click on the **Next** button present in the bottom-right corner of this lab guide.  

