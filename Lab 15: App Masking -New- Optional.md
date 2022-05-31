# Lab 15: App Masking -New- Optional


##  Exercise-1 : App Masking


### Overview

Application Masking is used to manage user access of installed components. Application Masking may be used in both physical and virtual environments. Application Masking is most often applied to manage non-persistent, virtual environments, such as Virtual Desktops.


1. Inside the Jump VM, copy and paste the below mentioned URL to dowload the **FSLogix**.

  ```
  https://download.microsoft.com/download/e/a/1/ea1bcf0a-e66d-48d2-ac9f-e385e5a7456e/FSLogix_Apps_2.9.8171.14983.zip
  ```
  
2. After downloding, extract the files to default path.

3. After extracting the zip folder, navigate to the path ```C:\Users\demouser\Downloads\FSLogix_Apps_2.9.8171.14983\x64\Release``` to setup FSLogix app.

4. Double click on the **FSLogixAppsSetup** to install the app setup.

   ![](../Azure-Virtual-Desktop-v3/media/FSLAS.png)
   
5. On the **Microsoft FSLogix Apps Setup** dialoge box, check the box ***I agree to the license terms and conditions (1)*** and click on ***Install (2)***.

   ![](../Azure-Virtual-Desktop-v3/media/installapp.png)
   
6. Click on ***Yes***, if you are prompted with pop-out.

7. Now navigate back to the same path in file explorer and double click on ***FSlogixAppsRuleEditorSetup*** to install ***Rule Editor*** app.

    ![](../Azure-Virtual-Desktop-v3/media/ruleeditor.png)
    
8.  On the **Microsoft FSLogix Apps RuleEditor Setup** dialoge box, check the box ***I agree to the license terms and conditions (1)*** and click on ***Install (2)***.

    ![](../Azure-Virtual-Desktop-v3/media/ruleeditorsetup.png)
    
9.  Click on ***Yes***, if you are prompted with pop-out.

10. In your JumpVM,  go to Start and search for **FSLogix Apps RuleEditor** and open the FSLogix Apps RuleEditor application.

    ![](../Azure-Virtual-Desktop-v3/media/selectRE.png)
    
11. On FSLogix Apps RuleEditor application, click on **New**.

    ![](../Azure-Virtual-Desktop-v3/media/new.png)
    
12. Enter the file name as **hidepowershell (1)** and click on **Enter file name (2)**.

    ![](../Azure-Virtual-Desktop-v3/media/hidepowershell.png)
    
13. On the **Rule Set : hidepowershell** dialogue box, follow the below instructions:

    - Select ***Choose from installed programs (1)***
    -  Click on ***Browse (2)***
    -  Navigate to the mentioned path ***C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Windows PowerShell (3)***
    -  Click on ***Scan (4)***
    
    ![](../Azure-Virtual-Desktop-v3/media/chooseprogram.png)
    
14. After Scan completes succesfully, click on ***Ok***.

     ![](../Azure-Virtual-Desktop-v3/media/scnok.png)
     
15. Now you have created the hiding rules to hide PowerShell application. Click on **Apply Rules to System** to apply the created rule in your JumpVM.

     ![](../Azure-Virtual-Desktop-v3/media/applyrul.png)
     
16. 

   
