# Microsoft Defender for Office 365 (MDO) Baseline

Hi! In this file we will provide you with some Real World Best-Practices regarding Microsoft Defender for Office 365 (MDO) which we (ITCowboys) have developed over the past years while implementing the following Subjects:

- Preset Security Policies
- Configuration Analyzer
- Anti-Phishing
- Anti-Spam
- Anti-Malware
- Safe Attachments
- Safe Links
- Additional Settings

Per Subject we will provide you with a brief description, Recommended Values and an how to with a Step-by-Step Guide or Code Examples! Our Recommendations are based on Microsoft Best-Practices, Real-World Best Practises and Frameworks such as the CIS Microsoft 365 Benchmarks. 

So buckle up and get ready for a ride into the deep of Microsoft Defender for Office 365 with the ITCowboys!

## Preset Security Policies

Microsoft Defender for Office 365 offers Preset Security Policies as a way to streamline the configuration of security settings and improve the protection against threats like phishing, malware, and other malicious attacks targeted at an organization's Office 365 environments, including email and collaboration tools. These preset policies are designed to simplify the administration of security measures by providing predefined security settings that can be quickly applied to an organization's environment. Here's a brief technical summary of Preset Security Policies within Microsoft Defender for Office 365:

**Key Components**

- **Standard Protection**: This preset is designed for general protection and is aimed at organizations needing a balance between security and usability. It provides a solid level of security against common threats without significantly impacting user productivity.
- **Strict Protection**: Aimed at higher-risk environments, this preset offers more stringent security measures. It is designed for organizations that are more likely to be targeted by attacks or those that handle sensitive information. The strict preset applies more aggressive settings to ensure maximum protection at the cost of potential false positives and a slight impact on usability.

**Recommended Values**

In the Microsoft Security Center -> Email & Collaboration -> Policies -> Preset Security Policies we recommend the following:

- Turn of Standard and Strict Protection
- Exclude your domains from the Built-in Protection

![image](https://github.com/ITCowboys/Microsoft/Source/Picture1.png)


Description automatically generated](Aspose.Words.afafb00d-3be9-4b3c-83da-12720c2c65a8.001.png)

Since we are going to create our own Policies within Microsoft Defender for Office 365 we don’t need the Standard, Strict or Built-in Policies to conflict with your custom ones Based on Best Practices 😊

With Powershell you can view the individual security policies for the Built-in protection preset security policy, run this command:

Get-ATPBuiltInProtectionRule

For more Powershell examples please visit: <https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/preset-security-policies?view=o365-worldwide> 

## Configuration Analyzer

Microsoft Defender for Office 365, formerly known as Office 365 Advanced Threat Protection, includes a feature called Configuration Analyzer. This tool is designed to help organizations ensure their Microsoft Defender for Office 365 settings are configured optimally to protect against threats. Here's a brief technical summary of Configuration Analyzer:

**Purpose**

The Configuration Analyzer is intended to help IT administrators and security professionals evaluate and improve their security posture by analyzing the current configuration settings of Microsoft Defender for Office 365 against Microsoft's recommended best practices.

**Key Features**

- **Comparison Against Best Practices:** It compares the organization's current Defender for Office 365 configuration settings against Microsoft's recommended best practices.
- **Security Recommendations:** Provides actionable recommendations for adjusting configurations that are not aligned with best practices, potentially improving the organization’s security posture.
- **Customization:** Recognizes that not all recommendations can be universally applied, allowing for exceptions based on the organization's specific needs and risk tolerance.
- **Reporting:** Offers detailed reports that outline current configurations, how they differ from recommended settings, and the potential impact of aligning with those recommendations.
- **Continuous Improvement:** Encourages an iterative approach to security posture improvement by regularly reviewing and updating configurations as new threats emerge and best practices evolve.

**Recommendations**

We highly recommend that you know of the existence and capacities of the Configuration Analyzer withing Microsoft Defender for Office 365. Next to the Configuration Analyzer there is a Powershell Module called ORCA. ORCA is a module that scan’s you Microsoft Defender for Office 365 policies and gives you (a little more detailed) information where you are able to improve.

