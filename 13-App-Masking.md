# Lab 13: App Masking (Read - Only)


### Overview

Application Masking is used to manage user access to installed components. Application Masking may be used in both physical and virtual environments. Application Masking is most often applied to manage non-persistent, virtual environments, such as Virtual Desktops.


## Exercise 1: Install Google Chrome on Session Hosts

In this task, we will install Google Chrome in the AVD-HP01-SH-0 session host using a PowerShell script.

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
#Create Directories
$LabFilesDirectory = "C:\LabFiles"

if(!(Test-path -Path "$LabFilesDirectory")){
    New-Item -Path $LabFilesDirectory -ItemType Directory |Out-Null
}
if(!(Test-path -Path "$LabFilesDirectory\GoogleChrome")){
    New-Item -Path "$LabFilesDirectory\GoogleChrome" -ItemType Directory |Out-Null
}

#Download Google Chrome

if(!(Test-path -Path "$LabFilesDirectory\ChromeStandaloneSetup64.exe")){
    Invoke-WebRequest -Uri "https://dl.google.com/tag/s/appguid%3D%7B8A69D345-D564-463C-AFF1-A69D9E530F96%7D%26iid%3D%7B4549E3D4-D0C4-1201-C4B3-39A7175143AB%7D%26lang%3Den%26browser%3D3%26usagestats%3D0%26appname%3DGoogle%2520Chrome%26needsadmin%3Dprefers%26ap%3Dx64-stable-statsdef_1%26installdataindex%3Dempty/chrome/install/ChromeStandaloneSetup64.exe" -OutFile "$LabFilesDirectory\GoogleChrome\ChromeStandaloneSetup64.exe"

    #Install Google Chrome
    $pathvargs = {C:\LabFiles\GoogleChrome\ChromeStandaloneSetup64.exe /silent /install}
    Invoke-Command -ScriptBlock $pathvargs

    #Display script completion in the console
    Write-Host "Script Executed successfully"
}
Else {
    #Display script error in the console
    Write-Host "Could not find Google Chrome installer"
}
```
 ![image](https://user-images.githubusercontent.com/83349577/175347015-6cfba26e-fbf8-4cf9-bfa9-6d6f1547596e.png)
 
 Note: The above script will Install Google Chrome
 
7.	Then click on **Run** to execute the script.


8.	Wait for some time for the script to execute. Once done, it will show an output saying **Script Executed successfully**.

   ![image](https://user-images.githubusercontent.com/83349577/175347230-9abe6dc3-7e3b-4e95-a3d5-85e4034d164c.png)

   Note: It will take around five minutes for the script to execute.
   
9. Navigate to virtual machines and click on **AVD-HP01-SH-1**.

    ![image](https://user-images.githubusercontent.com/83349577/175347379-ac20a82e-8ead-4523-a4d8-f75a927a55be.png)

10. Click on **Run command (1)** under Operations. Then select **RunPowerShellScript (2)**.

    ![image](https://user-images.githubusercontent.com/83349577/175347558-bda31f12-5470-4e1d-be5d-a4e67b94729c.png)

11. Copy the script given below and paste it by using Ctrl + V in the Powershell window.

  

```
#Create Directories
$LabFilesDirectory = "C:\LabFiles"

if(!(Test-path -Path "$LabFilesDirectory")){
    New-Item -Path $LabFilesDirectory -ItemType Directory |Out-Null
}
if(!(Test-path -Path "$LabFilesDirectory\GoogleChrome")){
    New-Item -Path "$LabFilesDirectory\GoogleChrome" -ItemType Directory |Out-Null
}

#Download Google Chrome

if(!(Test-path -Path "$LabFilesDirectory\ChromeStandaloneSetup64.exe")){
    Invoke-WebRequest -Uri "https://dl.google.com/tag/s/appguid%3D%7B8A69D345-D564-463C-AFF1-A69D9E530F96%7D%26iid%3D%7B4549E3D4-D0C4-1201-C4B3-39A7175143AB%7D%26lang%3Den%26browser%3D3%26usagestats%3D0%26appname%3DGoogle%2520Chrome%26needsadmin%3Dprefers%26ap%3Dx64-stable-statsdef_1%26installdataindex%3Dempty/chrome/install/ChromeStandaloneSetup64.exe" -OutFile "$LabFilesDirectory\GoogleChrome\ChromeStandaloneSetup64.exe"

    #Install Google Chrome
    $pathvargs = {C:\LabFiles\GoogleChrome\ChromeStandaloneSetup64.exe /silent /install}
    Invoke-Command -ScriptBlock $pathvargs

    #Display script completion in the console
    Write-Host "Script Executed successfully"
}
Else {
    #Display script error in the console
    Write-Host "Could not find Google Chrome installer"
}
```
![image](https://user-images.githubusercontent.com/83349577/175347801-0b0d0082-0eae-46be-8248-d307e25bf2f7.png)

 > **Note:** The above script will Install Google Chrome.

12. Then click on Run to execute the script.

13. Wait for some time for the script to execute. Once done, it will show an output saying Script Executed successfully.

   ![image](https://user-images.githubusercontent.com/83349577/175348086-9041a20c-909e-4821-94bf-961e015f8eab.png)

   > **Note:** It will take around five minutes for the script to execute.






    


##  Exercise 2: App Masking


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
     
18. Within the session desktop, go to Start and search for **Chrome (1)** and double click on **Google Chrome (2)** to open the application. Here you will not be able to open the app due to the hiding rule applied to your session desktop through JumpVM. 

     ![](media-1/googlechrome.png)

19. You have successfully added the hiding rule through App Masking for both the JumpVM and Session host.

20. Click on the **Next** button present in the bottom-right corner of this lab guide.  
