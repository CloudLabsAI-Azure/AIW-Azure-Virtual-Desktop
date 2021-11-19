### **Azure Virtual Desktop**

## **Overview**

Contoso IT consulting services, headquartered in Los Angeles, California, is one among the top IT companies in the country and it is located throughout North America. These locations continue to grow through acquisition. The nature of their business requires a high level of security of Personal Identifiable Information (PII) for their employees.

## **Hands-on Labs Scenario**

Contoso IT consulting services has grown rapidly and this has created a new challenge. Contoso has a requirement for providing it's staff with a secured environment to access their work application and also certain staff required access to a fully managed desktop that is goverened by policies. Contoso wants their resources to provide more control and flexibility over the computing environment. They want their resources to be highly available.

Recently contoso is experiencing a huge rise in supporting their remote working staff, essentially staff that is working from home and because Contoso does not have a capacity to provide such huge number of managed physical computers and the Board of Directors has been unwilling to increase capital expenditures for new equipment. Contoso has been evaluating the value of the public cloud and views Microsoft Azure as an excellent option to maintain availability and increase scalability of resources to the organization. Contoso have decided to use Azure virtual desktop which is the cloud Desktop-as-a-Service (DaaS) offered by Microsoft as part of Azure and Microsoft 365.

They need your help to configure the infrastructure and deploy a solution. You need to choose the right approach to set up and deploy the solution on Azure. However, you will be doing it in phases as the development and testing progress.
 
## **Lab Context**

In this hands-on lab, you will implement an Azure Virtual Desktop (formerly Windows Virtual Desktop) Infrastructure and learn how-to setup a working AVD environment end-to-end in a typical Enterprise model. At the end of the lab, attendees will have deployed an Azure Active Directory Tenant that is running on Azure. Azure Active Directory (Azure AD) is Microsoft’s enterprise cloud-based identity and access management (IAM) solution.

You will also deploy the Azure infrastructure for the Azure Virtual Desktop Tenant(s), Host pool which is  a collection of one or more identical virtual machines (VMs), also known as session hosts within Azure Virtual Desktop environments. A default Application group will be created which is a collection of remote applications that you can present to a user or group of users. You will publish desktops and remote apps with the help of application group. You will be configuring FSLogix for user profile solution which stores a complete user profile in a single container. You will be configurig MSIX app attach to publish the apps securely as a package. You will be configuring a specific version of Microsoft Teams which is meant for AVD inorder to improve commmunication and acheive A/V experience. Finally, you will configure monitoring and security for the Azure Virtual Desktop infrastructure.

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
 
In this lab, you will be creating an Azure File share and enabling SMB access via Active Directory authentication. Azure Files is a platform service (PaaS) and is one of the recommended solutions for hosting FSLogix containers for AVD users. At the end of this exercise, you will have the following components:

- A new storage account in your Azure subscription.
- A new Azure file share for your FSLogix profile containers.
- AD authentication enabled for your Azure storage account.
- Permissions applied for user access to the file share.
    
## **Lab 7: Load Balancing methods**
    
In this lab we will be seeing the user allocation among session host between both Depth first anf Breadth first approach.

## **Lab 8: Cost Optimizations**

In this lab, We'll be enabling the Start Virtual Machine (VM) on Connect feature in host pool which lets you save costs by allowing users to turn on their VMs only when they need them.

## **Lab 9: Use MEM to enforce MFA while using AVD**

In this lab we will setup Multi-Factor Authentication (MFA) and will be Creating Conditional Access Policy.

## **Lab 10: MS Teams Optimized Experience**

In this lab we will be configuring Session host for implementing MS Teams and configure hostpool for teams requirements. Later we will be accessing MS Teams using Remote Desktop Application

## **Lab 11: MSIX App Attach**

In this lab, first we will be configuring AVD for MSIX App Attach then later will be creating MSIX Package in AVD environment.

## **Lab 2 (B): Monitoring using Azure Monitor for AVD**

In this lab we will be looking at the informatgion collected by Azure Monitoring with the help of log analytics workspace created earlier.

Click on the **Next** button present in the bottom-right corner of this lab guide.