We don’t recommend using the Configuration Analyzer or ORCA scan at this but it will come in handy in de future when you have deployed your own Best-Practices and Configuration within Microsoft Defender for Office 365. With this overview you are able to get insight into configuration drifts and changes. Is is a great addition to your documentation 😊

![A screenshot of a computer

Description automatically generated](Aspose.Words.afafb00d-3be9-4b3c-83da-12720c2c65a8.002.png)

## Anti-Phishing

Anti-Phishing in Microsoft Defender for Office 365 is a comprehensive security feature designed to detect, investigate, and respond to phishing threats targeting organizations. This feature is part of Microsoft Defender for Office 365's  suite of tools aimed at protecting against sophisticated attacks through email, collaboration tools, and more. Here's a brief technical summary of its key components and functionalities:

**Detection**

- **Machine Learning Algorithms**: Utilizes advanced machine learning models to analyze email patterns, sender reputation, and content to identify potential phishing threats.
- **Impersonation Detection**: Checks for emails that impersonate trusted entities or internal users, leveraging algorithms to spot slight variations in sender addresses or domains that might deceive recipients.
- **Spoof Intelligence**: Identifies and blocks emails that spoof legitimate domains, with the ability to differentiate between malicious spoofing and legitimate use cases (e.g., third-party senders authorized by the domain owners).

**Investigation and Response**

- **Threat Explorer and Real-time Reports**: Provides detailed insights into detected threats, allowing security teams to investigate and respond to incidents quickly.
- **Automated Investigation and Response (AIR)**: Automates certain investigation tasks, such as examining the scope of a phishing attack, and recommends or executes response actions to mitigate threats.

**Protection Policies**

- **Anti-Phishing Policies**: Administrators can configure detailed policies to control how anti-phishing protection is applied, including actions to take when a threat is detected, such as moving emails to the junk folder or deleting them.
- **Safe Links and Safe Attachments**: These features provide additional layers of protection by scanning URLs and attachments in emails in real-time, blocking access to malicious content.

**Recommendations**

First of all, we need to make sure that de Default Anti-Phishing Policy won’t be conflicting with our Baseline Policy.

Whitin the Microsoft Security Portal -> Email & Collaboration -> Threat Policies -> Anti-Phishing Select the “Office365 AntiPhish Default (Default)” or any other Policy and make sure all the settings are disabled:

![A screenshot of a computer

Description automatically generated](Aspose.Words.afafb00d-3be9-4b3c-83da-12720c2c65a8.003.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.afafb00d-3be9-4b3c-83da-12720c2c65a8.004.png)

Based on our Knowledge and developed Best Practices we recommend the following values for configuring Anti-Phishing Policies:

|**Setting**|**Recommended Value**|
| :- | :- |
|Phishing threshold|2|
|User Impersonation protection|All Users|
|Domain impersonation protection|All Owned Domains|
|Trusted impersonated senders and domains|None|
|Mailbox Intelligence|On|
|Mailbox Intelligence for impersonations|On|
|Spoof Intelligence|On|
|If a message is detected as user impersonation|Quarantine|
|If a message is detected as domain impersonation|Quarantine|
|If Mailbox Intelligence detects an impersonated user|Quarantine|
|If the message is detected as spoof and DMARC Policy is set as p=quarantine|Quarantine|
|If the message is detected as spoof and DMARC Policy is set as p=reject|Reject the message|
|If the message is detected as spoof by spoof intelligence|Quarantine|
|First contact safety tip|On|
|User impersonation safety tip|On|
|Domain impersonation safety tip|On|
|Unusual characters safety tip|On|
|Unauthenticated senders symbol (?) for spoof|On|
|Show "via" tag|On|
|Honor DMARC record policy when the message is detected as spoof|On|

For scripts please see our “/Scripts/ÌTCowboysAntiPhishing.ps1” script 😊 Please use with cause and common knowledge!

# Anti-Spam

Microsoft Defender for Office 365, formerly known as Office 365 Advanced Threat Protection, offers comprehensive protection for enterprise and education customers against threats such as phishing, malware, and other forms of malicious content delivered via email or collaboration tools. The anti-spam capabilities within Microsoft Defender for Office 365 are part of its multi-layered defense strategy, designed to detect, block, and mitigate unsolicited email or spam. Here’s a brief technical summary of its anti-spam features:

