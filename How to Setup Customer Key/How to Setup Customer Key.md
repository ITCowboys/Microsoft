# How to Setup Customer Key

## What is Customer Key

Your Microsoft 365 data is always encrypted at rest in the Microsoft 365 service with BitLocker and DKM. Customer Key provides extra protection against viewing of data by unauthorized systems or personnel, and complements BitLocker disk encryption and SSE in Microsoft data centers. Service encryption isn't meant to prevent Microsoft personnel from accessing your data. Instead, Customer Key helps you meet regulatory or compliance obligations for controlling root keys. You explicitly authorize Microsoft 365 services to use your encryption keys to provide value added cloud services, such as eDiscovery, anti-malware, anti-spam, search indexing, and so on.

Customer Key is built on service encryption and lets you provide and control encryption keys. Microsoft 365 then uses these keys to encrypt your data at rest as described in the [Online Services Terms (OST)](https://www.microsoft.com/licensing/product-licensing/products.aspx). Customer Key helps you meet compliance obligations because you control the encryption keys that Microsoft 365 uses to encrypt and decrypt data.

![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Customer%20Key/Source/Image1.png)

Customer Key enhances the ability of your organization to meet the demands of compliance requirements that specify key arrangements with the cloud service provider. With Customer Key, you provide and control the root encryption keys for your Microsoft 365 data at-rest at the application level. As a result, you exercise control over your organization's keys.

**Summary:**

Service Encryption is the default way of encrypting the Platform by Microsoft

- Encryption keys are managed by Microsoft
- Microsoft had access to the encryption keys and can access your data

On top off Service Encryption you layer Customer Key

- Customer manages Encryption Keys
- Provides extra protection against unauthorized access (on the Microsoft platform)
- Microsoft cannot access your data without your consent (there is a availability key for Emergency access situations)


## What does Customer Key Encrypt?

A data encryption policy (DEP) defines the encryption hierarchy. This hierarchy is used by the service to encrypt data using each of the keys you manage and the availability key that's protected by Microsoft. You create DEPs using PowerShell cmdlets, and then assign those DEPs to encrypt application data. There are three types of DEPs supported by Customer Key, each policy type uses different cmdlets and provides coverage for a different type of data. The DEPs you can define include:

**DEP for multiple Microsoft 365 workloads** These DEPs encrypt data across multiple Microsoft 365 workloads for all users within the tenant. These workloads include:

- Windows 365 Cloud PCs
- Teams chat messages (1:1 chats, group chats, meeting chats and channel conversations)
- Teams media messages (images, code snippets, video messages, audio messages, wiki images)
- Teams call and meeting recordings stored in Teams storage
- Teams chat notifications
- Teams chat suggestions by Cortana
- Teams status messages
- Microsoft 365 interactions
- User and signal information for Exchange Online
- Exchange Online mailboxes that aren't already encrypted by mailbox DEPs
- Microsoft Purview Information Protection:
  - Exact data match (EDM) data, including data file schemas, rule packages, and the salts used to hash the sensitive data. For EDM and Microsoft Teams, the multi-workload DEP encrypts new data from the time you assign the DEP to the tenant. For Exchange Online, Customer Key encrypts all existing and new data.
  - Label configuration for sensitivity labels

Multi-workload DEPs don't encrypt the following types of data. Instead, Microsoft 365 uses other types of encryption to protect this data.

- SharePoint and OneDrive for Business data.
- Microsoft Teams files and some Teams call and meeting recordings saved in OneDrive for Business and SharePoint Online are encrypted using the SharePoint Online DEP.
- Other Microsoft 365 workloads that aren't currently supported by Customer Key such as Viva Engage and Planner.
- Teams Live Event data.

**DEPs for Exchange Online mailboxes** Mailbox DEPs provide more precise control over individual mailboxes within Exchange Online. Use mailbox DEPs to encrypt data stored in EXO mailboxes of different types such as UserMailbox, MailUser, Group, PublicFolder, and Shared mailboxes. You can have up to 50 active DEPs per tenant and assign those DEPs to individual mailboxes. You can assign one DEP to multiple mailboxes.

By default your mailboxes get encrypted using Microsoft-managed keys. When you assign a Customer Key DEP to a mailbox:

- If the mailbox is encrypted using a multi-workload DEP, the service rewraps the mailbox using the new mailbox DEP as long as a user or a system operation accesses the mailbox data.
- If the mailbox is already encrypted using Microsoft-managed keys, the service rewraps the mailbox using the new mailbox DEP as long as a user or a system operation accesses the mailbox data.
- If the mailbox isn't yet encrypted using default encryption, then the service marks the mailbox for a move. The encryption takes place once the move is complete. Mailbox moves are governed based on priorities set for all of Microsoft 365.. If the mailboxes aren't encrypted within the specified time, contact Microsoft.

**DEP for SharePoint Online and OneDrive for Business** This DEP is used to encrypt content stored in SPO and OneDrive for Business, including Microsoft Teams files stored in SPO. If you're using the multi-geo feature, you can create one DEP per geo for your organization. If you're not using the multi-geo feature, you can only create one DEP per tenant. 

## Implementing Customer Key in your Tenant

- First of all you would need to have the right license withing your tenant. Summarized you would need to have a E5 license
- You need to create two new Azure Subscriptions where you will be hosting two Azure Key Vaults
- Submit a Service Request to activate Customer Key on your tenant
  - Using a work or school account that has global administrator permissions in your organization, sign in to the [Microsoft FastTrack portal](https://fasttrack.microsoft.com/).
  - Once you're logged in, select the appropriate domain.
  - For the selected domain, choose Deploy from the top navigation bar, and review the list of available offers.
  - Choose the information card for the offer that applies to you:
    - Multiple Microsoft 365 workloads: Choose the Request encryption key help for Microsoft 365 offer.
    - Exchange Online: Choose the Request encryption key help for Exchange offer.
    - SharePoint Online, OneDrive, and Teams files: Choose the Request encryption key help for SharePoint and OneDrive for Business offer.
  - Once you've reviewed the offer details, choose Continue to step 2.
  - Fill out all applicable details and requested information on the offer form. Pay particular attention to your selections for which officers of your organization you want to authorize to approve the permanent and irreversible destruction of encryption keys and data. Once you've completed the form, choose Submit.

- Register Azure subscriptions to use a mandatory retention period
  - For your two Subscriptions run the following Powershell Command

|<p>Set-AzContext -SubscriptionId <SubscriptionId></p><p>Register-AzProviderFeature -FeatureName mandatoryRetentionPeriodEnabled -ProviderNamespace Microsoft.Resources</p><p></p>|
| :- |
- Now Contact the corresponding Microsoft alias to proceed with the process
  - For enabling Customer Key for assigning DEP to individual Exchange Online mailboxes, contact exock@microsoft.com.

  - For enabling Customer Key for assigning DEPs to encrypt SharePoint Online and OneDrive for Business content (including Teams files) for all tenant users, contact spock@microsoft.com.

  - For enabling Customer Key for assigning DEPs to encrypt content across multiple Microsoft 365 workloads (Exchange Online, Teams, Microsoft Purview Information Protection, and Windows 365 Cloud PCs) for all tenant users, contact <m365-ck@service.microsoft.com>.

- Include the following information in your email:

  Subject: Customer Key for <Your tenant's fully qualified domain name>

  Body: Include the FastTrack Request IDs and subscription IDs for each of the Customer Key services that you would like to be onboard to. These subscription IDs are the ones that you want to complete the mandatory retention period and the output of Get-AzProviderFeature for each subscription.

- The Service Level Agreement (SLA) for completion of this process is five business days once Microsoft has been notified (and verified) that you have registered your subscriptions to use a mandatory retention period.
- Once you receive notification from Microsoft that registration is complete, verify the status of your registration by running the Get-AzProviderFeature command as follows.

|Get-AzProviderFeature -ProviderNamespace Microsoft.Resources -FeatureName mandatoryRetentionPeriodEnabled|
| :- |

- Before moving on, make sure the 'RegistrationState' is set to 'Registered'.
- Create 1 Key Vault in every Subscription

- Enable Soft Delete
- Enable Purge Protection
- Set the right permissions for Users
  - Example: Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 -UserPrincipalName alice@contoso.com -PermissionsToKeys create,import,list,get,backup,restore
- Set the right permissions for Microsoft Services
  - Give the following Applications the; wrapkey, unwrapkey and get permission to the following services using the “*Key Vault Crypto Service Encryption User* ” Role
    - Office 365 Exchange Online
    - Office 365 SharePoint Online
    - M365DataAtRestEncryption
- Add a Key for EXO, SPO and M365DataAtRest in every Key Vault
  - You can do this directly from the Azure Key Vault
  - Customer Key supports RSA Key lengths up to 4096
- Verify that there is no expiration date~
  - Command: Get-AzKeyVaultKey -VaultName <vault name>
- Check the recovery level of your keys
  - Command: (Get-AzKeyVaultKey -VaultName <vault name> -Name <key name>).Attributes
  - Expect a result like: Recoverable+ProtectedSubscription
- Backup the Key Vault
  - Use Backup-AzKeyVaultKey
  - Example:  Backup-AzKeyVaultKey -VaultName 'MyKeyVault' -Name 'MyKey' -OutputFile 'C:\Backup.blob'
- Obtain the URI for each Azure Kye Vault Key
  - Example: (Get-AzKeyVaultKey -VaultName <vault name>).Id
- Now we are ready to create DEPs, we will start wil a Multiple Workload DEP
- Create a DEP for use with multiple workloads for all tenant users
  - Connect ot Exchange Online Powershell
  - Create and assign a DEP:
    - Command: New-M365DataAtRestEncryptionPolicy -Name <PolicyName> -AzureKeyIDs <KeyVaultURI1, KeyVaultURI2> [-Description <String>]
      - PolicyName is the name you want to use for the policy. Names can't contain spaces. For example, Contoso\_Global.
      - KeyVaultURI1 is the URI for the first key in the policy. For example, "https://contosoWestUSvault1.vault.azure.net/keys/Key\_01".
      - KeyVaultURI2 is the URI for the second key in the policy. For example, "https://contosoCentralUSvault1.vault.azure.net/keys/Key\_02". Separate the two URIs by a comma and a space.
      - Policy Description is a user-friendly description of the policy that helps you remember what the policy is for. You can include spaces in the description. For example, "Root policy for multiple workloads for all users in the tenant."
    - Assign the Multi-workload Policy
      - Command:  Set-M365DataAtRestEncryptionPolicyAssignment -DataEncryptionPolicy <PolicyName or ID>
- Now the First DEP is in place! Now let’s continue with DEP for Exchange Online Mailboxes
  - Connect to Exchange Online Powershell
  - Create and Assign a DEP
    - Command: New-DataEncryptionPolicy -Name <PolicyName> -Description "Policy Description" -AzureKeyIDs <KeyVaultURI1>, <KeyVaultURI2>
    - Get-Mailbox | Set-Mailbox -DataEncryptionPolicy "<PolicyName>"
    - **You will need to add newly created mailboxes to this policy, this will not go automatically**

- Alright, now let’s continue with DEP to use with SharePoint Online, OneDrive for Business and Teams Files
  - Connect to SharePoint Online Powershell
  - Create and Assign a DEP
    - Command: Register-SPODataEncryptionPolicy -PrimaryKeyVaultName <PrimaryKeyVaultName> -PrimaryKeyName <PrimaryKeyName> -PrimaryKeyVersion <PrimaryKeyVersion> -SecondaryKeyVaultName <SecondaryKeyVaultName> -SecondaryKeyName <SecondaryKeyName> -SecondaryKeyVersion <SecondaryKeyVersion>
- Now we are all set! Let’s check if everything is “Green”
  - Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl IsEncrypted
  - Get-SPODataEncryptionPolicy <SPOAdminSiteUrl>
  - Get-M365DataAtRestEncryptionPolicy

Now you have successfully enabled Customer Key within your tenant!



