# Microsoft Defender (Tenant) Settings Baseline

Hi! In this file we will provide you with some Real World Best-Practices regarding Microsoft Defender (Tenant) Settings which we (ITCowboys) have developed over the past years while implementing the following Subjects:

- Microsoft Defender XDR Settings
- Endpoints Settings
- Identities Settings
- Cloud Apps Settings
- Actions & Submissions

Per Subject we will provide you with a brief description, Recommended Values and an how to with a Step-by-Step Guide or Code Examples! Our Recommendations are based on Microsoft Best-Practices, Real-World Best Practices and Frameworks such as the CIS Microsoft 365 Benchmarks. 

So buckle up and get ready for a ride into the deep of Microsoft Defender for Office 365 with the ITCowboys!

## Microsoft Defender XDR Settings

Microsoft Defender XDR (Extended Detection and Response) represents a unified security solution that extends beyond traditional endpoint protection, integrating various Microsoft Defender services to offer comprehensive protection across domains including email, applications, endpoints, identities, and cloud environments. This integration facilitates a coordinated defense against sophisticated cyber threats, leveraging the breadth and depth of security analytics and threat intelligence available across the Microsoft ecosystem. The settings within the Microsoft Defender Portal are central to configuring and managing this extended protection. Here's a brief technical summary of the key components and functionalities of Microsoft Defender XDR settings within the Microsoft Defender Portal:

**Integrated Security Components**

- **Microsoft Defender for Endpoint**: Provides advanced threat protection, post-breach detection, automated investigation, and response capabilities for endpoints.
- **Microsoft Defender for Office 365**: Protects against advanced threats in email and collaboration tools through features like Safe Links and Safe Attachments.
- **Microsoft Defender for Identity**: Identifies and investigates advanced threats, compromised identities, and malicious insider actions directed at your organization.
- **Microsoft Defender for Cloud Apps**: A CASB (Cloud Access Security Broker) that gives deeper visibility, comprehensive controls, and improved protection for your cloud applications.
- **Microsoft Defender for Cloud**: Offers integrated security management and threat protection for workloads running in Azure, on-premises, and in other clouds

Microsoft Defender XDR extends beyond just endpoint security, offering a comprehensive extended detection and response (XDR) solution. While it doesn't have dedicated settings like other Defender components, the Microsoft Defender portal ()serves as the central hub for managing settings related to XDR functionalities.

**Recommended Values**

In the Microsoft Security Center -> Settings -> Microsoft Defender XDR -> Preset Security Policies we recommend the following:

