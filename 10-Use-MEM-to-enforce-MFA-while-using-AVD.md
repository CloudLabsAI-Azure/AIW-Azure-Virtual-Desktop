# Lab 9: Use MEM to enforce MFA while using AVD

## **Scenario**

Contoso wants their resources to be secure and protected from any kind of unethical activities. So Contoso wants to enable Multi factor authentication (MFA) for session login. You will guide Contoso to set up MFA for sign-ins.

## **Overview**

In this lab, We'll be enabling Multi-Factor authentication, Multi-factor authentication is a process where a user is prompted during the sign-in process for an additional form of identification which increases the level of security.

### Exercise 1: Setup Multi-Factor Authentication (MFA)

1. In your JumpVM launch browser and visit `https://AKA.ms/proofup` and if asked to log in then log in using the following credentials:

   - Username: **<inject key="AzureAdUserEmail" />**
   - Password: **<inject key="AzureAdUserPassword" />**
  
2. On a prompt saying "Help us protect your account" click on **Next**.

   ![](media/mfa-00.png)

3. Download the **Microsoft Authenticator** app on your Mobile from App Store. After installing the app, select **Next**.

   ![](media/mfa-01.png)
   
4. In the Microsoft Authenticator app, set up your account by adding a work or school account. After adding an account select **Next**.

   ![](media/mfa-02.png)
   
5. To connect the Microsoft Authenticator app with your account, **Scan the QR code** and select **Next**.

   ![](media/mfa-03.png)
   
6. A Notification to Approve will pop-up on your mobile. Approve that and select **Next**.

   ![](media/mfa-04.png)
   
7. Enter the details required to set up MFA.

   - Country Code: Select the country code of your mobile number (1)
   - Mobile Number: Enter the number which you want to use for the MFA (2)
   - Method: Select **Text me a code** (3)
   - Click on **Next**.

   ![](media/textme.png)

8. Authenticate the login according to the authentication method you have chosen in the previous step to complete the verification.

   ![](media/SMSverified.png)
  
9. Now after a few seconds the status will change to **Verification Success**, click on **Done** to finish the MFA registration.

   ![](media/mfa-07.png)
  
### Exercise 2: Creating Conditional Access Policy

1. In Azure Portal search for *Azure Active Directory* and click on the search result.

   ![](media/avdv21.png)

2. From the left-hand side blade, click on **Properties** (1) under Manage and scroll down to select **Manage Security Defaults** (2) at the bottom of the page.

   ![](media/aad-properties-01.png)
   
3. In **Enable Security defaults** pane, for **Enable Security defaults** select to **No** (1) and check the box for **My organization is using Conditional Access** (2). Then select **Save** (3).

   ![](media/aad-properties-02.png)

4. From the left-hand side blade, click on **Security** under Manage.

   ![](media/2avd118.png)
  
5. In **Security** page select **Conditional Access** under Protect.

   ![](media/avdv23.png)
  
6. Under the Policies page click on **+ New Policy**. Select **Create new policy**.

   ![](media/avdv24.png)

7. Configure the Conditional Access Policy with the following details:

   - Name: **AVD-MFA** (1)
   - **Assignments**:
   - Click on **Users or workload identities** (2)
   - A new window will slide in, there click on **Select users and Groups** (3) and then select the check box saying **Users and groups** (4)
   - Now a *Select* window will open, here search for ODL user and Select it (5)
   - Click on **Select** (6) button
   
   ![](media/feb2.png)
   
   - Click on **Cloud apps or actions** (1)
   - Click on **Select apps** (2)
   - Search for **Windows Virtual Desktop** and click on the **check box** of **Azure Virtual Desktop** (3) next to the search result
   - Now Click on **Select** (4) button.

   ![](media/conditional-access-apps.png)
  
   - Click on **Conditions** (1)
   - Then select **Client apps** (2)
   - Now in the Client Apps blade toggle the *Configure* switch to **Yes** (3) and make sure that all the checkboxes below are selected.
   - Then click on **Done** (4)

   ![](media/avdv27.png)
  
   - **Access Control**
   - Click on **Grant** (1)
   - Select the Check Box saying **Require multi-factor authentication** (2)
   - Then click on **Select** (3)

   ![](media/avdv28.png)
   
8. Toggle the **Enable Policy** switch to **On** and click on **Create**.

   ![](media/avdv29.png)
  
9. Now, Open the following URL in a new browser tab in the JumpVM. This URL will lead us to the Remote Desktop Web Client.

   ``` 
   aka.ms/wvdarmweb 
   ``` 

   >**Note:** If you are already logged in through your user, then jump to step 3 else continue with the next step i.e., Step 2.

10. Now to login, enter the lab credentials as mentioned below:

   - Username: *Paste your username* **<inject key="AzureAdUserEmail" />** *and then click on **Next**.*
   
     ![ws name.](media/95.png)

   - Password: *Paste the password* **<inject key="AzureAdUserPassword" />** *and click on **Sign in**.*

     ![ws name.](media/96.png)
   
11. You'll see a dialog box to authenticate your login which is the indication of MFA implementation. Authenticate the login according to the authentication menthod you have chosen in exercise 1, step 7 to complete the verification.

     ![ws name.](media/2avd54.png)

    >**Note:** If there's a dialog box saying ***Help us protect your account***, then select the **Skip for now** option.

     ![](media/login.png)
   
12. The AVD dashboard will be launched. 

     ![](media/EB-AVD-WS.png)
    
13. Click on the **Next** button present in the bottom-right corner of this lab guide.