**1. Connection Filtering**

- **IP Allow List and Block List**: Administrators can specify IP addresses that are always allowed or blocked.
- **IP Reputation Filtering**: Utilizes Microsoft’s dynamic IP reputation database to block emails from known spam sources.

**2. Content Filtering**

- **Spam and Bulk Email Detection**: Analyzes email content for typical spam characteristics using machine learning, heuristics, and content patterns.
- **Phishing Protection**: Identifies attempts at phishing by examining message properties and content for malicious intent.

**3. Policies and Rules**

- **Anti-spam Policies**: Administrators can configure and customize policies to determine the action on detected spam (e.g., delete, quarantine, mark as spam).
- **Outbound Spam Policies**: Monitors and takes action on outgoing email to prevent the organization from being a source of spam.

**4. Quarantine Management**

- Emails flagged as spam can be quarantined, allowing administrators or end-users to review and take appropriate actions, such as releasing false positives.

**Recommendations**

First of all, we need to make sure that de Default Anti-Phishing Policies won’t be conflicting with our Baseline Policy.

Whitin the Microsoft Security Portal -> Email & Collaboration -> Threat Policies -> Anti-Spam Select the “Anti-spam inbound policy  (Default)” or any other Inbound Policy and make sure all the settings are disabled:

![A screenshot of a computer

Description automatically generated](Aspose.Words.afafb00d-3be9-4b3c-83da-12720c2c65a8.005.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.afafb00d-3be9-4b3c-83da-12720c2c65a8.006.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.afafb00d-3be9-4b3c-83da-12720c2c65a8.007.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.afafb00d-3be9-4b3c-83da-12720c2c65a8.008.png)

Secondly Whitin the Microsoft Security Portal -> Email & Collaboration -> Threat Policies -> Anti-Spam Select the “Anti-spam outbound policy  (Default)” or any other outbound Policy and make sure all the settings are disabled:

![A screenshot of a computer

Description automatically generated](Aspose.Words.afafb00d-3be9-4b3c-83da-12720c2c65a8.009.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.afafb00d-3be9-4b3c-83da-12720c2c65a8.010.png)

Lastly whitin the Microsoft Security Portal -> Email & Collaboration -> Threat Policies -> Anti-Spam Select the “Connectorion Filter policy  (Default)” or any other Connection Filter Policy and make sure all the settings are blank or reviewed and legit:

![A screenshot of a computer

Description automatically generated](Aspose.Words.afafb00d-3be9-4b3c-83da-12720c2c65a8.011.png)

Based on our Knowledge and developed Best Practices we recommend the following values for configuring Anti-Spam Policies:

|**Anti-Spam Inbound Policy Setting**|**Recommendation**|
| :- | :- |
|Bulk email spam action|On|
|Bulk email threshold|5|
|URL to .biz or .info websites|On|
|Image links to remote sites|Off|
|Numeric IP address in URL|On|
|URL redirect to other port|On|
|Empty messages|On|
|JavaScript or VBScript in HTML|On|
|SPF Hard Fail|On|
|Sensitive Words|On|
|All other|On|
|Spam Message Action|Quarantine|
|Phishing message action|Quarantine|
|High Confidence Spam Action|Quarantine|
|High confidence Phishing Actoin|Quarantine|
|Bulk Message Action|Quarantine|
|Enable spam safety tips|On|
|Enable for spam messages|On|
|Enable for Phishing messages|On|
|Retain in quarantine for days|30|
|Allowed senders|0|
|Allowed domains|0|
|Blocked senders|0|
|Blocked domains|0|

|**Anti-Spam Outbound Policy Setting**|**Recommendation**|
| :- | :- |
|Restrict sending to external recipients (per hour)|500|
|Restrict sending to internal recipients (per hour)|1000|
|Maximum recipient limit per day|1000|
|Over limit action|Restrict user from sending email|
|Automatic forwarding|Block|
|Send a copy of suspicious outbound messages or message that exceed these limits to these users and groups|On|
|Notify these users and groups if a sender is blocked due to sending outbound spam|On|

