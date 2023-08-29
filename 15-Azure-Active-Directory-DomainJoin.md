# Lab 15 : Azure Active Directory Domain Join (Read Only) 

## **Scenario**

 Contoso is planning to set up its infrastructure on Azure. As a first step, Contoso needs you to provision a host pool which is the main component of AVD. Creation of host pool also includes session hosts domain joined through Azure Active directory, default application group, and a workspace.

## **Overview**

 A Host Pool is a collection of Azure virtual machines that register to Azure Virtual Desktop as session hosts when you run the Azure Virtual Desktop agent. All session host virtual machines in a host pool should be sourced from the same image for a consistent user experience. To start with, we will login to the Azure portal.
 
## Exercise 1: Create Host Pool using Getting Started Wizard

In this exercise, We'll be creating the Host pool using **Getting Started Wizard** using minimum efforts and information.

1. On the **Azure portal** search for **Azure Virtual Desktop** in the **search bar** **(1)** and select **Azure Virtual Desktop** **(2)** from the suggestions.

   ![ws name.](media/2avd1.png)
   
2.	On the AVD **Overview page (1)**, click on Create a host pool **(2)**.

   ![image](https://user-images.githubusercontent.com/83349577/175352775-1ca92f9e-b510-4fee-89e5-8c476bcffa5b.png)

3.	On the **Basics** tab, provide the following information and click **Next: Virtual machines >**


   ![](media/LAB15-1.png)

   - Load balancing algorithm: **Breadth-first (2)**
   - Max session limit: **5** **(3)**

   ![](media/LAB15-2.png)


4.	On the **Virtual Machines** tab, provide the following information :

   ![](media/LAB15-5.png)

   - Number of VMs: **2 (4)**
   - OS disk type: **Standard SSD (5)**

   ![](media/LAB15-6.png)

   B. **Network and security**

   - Virtual network: Select **aadds-vnet (1)** from drop-down
   - Network security group: **Basic (3)**
   - Public inbound ports: **No (4)**

   ![](media/LAB15-7.png)

   C. **Domain to join**

   - Select which directory you would like to join: **Azure Active Directory (1)**
   - Enroll VM with Intune: **No**

   D. **Virtual Machine Administrator account**

   - Confirm password: **Password.1!!** **(4)**
   - Click on **Next : Workspace >**

   ![](media/LAB15-8.png)

5.	On the Workspace tab, provide the following information and click **Review + create (3)**:

   - Register desktop app group: **Yes (1)**
   - To this workspace: **GS-AVD-WS (2)**

     ![](media/LAB15-9.png)

6.	Verify the information and click **Create**.

   ![](media/createhp5-new.png)


   > **NOTE:** Usually it takes 20 mins to get deployed successfully. Sometimes it might take up to 90 minutes.

7.	Once the deployment is successful, click on **Go to resource**.

   ![ws name.](media/gsw7.png)

8.	It will take you to the Host pool. The following resources were created:

   - Host Pool: 1 (EB-AVD-AADJ-HP)
   - Session Host: 2 (AVD-AADJ-SH-0, AVD-AADJ-SH-1)
   - Application Group: 1 (EB-AVD-AADJ-HP-DAG)
   - Application: 1 (SessionDesktop)
   - Workspace: 1 (EB-AVD-WS)
     
   ![ws name.](media/LAB15-10.png)
   
9. Click on the **Next** button present in the bottom-right corner of this lab guide.  
   
