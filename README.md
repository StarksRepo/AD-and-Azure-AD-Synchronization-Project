# On Preme AD-and-Entra-ID-Synchronization-Project
## Description
* This Hybrid Identity Integration Project is aimed to bridge the gap between our on-premises Active Directory (AD) and Entra ID, creating a unified and seamless identity management system. This initiative was crucial for enhancing security, streamlining user access, and supporting the organization's transition to a hybrid cloud environment.
* Azure AD is a cloud-based multi-tenant directory and identity service that provides identity and access management capabilities in the cloud.

<img src="https://github.com/StarksRepo/AD-and-Azure-AD-Synchronization-Project/assets/155681117/c11e8901-c905-430a-ba72-ffaa2e4520da)" width=500>

## Utilities Used
* Windows Server 2019
* Active Directory
* Azure - Tier 1 Subscripiton

## Entra ID Setup
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

To start the installion process,
* Launch the Azure AD Connect installation
* Click on **“I agree with the License agreements and privacy rules”** 
* Click on **“Continue”** as shown below.

<img src="https://github.com/StarksRepo/AD-and-Azure-AD-Synchronization-Project/assets/155681117/cf87e47e-ba5d-4b0f-b192-3e619cdfd321)" width=500>

In the next slide, choose whether you would go with an express installation or a customised installation. 

I will be using express settings since we are only added 10 or so users and enabling password hash.

<img src="https://github.com/StarksRepo/AD-and-Azure-AD-Synchronization-Project/assets/155681117/8c460ae2-c28b-4b88-9a27-aa793831659c)" width=500>

Now you will be asked to enter that Gloab Administrator credentials you made earlier to verify the domain.

<img src="https://github.com/StarksRepo/AD-and-Azure-AD-Synchronization-Project/assets/155681117/ebe7c89e-9684-4efb-86ea-a3d4ca764b29)" width=500>

To connect to Active Directory Domain Services (Active Directory), Azure AD Connect needs the forest name and credentials of an account that has sufficient permissions
Using an existing AD account that Azure AD Connect can use to connect to the Active Directory forest during directory synchronization.
I will be using an existing account I have in AD which is the admin account, pictured below.

<img src="https://github.com/StarksRepo/AD-and-Azure-AD-Synchronization-Project/assets/155681117/04cdb4ad-d7b8-4bd5-9c56-e57b826577f4)" width=500>

After following those steps for configuration you will then install it and see the configuration is now complete and you can verify in your azure AD that the user accounts have been created.

<img src="https://github.com/StarksRepo/AD-and-Azure-AD-Synchronization-Project/assets/155681117/29df82f6-36f1-4adb-a503-b8b1b017cb2f)" width=500>

After the installation has been completed, sign out and sign in again before you use the Synchronization Service Manager or Synchronization Rule Editor.

To confirm the synchronization between your on-premises AD with Azure AD, log on to the Azure portal
* Navigate to Active Directory
* Click on Azure Active Directory
* Click on All Users

In the all users list, you will see the accounts from my on premise AD are added. Therefore, our on-premise AD is fully synchronized with Azure AD. Below I will show you;

<img src="https://github.com/StarksRepo/AD-and-Azure-AD-Synchronization-Project/assets/155681117/20dad329-7483-408c-b269-ef1c9d7ed0f6)" width=300>
<img src="https://github.com/StarksRepo/AD-and-Azure-AD-Synchronization-Project/assets/155681117/260c89e1-85e4-45e5-8040-fbf9b569c5a1)" width=300>

I decided to run a script in Powershell to have Azure AD sync with Active Directory every 30 mintues.

<img src="https://github.com/StarksRepo/AD-and-Azure-AD-Synchronization-Project/assets/155681117/af5fd022-44d7-44dd-b44d-0a3404d1bda2)" width=500>

After the script completed, I ran another one to confirm that it worked. This script will show that it is in fact syncing every 30 mins, see below..

<img src="https://github.com/StarksRepo/AD-and-Azure-AD-Synchronization-Project/assets/155681117/229a73da-f144-4a8d-a1de-da5aa9f18390)" width=500>

# Conclusion
In the end we have synced our on preme AD with Azure AD / Entra ID. They will sync together every 30 mins, so if another user is created on the on preme AD after 30 mins they will be added to Azure and from there they will have access to even more company resources if needed.