![image](https://github.com/ITCowboys/Microsoft/blob/main/Microsoft%20Defender%20Tenant%20Settings%20-%20XDR%2C%20Identities%2C%20Endpoints%2C%20Devices/Source/Picture1.png)

|**Microsoft Defender XDR Settings**|**Recommendation**|**Note**|
| :- | :- | :- |
|Preview Functions|On| |
|Incidents|Admins|Set email and Rules which fill your own requirements|
|Actions|Admins|Set email and Rules which fill your own requirements|
|Threat Analytics|Admins|Set email and Rules which fill your own requirements|
|Choose which identity protection alerts will appear in the alerts and incidents pages.|On|Set incident rule under email notifications|
|Choose which MDC alerts will appear in the alerts and incidents pages.|On|Set incident rule under email notifications|

For scripts please see our “/Scripts/ITCowboysXDRRules.ps1” script 😊 Please use with cause and common knowledge!

## Endpoints Settings

Endpoint settings within the Microsoft Defender Portal are crucial for configuring and managing Microsoft Defender for Endpoint, a component of Microsoft's comprehensive security solutions. This platform is designed to help organizations prevent, detect, investigate, and respond to advanced threats, data breaches, and cybersecurity incidents on network endpoints. Here’s a brief technical overview of the Endpoint settings available in the Microsoft Defender Portal:

**Key Features and Functionalities**

- **Threat & Vulnerability Management**: Provides real-time insights into the security posture of endpoints, identifying vulnerabilities and misconfigurations, and offering recommendations for remediation.
- **Attack Surface Reduction (ASR)**: A set of capabilities designed to prevent attacks from happening, including rules that reduce the areas of the system attackers can exploit. It includes settings to control executable files, script use, and email attachment access.
- **Antivirus & Antimalware Protection**: Configurable settings for Microsoft Defender Antivirus, including cloud-delivered protection, sample submission settings, and exclusions for files and processes from scans.
- **Endpoint Detection and Response (EDR)**: Settings to manage the level of automated response, the collection of investigation data, and advanced features like live response and full attack surface reduction.
- **Account Protection**: Enhances security for user accounts by identifying and mitigating risks associated with credentials and authentication mechanisms.
- **Device Control**: Policies to manage the use of removable storage devices and other peripherals to prevent data leakage and malware infections.
- **Firewall & Network Protection**: Configurations to manage the Windows Defender Firewall, including rules for inbound and outbound connections, and network protection against online threats.

**Recommendations**

In the Microsoft Security Center -> Settings -> Endpoints we recommend the following:

![image](https://github.com/ITCowboys/Microsoft/blob/main/Microsoft%20Defender%20Tenant%20Settings%20-%20XDR%2C%20Identities%2C%20Endpoints%2C%20Devices/Source/Picture2.png)

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

For scripts please see our “/Scripts/ITCowboysXDREndpointSettings.ps1” script 😊 Please use with cause and common knowledge!



# Identities Settings

Identity Security settings within the Microsoft Defender Portal are a crucial aspect of Microsoft's comprehensive cybersecurity framework, focusing on protecting user identities and ensuring secure access to resources across an organization's environment. This area primarily leverages Microsoft Defender for Identity, which is designed to safeguard against identity-based threats and attacks, such as those involving compromised credentials or insider threats. Here's a brief technical summary of the Identity Security features and settings within the Microsoft Defender Portal:

**Key Components**

- **Microsoft Defender for Identity**: A cloud-based security solution specifically aimed at detecting and investigating advanced threats, compromised identities, and malicious insider actions across an organization's Microsoft and hybrid environments.
- **User and Entity Behavior Analytics (UEBA)**: Utilizes advanced analytics to understand normal user behavior and detect anomalies indicative of threats or compromised identities, enabling proactive threat mitigation.
- **Advanced Threat Detection**: Leverages machine learning and heuristics to identify suspicious activities and signs of attack, such as lateral movement, privilege escalation, and other tactics used by attackers.
- **Automated Investigation and Response (AIR)**: Offers automated response capabilities that can remediate detected threats, such as suspending compromised accounts or resetting user passwords, reducing the time and effort required for incident response.

**Recommendations**

In the Microsoft Security Center -> Settings -> Identities we recommend the following:

Make sure you are using Microsoft Defender for Identity, the first thing you need to do is checking if you already have a Sensor in your local AD-infrastructure deployed.

![image](https://github.com/ITCowboys/Microsoft/blob/main/Microsoft%20Defender%20Tenant%20Settings%20-%20XDR%2C%20Identities%2C%20Endpoints%2C%20Devices/Source/Picture3.png)

In order to be able to connect your on-premises environment to the Cloud please configure an Directory Service account. For more information and options please visit <https://learn.microsoft.com/en-us/defender-for-identity/deploy/directory-service-accounts> 

If you don’t have a sensor in your local AD-infrastructure please click “Add sensor”  and download the sensor. Secondly install the sensor on 1 or more Domain Controllers using the Access Key

![image](https://github.com/ITCowboys/Microsoft/blob/main/Microsoft%20Defender%20Tenant%20Settings%20-%20XDR%2C%20Identities%2C%20Endpoints%2C%20Devices/Source/Picture4.png)

![image](https://github.com/ITCowboys/Microsoft/blob/main/Microsoft%20Defender%20Tenant%20Settings%20-%20XDR%2C%20Identities%2C%20Endpoints%2C%20Devices/Source/Picture5.png)

The next step is to check if your Action Account automatically uses the sensor’s local system account

![image](https://github.com/ITCowboys/Microsoft/blob/main/Microsoft%20Defender%20Tenant%20Settings%20-%20XDR%2C%20Identities%2C%20Endpoints%2C%20Devices/Source/Picture6.png)

Make sure you Adjust the Alerts Thresholds with the following values:

![image](https://github.com/ITCowboys/Microsoft/blob/main/Microsoft%20Defender%20Tenant%20Settings%20-%20XDR%2C%20Identities%2C%20Endpoints%2C%20Devices/Source/Picture7.png)

![image](https://github.com/ITCowboys/Microsoft/blob/main/Microsoft%20Defender%20Tenant%20Settings%20-%20XDR%2C%20Identities%2C%20Endpoints%2C%20Devices/Source/Picture8.png)

Make sure you are able to receive Alerts about Health Issues:

![image](https://github.com/ITCowboys/Microsoft/blob/main/Microsoft%20Defender%20Tenant%20Settings%20-%20XDR%2C%20Identities%2C%20Endpoints%2C%20Devices/Source/Picture9.png)

Lastly make sure you are able to receive Alert Notifications

![image](https://github.com/ITCowboys/Microsoft/blob/main/Microsoft%20Defender%20Tenant%20Settings%20-%20XDR%2C%20Identities%2C%20Endpoints%2C%20Devices/Source/Picture10.png)

# Cloud Apps Settings

Cloud Apps Security settings within the Microsoft Defender Portal are centered around Microsoft Defender for Cloud Apps, formerly known as Microsoft Cloud App Security (MCAS). This component is a Cloud Access Security Broker (CASB) that operates as a critical part of Microsoft's comprehensive cybersecurity suite, providing organizations with deep visibility, strong data control, and enhanced threat protection for their cloud applications and services. Here's a brief technical summary of Cloud Apps Security features and settings accessible through the Microsoft Defender Portal:

**Key Components**

- **Discovery and Risk Assessment**: Utilizes traffic logs from your network appliances to discover and continuously monitor cloud applications used within the organization, assessing them for risk and compliance with corporate policies.
- **Data Protection and Loss Prevention**: Offers tools for controlling and securing sensitive information stored in and shared across cloud applications, including data classification, encryption, and access control policies.
- **Threat Protection**: Leverages advanced analytics and machine learning to detect unusual behavior and potential threats across cloud applications, such as compromised accounts or insider threats.
- **Conditional Access App Control**: Uses reverse proxy architecture to provide real-time session and access control to cloud applications, enabling granular enforcement of policies based on user activities and risk levels.

**Recommendations** 

In the Microsoft Security Center -> Settings -> Cloud Apps we recommend the following:

Make sure you get notifications from Medium or above from Microsoft Defender for Cloud Apps

![image](https://github.com/ITCowboys/Microsoft/blob/main/Microsoft%20Defender%20Tenant%20Settings%20-%20XDR%2C%20Identities%2C%20Endpoints%2C%20Devices/Source/Picture11.png)

Enforce App Access for Microsoft Defender for Endpoint

![image](https://github.com/ITCowboys/Microsoft/blob/main/Microsoft%20Defender%20Tenant%20Settings%20-%20XDR%2C%20Identities%2C%20Endpoints%2C%20Devices/Source/Picture12.png)

Connect Microsoft Azure to Microsoft Defender for Cloud Apps

![image](https://github.com/ITCowboys/Microsoft/blob/main/Microsoft%20Defender%20Tenant%20Settings%20-%20XDR%2C%20Identities%2C%20Endpoints%2C%20Devices/Source/Picture13.png)

Edit Settings for the Microsoft 365 Connector

![image](https://github.com/ITCowboys/Microsoft/blob/main/Microsoft%20Defender%20Tenant%20Settings%20-%20XDR%2C%20Identities%2C%20Endpoints%2C%20Devices/Source/Picture14.png)

Make sure all are enabled

![image](https://github.com/ITCowboys/Microsoft/blob/main/Microsoft%20Defender%20Tenant%20Settings%20-%20XDR%2C%20Identities%2C%20Endpoints%2C%20Devices/Source/Picture15.png)

Make sure you enable the settings below for Microsoft Information Protection integration

![image](https://github.com/ITCowboys/Microsoft/blob/main/Microsoft%20Defender%20Tenant%20Settings%20-%20XDR%2C%20Identities%2C%20Endpoints%2C%20Devices/Source/Picture16.png)

Enable File Monitoring

![image](https://github.com/ITCowboys/Microsoft/blob/main/Microsoft%20Defender%20Tenant%20Settings%20-%20XDR%2C%20Identities%2C%20Endpoints%2C%20Devices/Source/Picture17.png)

# Actions & Submissions

Actions & Submissions within the Microsoft Defender Portal encompass a set of functionalities designed to enhance organizational security through the proactive management of potential threats and the submission of suspicious entities for analysis. This feature set enables security teams to take direct action on threats, submit files, URLs, emails, and other entities for examination, and receive expert analysis and feedback from Microsoft's security services. Here's a brief technical summary of the Actions & Submissions features and their significance within the Microsoft Defender Portal:

**Key Components**

- **Threat Submission**: Allows users to submit suspicious files, emails, URLs, and other content directly to Microsoft for analysis. This aids in the identification of new threats and enhances the overall security intelligence of Microsoft's security products.
- **Automated Investigation and Response (AIR)**: Upon submission, many of these items can trigger automated investigations, leveraging AI and machine learning to quickly assess and respond to potential threats, minimizing the time to remediation.
- **Alerts and Actions Management**: Users can manage and respond to security alerts generated across Microsoft Defender services. This includes viewing detailed alert information, taking response actions, and tracking the status of investigations.

**Recommendations**

In the Microsoft Security Center -> Actions & Submissions -> User Reported Settings the following:

![image](https://github.com/ITCowboys/Microsoft/blob/main/Microsoft%20Defender%20Tenant%20Settings%20-%20XDR%2C%20Identities%2C%20Endpoints%2C%20Devices/Source/Picture18.png)

![image](https://github.com/ITCowboys/Microsoft/blob/main/Microsoft%20Defender%20Tenant%20Settings%20-%20XDR%2C%20Identities%2C%20Endpoints%2C%20Devices/Source/Picture19.png)

|**Actions & Submissions Settings**|**Recommendation**|**Notes**|
| :- | :- | :- |
|Monitor reported messages in Outlook|Yes|https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/submissions-user-reported-messages-custom-mailbox?view=o365-worldwide|
|Use the built-in Report button in Outlook|Yes|https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/submissions-user-reported-messages-custom-mailbox?view=o365-worldwide|
|Ask the user to confirm before reporting|Yes|https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/submissions-user-reported-messages-custom-mailbox?view=o365-worldwide|
|Show a success message after the message is reported|Yes|https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/submissions-user-reported-messages-custom-mailbox?view=o365-worldwide|
|Monitor reported messages in Teams|Yes|https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/submissions-user-reported-messages-custom-mailbox?view=o365-worldwide|
|Send Reported messaged to:|Yes|Set email|
|Add an Exchange Online mailbox to send reported messages to|Yes|Set email|
|Check for custom Tags|None| |
|Priority Account Protection|On|https://learn.microsoft.com/en-us/microsoft-365/admin/setup/priority-accounts?view=o365-worldwide|
|Check Members|Management|Add Management en C-Level to Priority Users|
|Zero-hour auto purge (ZAP)|On| |
|Exclude these participants|None| |

# Summary

The ITCowboys thank you for taking your time to read and hopefully deploy the recommendations from this document within your own Environment! We aim to inspire, help and educate people and organizations to get the most out of the Microsoft Cloud.

Please feel free to provide us with feedback or success stories related to this document. Now you have a great base  deployment of Microsoft Defender (Tenant) Settings 😊

Please check our Website ([www.itcowboys.nl](http://www.itcowboys.nl)) and Github Repo to keep up to date with our contributions!

Thanks for the ride together with the ITCowboys: Jordy Herber and Unknown User