|**Anti-Spam Connection Filter Policy Setting**|**Recommendation**|
| :- | :- |
|IP Allow List|None|
|IP Block List|As you desire|
|Safe list|Off|

For scripts please see our “/Scripts/ÌTCowboysAntiSpamInbound.ps1, /Scripts/ÌTCowboysAntiSpamOutbound.ps1 ” scripts 😊 Please use with cause and common knowledge!

# Anti-Malware

Microsoft Defender for Office 365, previously known as Office 365 Advanced Threat Protection (ATP), is a comprehensive cloud-based email filtering service designed to protect organizations against a variety of threats. The anti-malware capabilities within Microsoft Defender for Office 365 are a key component of its defense strategy, offering protection against malware, viruses, phishing attempts, and other malicious activities targeting enterprise communication and collaboration tools. Here's a brief technical summary of its anti-malware features:

Microsoft Defender for Office 365, previously known as Office 365 Advanced Threat Protection (ATP), is a comprehensive cloud-based email filtering service designed to protect organizations against a variety of threats. The anti-malware capabilities within Microsoft Defender for Office 365 are a key component of its defense strategy, offering protection against malware, viruses, phishing attempts, and other malicious activities targeting enterprise communication and collaboration tools. Here's a brief technical summary of its anti-malware features:

**1. Real-time Detection and Automated Response**

- **Purpose**: Enables rapid identification of and response to threats as they occur.
- **Mechanism**: Leverages the Microsoft 365 Defender portal for threat investigation and response, integrating insights from email, devices, identities, and applications to provide a comprehensive security posture.

**2. Zero-hour Auto Purge (ZAP)**

- **Purpose**: Removes malicious emails from mailboxes after they've been delivered if they're later found to be dangerous.
- **Mechanism**: Continuously monitors updates to threat intelligence and can retroactively delete or quarantine emails if new threats are detected after delivery.

**Recommendations**

First of all, we need to make sure that de Default Anti-Malware Policies won’t be conflicting with our Baseline Policy.

Whitin the Microsoft Security Portal -> Email & Collaboration -> Threat Policies -> Anti-Malware Select the “Default (Default)” or any other Anti-Malware Policy and make sure all the settings are disabled:

![A screenshot of a computer

Description automatically generated](Aspose.Words.afafb00d-3be9-4b3c-83da-12720c2c65a8.012.png)

Based on our Knowledge and developed Best Practices we recommend the following values for configuring Anti-Malware Policies:

|**Anti-Malware Policy Setting**|**Recommendations**|
| :- | :- |
|Included Domains|All owned Domains|
|Enable the common attachments filter|Yes|
|Customize file types|Yes|
|When these file types are found|Quarantine|
|Enable zero-hour auto purge for malware (Recommended)|On|
|Notify an admin about undelivered messages from internal senders|On|
|Notify an admin about undelivered messages from external senders|On|
|Customize notifications|Off|
|Quarantine policy|AdminOnlyAccess|

For scripts please see our “/Scripts/ÌTCowboysAntiMalware.ps1” script 😊 Please use with cause and common knowledge!

# Safe-Attachments

Safe Attachments is a feature within Microsoft Defender for Office 365 designed to protect users from malicious email attachments, a common vector for malware and sophisticated cyber attacks. This feature is part of Microsoft's comprehensive approach to email and collaboration security, aimed at preventing malicious content from compromising users' devices and networks. Here's a brief technical summary of the Safe Attachments feature:

**Key Features and Mechanisms**

- **Dynamic Delivery**: Allows recipients to read and interact with the email immediately while the attachment is being scanned. This feature helps maintain productivity by not delaying email delivery, providing a placeholder in the attachment's place until the scan is complete.
- **Detonation Chambers**: Safe Attachments uses a technique called "detonation" to analyze attachments in a secure, virtual environment. This process executes the attachment in a sandbox to observe its behavior for signs of malicious activity without risking the user's actual device or network.
- **Machine Learning and Heuristics**: Employs advanced machine learning algorithms and heuristic rules to detect new and sophisticated malware that may not be recognized by traditional signature-based detection methods.
- **Comprehensive File Analysis**: The feature is capable of analyzing a wide range of file types, including documents, scripts, and executable files, for malicious content or behavior.
- **Integration with Microsoft 365**: Safe Attachments is deeply integrated with other Microsoft 365 services, including SharePoint, OneDrive, and Microsoft Teams, providing a unified security posture across Microsoft's cloud services.

