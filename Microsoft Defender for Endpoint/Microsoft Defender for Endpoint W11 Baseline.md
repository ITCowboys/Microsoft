# Microsoft Defender for Office 365 (MDO) Baseline

Hi! In this file we will provide you with some Real World Best-Practices regarding Microsoft Defender for Endpoint installed on Windows 10 and Windows 11 Machines which we (ITCowboys) have developed over the past years while implementing the following Subjects:

- Microsoft Defender for Endpoint Tenant Settings
- Antivirus
- Disk Encryption
- Windows Firewall
- Endpoint Detection and Response (EDR)
- Account Protection

Per Subject we will provide you with a brief description, Recommended Values and an how to with a Step-by-Step Guide or Code Examples! Our Recommendations are based on Microsoft Best-Practices, Real-World Best Practises and Frameworks such as the CIS Microsoft 365 Benchmarks. 

So buckle up and get ready for a ride into the deep of Microsoft Defender for Endpoint with the ITCowboys!

Microsoft Defender for Endpoint Tenant Settings

Before we start with configuring Microsoft Defender for Endpoint within Microsoft Intune we need to be sure all the right settings are enabled on the Tenant to enable certain options and configurations.

For example: one of the settings below enables you to use your Intune Configuration to target Microsoft Defender for Endpoint standalone deployments with the same policies which you save a lot of time so you don’t have to configure the policies separately!

**Recommendations**

In the Microsoft Security Center -> Settings -> Endpoints we recommend the following:

Picture1.png

|**Endpoints Settings** |**Recommendation**|**Notes**|
| :- | :- | :- |
|Restrict correlation to within scoped device groups​|Off| |
|Enable EDR in block mode|On| |
|Automatically resolve alerts|On| |
|Allow or block file|On| |
|Hide potential duplicate device records|On| |
|Custom network indicators|On| |
|Tamper protection|On| |
|Show user details|On| |
|Skype for business integration|On| |
|Microsoft Defender for Cloud Apps|On| |
|Web content filtering|On| |
|Device discovery|On| |
|Download quarantined files|On| |
|Live Response|On| |
|Live Response unsigned script execution|On| |
|Deception|On|https://derkvanderwoude.medium.com/mde-deception-fe8ba2ae8422|
|Share endpoint alerts with Microsoft Compliance Center|On| |
|Microsoft Intune connection|On| |
|Authenticated telemetry|On| |
|Preview features|On| |
|Alerts|On|Email Medium and Above|
|Vulnerabilities|On|Vulnerability (Medium and above), Exploits|
|Use MDE to enforce security configuration settings from Intune|On|<p>You can use the Intune Portal for Managing MDE settings with this turned on.</p><p></p><p>` `https://jeffreyappel.nl/managing-microsoft-defender-for-endpoint-with-the-new-security-management-feature-in-mem/</p>|

For more information on how to configure your Microsoft Defender Tenant Settings please see our other post: <https://github.com/ITCowboys/Microsoft/blob/main/Microsoft%20Defender%20Tenant%20Settings%20-%20XDR%2C%20Identities%2C%20Endpoints%2C%20Devices/Microsoft%20Defender%20(Tenant)%20Settings%20Baseline.md> 😊 Please use with cause and common knowledge!
# Antivirus Policies

Within the Microsoft Intune Admin Center -> Endpoint Security – Antivirus -> Create a new Policy

Picture2.png

Create a profile for Windows 10, Windows 11 and Windows Server and Choose the Profile Windows Defender Antivirus

Picture3.png

Fill in a name and description

Picture4.png

Now, let’s set the following Configuration Settings

Picture5.png

Picture6.png


Make sure to add exclusions that are needed for your business needs!

Picture7.png

Picture8.png

Picture9.png

Picture10.png

Picture11.png

Picture12.png

Picture13.png

Add to All Devices and create the policy!

Picture14.png

**Create a profile for Windows 10, Windows 11 and Windows Server and Choose the Profile Windows Security Experience**

**Create a name and description of your choice**

Picture15.png

Configure the following settings:

Picture16.png

Picture17.png

Picture17.png

Customize your Company Information

Picture19.png

Add to All Devices and Create Policy

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.001.png)

**Create a profile for Windows 10, Windows 11 and Windows Server and Choose the Profile Defender Update controls**

Create a name and description of your choice

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.002.png)

Configure the following settings

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.003.png)

Add to All Devices and Create Policy

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.004.png)

# Disk Encryption

Within the Microsoft Intune Admin Center -> Endpoint Security -> Disk Encryption -> Create a new Policy

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.005.png)

Fill in a name and description that fits your organization

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.006.png)

Configure the following Configuration Settings

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.007.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.008.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.009.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.010.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.011.png)

Add All Devices and Create Policy

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.012.png)

# Windows Firewall

Within the Microsoft Intune Admin Center -> Endpoint Security – Firewall -> Create a new Policy

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.013.png)

Fill in a Name and Description that fits your organization

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.014.png)

Configure the following Configuration settings

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.015.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.016.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.017.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.018.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.019.png)

**Use the same settings for Public and Private network Firewall!**

Add All Devices and Create the Policy

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.020.png)

# Endpoint Detection and Response (EDR)

Within the Microsoft Intune Admin Center -> Endpoint Security – Endpoint Detection and Response -> Create a new Policy

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.021.png)

Fill in a name and description that fits your organization

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.022.png)

Configure the following Configuration Settings

Use Connector if possible for onboarding, otherwise upload to blob storage and fill in the url!

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.023.png)

Add All Devices and create policy

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.024.png)

# Account Protection

Within the Microsoft Intune Admin Center -> Endpoint Security – Account Protection -> Create a new Policy

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.025.png)

Fill in a name and description that fits your organization

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.026.png)

Configure the following Configuration Settings

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.027.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.028.png)

Add All Devices and Create the policy

![A screenshot of a computer

Description automatically generated](Aspose.Words.2bd21043-a743-4363-9ce6-675cd4e0b401.029.png)
# Summary

The ITCowboys thank you for taking your time to read and hopefully deploy the recommendations from this document within your own Environment! We aim to inspire, help and educate people and organizations zo get the most out of the Microsoft Cloud.

Please feel free to provide us with feedback or success stories related to this document. Now you have a great deployment of Microsoft Defender for Endpoint using MS Intune 😊

Please check our Website ([www.itcowboys.nl](http://www.itcowboys.nl)) and Github Repo to keep up to date with our contributions!

Thanks for the ride together with the ITCowboys: Jordy Herber and Paul Erlings


