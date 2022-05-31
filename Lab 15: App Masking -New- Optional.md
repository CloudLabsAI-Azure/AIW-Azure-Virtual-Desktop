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
    
12. Provide a name for the Rule Set as **hidepowershell (1)** and click on **Enter file name (2)**.

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
     
16. Now in your JumpVM,  go to Start and search for **PowerShell (1)** and double click on **Windows Powershell ISE (2)** to open the application. Here you will not be able to open the app due to the hiding rule applied to your VM. 

     ![](../Azure-Virtual-Desktop-v3/media/powershell.png)
     
    **Note :** In the same way, you can apply the hiding rule to session desktop in the remote desktop from your JumpVM.
    
17. Navigate back to FSLogix App Rule Editor and click on **Manage Assignments**.

    ![](../Azure-Virtual-Desktop-v3/media/manageassign.png)
    
18. On Assignments tab, click on **Add**.

    ![](/Azure-Virtual-Desktop-v3/media/add.png)
    
19. Click on **User**.

    ![](../Azure-Virtual-Desktop-v3/media/user.png)
    
20. On the **Select User** dialogue box, follow the below instructions:

    - **User** : Paste the username  **<inject key="Avd User 01" /> (1)**
    - Click on **Ok (2)**

    ![](../Azure-Virtual-Desktop-v3/media/adduser.png)
    
21. After adding the User, click on **Apply (1)** and **Ok (2)**.

    ![](../Azure-Virtual-Desktop-v3/media/applyandadd.png)
    
 22. Now you have added the User to the same hiding rules to hide PowerShell application. Click on **Apply Rules to System** to apply the created rule in your Session host in Remote desktop.

     ![](../Azure-Virtual-Desktop-v3/media/applyrul.png)
     
23. Paste the below-mentioned link in your browser in the **JumpVM** and enter your **credentials** to login. 

     ```
     aka.ms/wvdarmweb
     ```

   - Username: *Paste the username*  **<inject key="Avd User 01" />** then click on **Next**.
   
     ![ws name.](media/username.png)

   - Password: *Paste the password*  **<inject key="AVD User Password" />** *and click on* **Sign in**.

     ![ws name.](media/password.png)

     >**Note:** If there's a dialog box saying ***Help us protect your account***, then select the **Skip for now** option.

      ![](media/login1.png)

24. Now in the AVD dashboard, click on the **Session Desktop** to access it. 

    ![ws name.](media/desktp-v2.png)

25. Select **Allow** on the prompt asking permission to *Access local resources*.

    ![ws name.](media/Accessallowres-v2.png)

26. Enter your **credentials** to access the application and click on **Submit**.

   - Username: *Paste the username*  **<inject key="Avd User 01" />** then click on **Next**.*
   
   - Password: *Paste the password*  **<inject key="AVD User Password" />** *and click on* **Sign in**.
   
     ![ws name.](media/lb52.png)
     
27. 


   