**Benefits**

- **Enhanced Security**: Offers robust protection against sophisticated malware and zero-day attacks delivered via email attachments.
- **Minimal Impact on Productivity**: With features like Dynamic Delivery, users can continue working without waiting for attachment scans to complete.
- **Seamless Integration**: Works across email and Microsoft's cloud storage and collaboration platforms, ensuring comprehensive coverage without the need for additional third-party tools.

Safe Attachments in Microsoft Defender for Office 365 represents a critical component in Microsoft's defense-in-depth strategy, leveraging advanced technologies to protect organizations from the evolving landscape of email-based threats.

**Recommendations**

First of all, we need to make sure that de Default Safe Attachment Policies won’t be conflicting with our Baseline Policy.

Whitin the Microsoft Security Portal -> Email & Collaboration -> Threat Policies -> Safe Attachments Select the “Built-in protection (Default)” or any other Safe Attachments Policy and make sure all the owned domains are excluded:

![A screenshot of a computer

Description automatically generated](Aspose.Words.afafb00d-3be9-4b3c-83da-12720c2c65a8.013.png)

Based on our Knowledge and developed Best Practices we recommend the following values for configuring Safe Attachment Policies:

|**Safe Attachments Global Settings**|**Recommendations**|
| :- | :- |
|Turn on Defender for Office 365 for SharePoint, OneDrive, and Microsoft Teams|Yes|
|Turn on Safe Documents for Office clients. Only available with *Microsoft 365 E5* or *Microsoft 365 E5 Security* license|Yes|
|Allow people to click through Protected View even if Safe Documents identified the file as malicious|Off|

|**Safe Attachments Policy Setting**|**Recommendations**|
| :- | :- |
|Included Domains|Owned Domains|
|Safe Attachments detection response:|Block|
|Redirect attachments:|Enabled|
|Quarantine policy|AdminOnlyAccess|

For scripts please see our “/Scripts/ÌTCowboysSafeAttachments.ps1” script 😊 Please use with cause and common knowledge!


# Safe Links

Safe Links is a feature within Microsoft Defender for Office 365 designed to safeguard users from malicious hyperlinks in emails and documents, a common tactic used by attackers to distribute malware or conduct phishing campaigns. It extends the protection against advanced threats by dynamically assessing the safety of web addresses (URLs) at the time of click, irrespective of the user's environment (e.g., email, Office documents, Teams). Here's a concise technical overview of the Safe Links feature:

**Key Features and Mechanisms**

- **URL Rewriting and Checking**: Safe Links rewrites URLs found in emails and Office documents. When a user clicks on a rewritten URL, Safe Links checks the URL in real-time against Microsoft's database of known malicious webpages before allowing access, effectively intercepting attempts to visit dangerous sites.
- **Time-of-Click Verification**: Performs real-time verification of websites at the moment a link is clicked. This approach ensures that even if a website was deemed safe at the time the email was received but has since been compromised, users are still protected against the newly identified threat.
- **Customizable Protection Policies**: Administrators can tailor Safe Links policies to meet the specific needs of their organization. This includes determining which URLs to rewrite, applying policies to specific users or groups, and deciding whether to allow users to bypass warnings for specific links.
- **Integration with Microsoft 365**: Safe Links is seamlessly integrated across Microsoft 365 applications, including SharePoint, OneDrive, and Microsoft Teams, offering comprehensive protection across Microsoft's ecosystem.

**Benefits**

- **Proactive Threat Prevention**: By checking the safety of links at the time of click, Safe Links provides a proactive approach to preventing access to malicious sites, reducing the risk of malware infection and phishing attacks.
- **Adaptable Security**: The real-time nature of Safe Links ensures that protection adapts to the rapidly changing threat landscape, offering defense against newly emerging threats.
- **User Education and Awareness**: Safe Links can serve as an educational tool by providing warnings to users about the dangers of malicious websites, helping to raise awareness and foster safer browsing habits.

