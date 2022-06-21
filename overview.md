### **Azure Virtual Desktop**

## **Lab Context and Session Overview**

Contoso IT consulting services, headquartered in Los Angeles, California, is one of the top IT consulting companies in the US. Contoso IT’s rapid expansion, often fueled through acquisitions, has led to the establishment of multiple office locations throughout North America. 

Contoso IT’s rapid growth has made it more challenging to provide its employees with the resources they need to do their jobs effectively. Contoso IT has more employees, working in more locations (including their homes), with more clients that often require specialized resources to complete their projects. 

Contoso’s IT team must find a way to provide employees with secure access to corporate resources to help them be productive wherever they are and deliver the resources they need to provide the high-quality IT consulting services that have fueled Contoso’s growth.  

Contoso’s IT team contacted its Microsoft account team to evaluate solutions.


## **Solution Context**

Contoso IT explained that they were looking to deploy their IT budget in a way that met the needs of its  IT consultants and its in-house IT team. For its consultants, Contoso needs to spend money on technology that: 
 - Delivers a Windows 11 or 10 experience with no learning curve for employees 
 - Provides the compute power and applications necessary to handle the standard and specialized work required for Contoso IT’s project engagements 
 - Works equally well no matter where employees are (in the office, at the client site, or at home) 

For Contoso’s in-house IT team, the solution they invest in must be:
 - **Secure** It must provide the safeguards necessary to protect and prevent unauthorized access to client data or the Contoso corporate network 
 - **Flexible** The solution must integrate with Contoso IT’s existing technology management infrastructure and provide Contoso’s admins the ability to patch, protect, and deploy it. 
 - **Cost effective** Because Contoso’s client engagements often require periods of extreme compute intensity followed by periods of lighter technical engagement, technology investments that can help them control costs without requiring additional capital investments. 

After learning of these requirements, the Microsoft account team recommended Azure Virtual Desktop as the cloud solution to meet Contoso IT services current and future needs. 


## **Lab Activities**

In this lab, you’ll assume the role of an Azure consultant tasked with creating the Azure Virtual Desktop Environment for Contoso IT services. You will configure and deploy: 
 - **Azure Infrastructure components** (Virtual Machines (VMs), Storage, Networking, Resource Groups) necessary to deliver Azure Virtual Desktop to Contoso IT’s employees 
 - **Azure Active Directory** (Azure’s Identity and Access Management solution) components necessary for providing secure access to AVD resources. 
 - **Azure Virtual Desktop Host Pools** that take the configured Azure Infrastructure components and convert them into one or more identical VMs (also known as Session Hosts)  
 - **Azure Virtual Desktop Application groups** which allow you to publish desktops and remote applications that authenticated Contoso users can use 
 - **FSLogix user profiles** that allow user specific customizations (desktop backgrounds, layouts, and other settings) to be available anytime a user accesses a VM 
 - **MSIX apps** that can be securely published for access by Session Hosts 
 - **A purpose-built version of Microsoft Teams** designed to improve the communication and audio-visual experience for Azure Virtual Desktop users 
 - And finally, **Monitoring and Security** so that Azure Virtual Desktop administrators can optimize performance and ensure that their environment is secure and well managed. 

## **Lab 1: Create Host Pool using Getting Started Wizard**

In this lab with the help of **Getting Started** wizard we will be creating an Azure Virtual Desktop host pool for pooled desktops. This is a set of computers or hosts which operate on an as-needed basis. In a pooled configuration we will be hosting multiple non-persistent sessions, with no user profile information stored locally. This is where FSLogix Profile Containers provide the users profile to the host dynamically. This provides the ability for an organization to fully utilize the compute resources on a single host and lower the total overhead, cost, and number of remote workstations.

You will be deploying the AVD Host Pool in an already deployed Azure active directory domain service(AAD DS) instance. Since Contoso is already using an AAD DS Service, AAD DS Service will provide Identity and Authentication service.

## **Lab 2 (A): Monitoring using Log Analytics**

In this lab we will deploy a Log Analytics workspace then, we will setup monitoring for our AVD host pools. There are multiple reasons why monitoring serves a critical role: troubleshooting, performance, security, etc. There are also multiple components that make up the AVD service, which can add some variation on how customers implement monitoring
    
## **Lab 3: Create Application Groups and assign to users**
    
In this lab we will be creating a application group, adding new applications and will be assigning users who will be able to access to those applications.
    
## **Lab 4: Access the Published Applications and Desktop using Browser**

In this lab we will be accessing the published applications and session desktop in our Azure Virtual Desktop environment with the help of a browser.
    
## **Lab 5: Access the Published Applications and Desktop using AVD Desktop Client**
    
In this lab we will be accessing the published applications and session desktop in our Azure Virtual Desktop environment with the help of AVD Desktop Client on out local system.
    
## **Lab 6: Setup FSLogix**
 
In this lab, we will be creating an Azure File share and enabling SMB access via Active Directory authentication. Azure Files is a platform service (PaaS) and is one of the recommended solutions for hosting FSLogix containers for AVD users. At the end of this exercise, you will have the following components:

- A new storage account in your Azure subscription.
- A new Azure file share for your FSLogix profile containers.
- AD authentication enabled for your Azure storage account.
- Permissions applied for user access to the file share.
    
## **Lab 7: Load Balancing methods**
    
In this lab we will be seeing the user allocation among session host between both Depth first anf Breadth first approach.

## **Lab 8: Auto Scaling**

In this lab we will be creating the Scaling plan, which lets us scale your session host virtual machines (VMs) in a host pool up or down to optimize deployment costs.

## **Lab 9: Cost Optimizations**

In this lab, We'll be enabling the Start Virtual Machine (VM) on Connect feature in host pool which lets you save costs by allowing users to turn on their VMs only when they need them.

## **Lab 10: Security Modules**

In this lab we will be configuring the Security Modules to prevent the sensitive information by setting up the Multi-Factor Authentication (MFA) and will be Creating Conditional Access Policy, Screen Capture Protection and App Locker.

## **Lab 11: Multimedia redirection for Azure virtual desktop**

In this lab we will be configuring Session host for implementing MS Teams and configure hostpool for teams requirements. Later we will be accessing MS Teams using Remote Desktop Application

## **Lab 12: MSIX App Attach**

In this lab, first we will be configuring AVD for MSIX App Attach then later will be creating MSIX Package in AVD environment.

## **Lab 13: App Masking (Optional)**

In this lab, you will be configuring the App Masking which is used to manage user access to installed components. Application Masking may be used in both physical and virtual environments. Application Masking is most often applied to manage non-persistent, virtual environments, such as Virtual Desktops.

## **Lab 14: Migration Tools (Optional)**

In this lab, we will be going through with few documents which explains about the Migration Tools in AVD.

## **Lab 15 : Azure Active Directory Domain Join (Read Only)**

Azure Active Directory (Azure AD) provides many benefits for organizations, such as modern authentication protocols, single sign-on (SSO), and support for FSLogix user profiles. Azure Virtual Desktop virtual machine (VM) session hosts can join directly to Azure AD. Joining directly to Azure AD removes an earlier need to use Active Directory Domain Services (AD DS) domain controllers.

## **Lab 2 (B): Monitoring using Azure Monitor for AVD**

In this lab we will be looking at the informatgion collected by Azure Monitoring with the help of log analytics workspace created earlier.

Click on the **Next** button present in the bottom-right corner of this lab guide.
