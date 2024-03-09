# How to Setup Bring Your Own Key (BYOK)

## What is Bring Your Own Key
Bring Your Own Key (BYOK) within Microsoft Purview Information Protection is a feature that allows organizations to control and manage the encryption keys used to protect their data. BYOK is particularly significant for businesses that need to meet specific regulatory or compliance requirements regarding data sovereignty, security, and access. Here's an overview of how BYOK works within Microsoft Purview Information Protection:

1. **Key Control**: BYOK gives organizations direct control over the encryption keys used to secure their data. This means businesses can generate, manage, and own the cryptographic keys, thus having full authority over the access to their encrypted data.
1. **Azure Key Vault**: The encryption keys managed by organizations through BYOK are stored securely in Azure Key Vault, a cloud service designed to safeguard cryptographic keys and other secrets used by cloud apps and services. Azure Key Vault ensures that the keys are protected and managed with high security and compliance standards.
1. **Key Usage**: Once an organization has set up BYOK, the keys they provide are used to encrypt and decrypt data labels and protection applied by Microsoft Purview Information Protection. This includes data stored in services like SharePoint Online, OneDrive for Business, and Exchange Online, as well as files protected by Microsoft Purview across various platforms.
1. **Compliance and Regulatory Requirements**: BYOK is crucial for organizations that are subject to stringent regulatory and compliance requirements. By managing their own keys, organizations can ensure that they comply with policies that mandate control over data access and encryption, such as GDPR, HIPAA, and more.
1. **Key Lifecycle Management**: Organizations are responsible for the lifecycle management of their keys, including creation, rotation, and retirement. Microsoft provides tools and guidelines for managing these processes within Azure Key Vault, ensuring that organizations can maintain security best practices.
1. **Security and Accessibility**: While BYOK enhances control over data encryption, it also requires organizations to implement robust security measures to protect their keys. This includes access controls, auditing, and monitoring of key usage. Azure Key Vault offers features to support these security measures, ensuring that keys are accessible only to authorized users and applications.

BYOK within Microsoft Purview Information Protection offers a higher degree of control and security for organizations, enabling them to meet their specific data protection, compliance, and regulatory needs while leveraging the scalability and efficiencies of cloud services.

![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Bring%20Your%20Own%20Key%20(BYOK)/Source/Picture1.jpg)

**Summary:**

Service Encryption is the default way of encrypting the Platform by Microsoft

- Encryption keys are managed by Microsoft
- Microsoft had access to the encryption keys and can access your data

On top off Service Encryption you layer Customer Key

- Customer manages Encryption Keys
- Provides extra protection against unauthorized access (on the Microsoft platform)
- Microsoft cannot access your data without your consent (there is a availability key for Emergency access situations)

Next to the Customer Key you want to Encrypt the Data in Transit (Information Protection)

- Customer manages Encryption Keys
- Provides extra protection against unauthorized access (on the Microsoft platform)
- Microsoft does not have a recovery key!
- Microsoft cannot access your data without your consent 



## What does Bring Your Own Key Encrypt?

Bring Your Own Key Encrypts your data in Transit which is Protected with Microsoft Purview Information Protection.

- After implementing BYOK is enabled on all Information Protection Labels
- Tenant has full control over the Key and authorizes Azure Information Protection (Purview) Services to access the key
- Cloud services, such as Microsoft SharePoint or Microsoft 365
- On-premises services running Exchange and SharePoint applications that use the Azure Rights Management service via the RMS connector
- Client applications, such as Office 2019, Office 2016, and Office 2013

![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Bring%20Your%20Own%20Key%20(BYOK)/Source/Picture2.jpg)
## Implementing Bring Your Own Key in your Tenant

- First of all you would need to have the right license withing your tenant. Summarized you would need to have a E5 license
- You need to create a new Azure Subscription (or use the ones that Customer Key Uses where you will be a Azure Key Vault
- (If you are using new Subscriptions) Register Azure subscriptions to use a mandatory retention period
  - For your Subscription run the following Powershell Command

|<p>Set-AzContext -SubscriptionId <SubscriptionId></p><p>Register-AzProviderFeature -FeatureName mandatoryRetentionPeriodEnabled -ProviderNamespace Microsoft.Resources</p><p></p>|
| :- |



- Verify the status of your registration by running the Get-AzProviderFeature command as follows.

|Get-AzProviderFeature -ProviderNamespace Microsoft.Resources -FeatureName mandatoryRetentionPeriodEnabled|
| :- |

- Before moving on, make sure the 'RegistrationState' is set to 'Registered'.
- Create 1 Key Vault 

- Enable Soft Delete
- Enable Purge Protection
- Set the right permissions for Users
  - Example: Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 -UserPrincipalName alice@contoso.com -PermissionsToKeys create,import,list,get,backup,restore
- Add a Key for BYOK in Key Vault
  - You can do this directly from the Azure Key Vault
  - Customer Key supports RSA Key lengths up to 4096
- Verify that there is no expiration date~
  - Command: Get-AzKeyVaultKey -VaultName <vault name>
- Check the recovery level of your key
  - Command: (Get-AzKeyVaultKey -VaultName <vault name> -Name <key name>).Attributes
  - Expect a result like: Recoverable+ProtectedSubscription
- Backup the Key Vault
  - Use Backup-AzKeyVaultKey
  - Example:  Backup-AzKeyVaultKey -VaultName 'MyKeyVault' -Name 'MyKey' -OutputFile 'C:\Backup.blob'
- Obtain the URI for the Azure Kye Vault Key
  - Example: (Get-AzKeyVaultKey -VaultName <vault name>).Id
- Get the Key ID for the created Key:
  - The key ID is a URL that contains the name of the key vault, the keys container, the name of the key, and the key version. For example: <https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333>
- On both Key Vaults set the right permissions for the Microsoft Services
  - Add Policy from template: “**Azure Information Protection BYOK**” 
    - Selected **key permissions** include **Get**, **Decrypt**, and **Sign**
  - Give the Access to Service Principal: “**Microsoft Rights Management Services”**

- Configure Azure Information Protection to use your key:
  - Connect to the Azure Rights Management service
    - Command: Connect-AipService
  - Set your key to be used:
    - Command: Use-AipServiceKeyVaultKey -KeyVaultKeyUrl [https://contosorms-kv.vault.azure.net/keys/contosorms-byok/<key-version>](https://contosorms-kv.vault.azure.net/keys/contosorms-byok/%3ckey-version%3e)
  - Check if key is active
    - Command: Get-AipServiceKeys
  - If key is not active make it active!
    - Command: Set-AipServiceKeyProperties -KeyIdentifier "c0f102b3-02cc-4816-b732-fcee73edd0e6" -RefreshSlcName

Now you have successfully enabled Bring Your Own Key within your tenant!



