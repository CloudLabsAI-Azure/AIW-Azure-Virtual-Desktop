# **Pre-requisites to deploy Windows Virtual Desktop**

- To deploy Windows Virtual Desktop environment, we need a Windows Active Directory (for example: contoso.com). This can be achieved using one of the following ways:

    1. Azure Active Directory Domain Services(AADDS)
    2. Windows Active Directory

- In this lab, we have used AADDS and it is pre-provisioned. 

  ![ws name.](media/w30.png)


- The domain name will be the suffix of your lab user account (for example: If your lab user account is ***odl_user_189588@azurehol1057.onmicrosoft.com***, the domain will be ***azurehol1057.onmicrosoft.com***.) 

- When you provision Azure ADDS, it creates a group named "AAD DC Administrators" in Azure Active Directory. Members of this group are allowed to be able to join WVD Sessions Hosts to Azure ADDS.  Your lab account is already a member of this group. 



Click on the **Next** button present in the bottom-right corner of this lab guide.  
