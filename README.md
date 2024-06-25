# AD-and-Azure-AD-Synchronization-Project
## Description
* This Hybrid Identity Integration Project is aimed to bridge the gap between our on-premises Active Directory (AD) and Azure Active Directory (Azure AD), creating a unified and seamless identity management system. This initiative was crucial for enhancing security, streamlining user access, and supporting the organization's transition to a hybrid cloud environment.
* Azure AD is a cloud-based multi-tenant directory and identity service that provides identity and access management capabilities in the cloud.

<img src="https://github.com/StarksRepo/AD-and-Azure-AD-Synchronization-Project/assets/155681117/c11e8901-c905-430a-ba72-ffaa2e4520da)" width=500>

## Utilities Used
* Windows Server 2019
* Active Directory
* Azure - Tier 1 Subscripiton

## Azure AD / Entra ID Setup
1. In order to integrate your on-premises environment, kindly ensure the following steps are followed strictly. The user should having the following rights.
* **Local Administrator** account: The administrator who is installing Azure AD Connect and who has local administrator permissions on the machine.
* **Azure AD Global Administrator** account: used to create the Azure AD Connector account and configure Azure AD. You can view global administrator accounts in the Azure portal. **Create an Azure Global or Administrative account**: See this guide on how to add a user account and set permissions in Azure.
2. **Microsoft Azure Account (Tenant):** See [this guide](https://learn.microsoft.com/en-us/entra/fundamentals/create-new-tenant) for how to set up an Azure AD Tenant. Also when the tenant is up and running, ensure you  add a custom domain in the Azure Active directory.
3. **Download the Azure AD Connect:** After completing the above steps, we will have to download and install Azure AD Connect to synchronize your on-premises to Azure Active Directory as well.
      - Alternatively, you can navigate to Azure AD, select Azure AD Connect as shown below, and click on download Azure AD Connect.
<img src="https://github.com/StarksRepo/AD-and-Azure-AD-Synchronization-Project/assets/155681117/8106dc0b-514c-4a65-92cd-608c081f845f)" width=500>

**Note: Azure AD Connect can be installed on any server in your on-premise environment. But in my lab, I will be installing it on my Domain Controller.**

As you can she I have downloaded the Azure AD Connect to my on premise Active Directory as shown below.
<img src="https://github.com/StarksRepo/AD-and-Azure-AD-Synchronization-Project/assets/155681117/368ba282-8ea4-4a7f-9d50-f2c0de6c81ec)" width=500>