Safe Links in Microsoft Defender for Office 365 plays a vital role in the broader security strategy of Microsoft, offering a dynamic and adaptive solution to protect against the constantly evolving tactics used by cyber attackers, especially in the context of phishing and malware distribution via hyperlinks.


**Recommendations**

First of all, we need to make sure that de Default Safe Links Policies won’t be conflicting with our Baseline Policy.

Whitin the Microsoft Security Portal -> Email & Collaboration -> Threat Policies -> Safe Links Select the “Built-in protection (Default)” or any other Safe Links Policy and make sure all the owned domains are excluded:

![A screenshot of a computer

Description automatically generated](Aspose.Words.afafb00d-3be9-4b3c-83da-12720c2c65a8.014.png)

Based on our Knowledge and developed Best Practices we recommend the following values for configuring Safe Links Policies:

|**Safe Links Policy Settings**|**Recommendations**|
| :- | :- |
|Included Domains|Owned Domains|
|Protection Settings: Email|On|
|Apply Safe Links to email messages sent within the organization|On|
|Apply real-time URL scanning for suspicious links and links that point to files|On|
|Wait for URL scanning to complete before delivering the message|On|
|Do not rewrite URLs, do checks via Safe Links API only.|Off|
|Do not rewrite the following URLs in email (0)|https://\*.microsoft.com https://\*.azure.com|
|Protection Settings: Teams|On|
|Protection Settings: Office 365 Apps|On|
|Track User clicks|On|
|Let users click through to the original URL|Off|
|Display the organization branding on notification and warning pages|On|
|Use custom notification text|Off|

For scripts please see our “/Scripts/ÌTCowboysSafeLinks.ps1” script 😊 Please use with cause and common knowledge!

# Additional Settings

Next to the main Products within Microsoft Defender for Office 365 are some smaller settings which we recommend checking and aligning with our best practices.

**Tenant Allow/Block List**

Within the Microsoft Security Portal -> Email & Collaboration -> Threat Policies -> Tenant Allow/Block List check for Allowed Domains & Addresses and Spoofed Senders:


![A screenshot of a computer

Description automatically generated](Aspose.Words.afafb00d-3be9-4b3c-83da-12720c2c65a8.015.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.afafb00d-3be9-4b3c-83da-12720c2c65a8.016.png)

**Recommendation:**

Don’t whitelist Domains & Senders and Spoofed Addresses

**Email Authentication Settings**

Within the Microsoft Security Portal -> Email & Collaboration -> Threat Policies -> Email Authentication Settings and check your DKIM configuration:

![A screenshot of a computer

Description automatically generated](Aspose.Words.afafb00d-3be9-4b3c-83da-12720c2c65a8.017.png)

**Recommendation**

If DKIM is not enabled please enable as soon as possible!

**Quarantine Policy**

Within the Microsoft Security Portal -> Email & Collaboration -> Threat Policies -> Quarantine Policy and check your Global Settings:

![A screenshot of a computer

Description automatically generated](Aspose.Words.afafb00d-3be9-4b3c-83da-12720c2c65a8.018.png)

Make sure your Quarantine Policies have the default Values:

![A screenshot of a computer

Description automatically generated](Aspose.Words.afafb00d-3be9-4b3c-83da-12720c2c65a8.019.png)

**Recommendations:**

Make sure you have the default Quarantine Policy Settings and Changed the Quarantine Notification to within 4 hours.

# Summary

The ITCowboys thank you for taking your time to read and hopefully deploy the recommendations from this document within your own Environment! We aim to inspire, help and educate people and organizations zo get the most out of the Microsoft Cloud.

Please feel free to provide us with feedback or success stories related to this document. Now you have a great deployment of Microsoft Defender for Office 365 😊

Please check our Website ([www.itcowboys.nl](http://www.itcowboys.nl)) and Github Repo to keep up to date with our contributions!

Thanks for the ride together with the ITCowboys: Jordy Herber and Paul Erlings


