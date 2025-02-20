# How to get started with Microsoft Sentinel

## What is Microsoft Sentinel

Microsoft Sentinel is a cloud-native Security Information and Event Management (SIEM) and Security Orchestration Automated Response (SOAR) solution provided by Microsoft. It is designed to provide enterprise-wide threat visibility, detection, response, and threat management across an organization's digital estate. Here's a short technical summary of its key features and capabilities:

1. **Data Collection and Aggregation**: Microsoft Sentinel seamlessly collects data at scale from users, devices, applications, and infrastructure, both on-premises and across multiple clouds. It supports a wide range of data sources, including Azure services, third-party cloud providers, and on-premises systems.
1. **Advanced Threat Detection**: Utilizing big data, machine learning technologies, and Microsoft's vast threat intelligence, Sentinel can detect previously undetected threats and minimize false positives. It provides customizable detection rules and templates, allowing organizations to tailor detection to their environment.
1. **Automated Incident Response**: With its SOAR capabilities, Sentinel automates responses to identified threats, streamlining the incident response process. This includes automated playbooks that can be customized to perform specific actions, such as isolating compromised devices or notifying relevant personnel.
1. **Visualization and Analysis Tools**: Sentinel offers a range of tools for visualizing and analyzing security data. This includes customizable dashboards, interactive investigation graphs, and the ability to query data using Kusto Query Language (KQL), providing deep insights into security incidents and trends.
1. **Integration and Collaboration**: It integrates with a broad ecosystem of Microsoft and third-party security products, enhancing its detection and response capabilities. Sentinel also supports collaboration across security teams, offering shared workspaces and the ability to assign and track incidents.
1. **Compliance and Security Standards**: Microsoft Sentinel is built on Azure, which complies with major regulatory standards, ensuring that data is handled securely and in compliance with global and industry-specific regulations.
1. **Cost Management and Scalability**: Sentinel offers a flexible and scalable pricing model based on the volume of data ingested for analysis, making it accessible for organizations of all sizes. It leverages Azure's scalable infrastructure to efficiently handle large volumes of data without the need for additional on-premises infrastructure.


![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture1.png)

In summary, Microsoft Sentinel provides organizations with a comprehensive and integrated SIEM and SOAR solution, offering advanced threat detection, automated incident response, and extensive data analysis capabilities. It helps businesses manage their security posture more effectively, respond to incidents rapidly, and reduce overall security risks.

## The Basics of Microsoft Sentinel

**Data Connectors**

To begin utilizing Microsoft Sentinel, the initial step involves linking your data sources to the platform.

Microsoft Sentinel offers a wide array of built-in connectors, particularly for Microsoft-based solutions, facilitating immediate and seamless real-time integration. These connectors encompass a variety of Microsoft resources, such as Microsoft Defender XDR, Microsoft Defender for Cloud, Office 365, Microsoft Defender for IoT, among others.

Additionally, it supports integration with Azure services through connectors for Microsoft Entra ID, Azure Activity, Azure Storage, Azure Key Vault, Azure Kubernetes Service, and others.

For integration with external security and application ecosystems beyond Microsoft's offerings, Microsoft Sentinel provides specialized connectors. It also allows for the connection of your data sources using common event formats, Syslog, or REST-APIs, broadening its compatibility and integration capabilities.

![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture2.png)

**Workbooks**

Once you've set up Microsoft Sentinel, you can oversee your data through its integration with Azure Monitor workbooks.

While workbooks might appear different in Microsoft Sentinel compared to Azure Monitor, understanding how to craft a workbook in Azure Monitor can still be beneficial. Microsoft Sentinel enables the creation of custom workbooks tailored to your data needs. Furthermore, it includes pre-designed workbook templates, empowering you to immediately derive valuable insights from your data upon connecting a source.

![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture3.png)

**Analytics Rules**

To streamline your workflow and decrease the volume of alerts requiring your attention, Microsoft Sentinel leverages analytics to consolidate related alerts into incidents. An incident represents a collection of related alerts that, when combined, suggest a potentially actionable threat for investigation and resolution. You can utilize the default correlation rules as provided or adapt them as a foundation for crafting personalized ones. Moreover, Microsoft Sentinel offers machine learning-based rules designed to understand your network's typical behavior patterns and identify anomalies across your resources. This analytical approach enhances threat detection by merging low fidelity alerts pertaining to various entities into cohesive, high-fidelity security incidents, thereby clarifying and prioritizing potential threats.

![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture4.png)

**Playbooks**

Simplify the orchestration of your security operations and automate routine tasks with playbooks that integrate seamlessly with Azure services and the tools you already use.

The automation and orchestration capabilities of Microsoft Sentinel are built on a highly adaptable architecture, ensuring your ability to automate at scale in response to emerging technologies and threats. Through Azure Logic Apps, Sentinel empowers you to create playbooks using an extensive collection of connectors, numbering in the hundreds, for a wide array of services and systems. These connectors facilitate the incorporation of bespoke logic into your operational workflows, covering options such as:

- ServiceNow
- Jira
- Zendesk
- HTTP requests
- Microsoft Teams
- Slack
- Microsoft Entra ID
- Microsoft Defender for Endpoint
- Microsoft Defender for Cloud Apps

For instance, if your processes involve the ServiceNow ticketing platform, you can configure Azure Logic Apps to automatically initiate ServiceNow tickets in response to specific alerts or incidents, thereby streamlining and enhancing the efficiency of your security response mechanism.

![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture5.png)

**Hunting**

Leverage the robust hunting capabilities of Microsoft Sentinel, which are grounded in the MITRE ATT&CK framework, to proactively seek out security threats within your organization's data sources before they trigger alerts. These powerful search-and-query tools empower you to tailor custom detection rules based on your investigative queries, allowing you to elevate those findings to alerts for your security incident response team.

During your threat hunting activities, you can mark significant events using bookmarks, enabling easy revisitation of noteworthy findings. Bookmarks not only facilitate personal reference but also allow for the sharing of events with team members. Moreover, you can aggregate these marked events with related incidents, assembling a comprehensive case for in-depth investigation, thereby enhancing your organization's proactive defense posture.

![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture6.png)

**Alerts vs Incidents**

In Microsoft Sentinel, "alerts" and "incidents" are closely related but serve different roles in the context of security event management and response. Here's a breakdown of the differences:

Alerts

- **Definition**: Alerts are notifications about events or conditions that might indicate a security issue or threat. They are typically generated by detection rules that analyze the data streaming into Microsoft Sentinel from various sources.
- **Granularity**: An alert is often granular, focusing on a single event or a small set of events that match specific criteria. It may indicate something suspicious, but not necessarily a confirmed threat.
- **Source**: Alerts can be triggered by a variety of sources, including analytics rules, threat intelligence, Microsoft and non-Microsoft security products, and custom detection rules.

Incidents

- **Definition**: Incidents are aggregates of one or more related alerts that, together, represent a potential security issue or confirmed threat that requires investigation and response. Incidents are designed to help security teams focus on threats that need attention by grouping related alerts into a single entity.
- **Context and Correlation**: The creation of an incident involves correlating related alerts based on factors like timing, attack techniques, threat actors, and affected assets. This correlation provides more context and helps in understanding the scope and impact of the threat.
- **Management and Investigation**: Incidents are the primary entities that security analysts interact with during the investigation and response process. They enable a structured approach to triaging, investigating, and remediating threats. Analysts can assign incidents, add tags for organization, and track the investigation status.

In summary, while alerts are the individual pieces of evidence that might indicate suspicious activity or security threats, incidents are more comprehensive entities that group related alerts to provide a clearer picture of a security issue, facilitating more effective investigation and response by security teams.

## Implementing Microsoft Sentinel in your Tenant

## Creating a Log Analytics Workspace

1. In the Azure Portal -> Search for Sentinel
1. Click on Create
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture7.png)

1. Create Log Analytics Workspace
  ![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture8.png)

1. From the Log Analytics workspaces menu in the Azure portal, select your workspace.
1. Select Usage and estimated costs in the left pane.
1. Select Data Retention at the top of the page.
1. Change retention to a retention you would like to use, for example 365 days.
1. After creation make sure you set the Entra ID Diagnostic settings to send all of the logs to this Workspace!

### Creating a Sentinel Instance

1. In the Azure Portal -> Search for Sentinel
1. Click on Create -> Add Microsoft Sentinel to a Workspace
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture9.png)

1. Click “Add”, this takes a while.

1. Finally you are presented with Microsoft Sentinel!

![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture10.png)

1. Within Sentinel, go to Settings -> Playbook Settings and give Sentinel Access to run Paybooks in your Subscription(s)
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture11.png)

1. Now we are ready to get started with Configuring Microsoft Sentinel!

### Implementing a Data Connector

Now we have an Sentinel Instance configured we are ready to create our first Data Connector! For this example I’m going to configure Microsoft Entra ID.

1. Within Sentinel go to the Content Hub and search for “Micosoft Entra ID”
1. Please click “Install” -> **Note:** you see that there are Analytics Rules, Workbooks and Playbooks in this Solution which we are configuring later!
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture12.png)

1. After installation please click “Manage”
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture13.png)

1. Now we are in the Solution settings menu, here you see how many items need configuration.
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture14.png)

1. Select (checkbox)  Microsoft Entra ID and open the Connector Page
1. Select all logs and Apply changes!
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture15.png)

1. Your Data Connector is now ready to import Data into Sentinel (this might take up to 24 hours

### Implementing a Analytics Rule

In this example we are going to use an Analytics Rule which is associated with the Microsoft Entra ID Data Connector

1. Go to the Solution Settings menu as shown in step 4 of the previous Subject.
1. Select a rule of your choice and “Create Rule”
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture16.png)

1. Now we are in the Rule Settings, you are able to change information and logic of this rule template to match your own requirements.
1. On the Incident Settings, configure if your want Sentinel to create Incidents based on this Rule
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture17.png)

1. On the Automation response tab, you can add actions as you desire. For example running a Playbook when this Alert occurs!
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture18.png)

1. Your rule is now active!

### Implementing a Playbook

In this example we are going to use an Playbook which is associated with the Microsoft Entra ID Data Connector

1. Go to the Solution Settings menu as shown in step 4 of the previous Subject.
1. Select a Playbook and Select Configuration
 ![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture19.png)
 
1. You can also do this from the Automation -> Playbook (Templates) menu:
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture20.png)

1. Configure the basic settings:
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture21.png)

1. Note the Connections that are needed, sometime the Paybooks create Managed Identities which need additional Roles!
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture22.png)

1. Create
1. Now the Logic App (Playbook) will open
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture23.png)

1. Review the Steps and Connectors
1. Give the Managed Identity the Roles or Permissions it requires!
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20get%20started%20with%20Microsoft%20Sentinel/Source/Picture24.png)

1. Now your Playbook is ready to go! Please add as an automation action to Analytics Rules 😊

### Overview of Recommended Solutions

We recommend implementing the following (Free) Solutions from the Content Hub. Please work your way down and configure every Solution after installation to keep a good overview. Every Solution may include notebooks, workbooks, hunting queries, playbooks, analytics rules or data connectors.

- Azure Activity
- Microsoft 365
- Microsoft Defender XDR
- Microsoft Defender for Cloud Apps
- Microsoft Entra ID
- Microsoft Threat Intelligence
- Analytics Health & Audit
- DNS Essentials
- Log4j Vulnerability Detection
- Network Session Essentials
- Security Threat essentials
- Sentinel SOAR Essentials
- SOC Handbook
- Workspace Usage Report
- A client made a web request to potentially harmful file
- A host is potentially running a crypto miner
- A host is potentially running a hacking took
- A host is potentially running a Powershell to send https
- AbuseIPDB
- Account added and removed from privileged groups
- Account created from non-approved sources
- AD Account with don’t expire password
- Addition of a temporary access pass to a privileged account
- ADFS DKM Master Key Export
- Anomalous login followed by Teams action
- Anomalous Microsoft Entra ID apps based on authentication location
- Anomalous Resource Creation and related Network activitty
- Anomalous sign-in location by user account and authenticating application with sign in details
- Anomaly sing in event from an ip
- Anomalous single factor sign in
- Azure diagnostics settings removed from a resource
- Azure key vault
- Azure log coverage
- Azure logic apps
- Azure security benchmark
- Cloud service threat protection essentials
- Cloud identity threat protection essentials
- Changes to PIM settings
- Business email compromise
- Brute force attack against user credentials
- Conditional access policy modified by new user
- Conditional access trends and changes
- Continuous diagnostics& mitigation
- Endpoint threat protection essentials
- External user access enabled
- Failed azure ad logons but success logon to host
- Failed host logons but success logon to azure ad
- Group create then added to built in domain local or global group
- High count of failed attempts from same client id
- High count of failed logons by a user
- High number or urgent vulnerabilities detected
- Insecure Protocols
- Mass download and copy to usb by single user
- M365d alerts correlation to non-Microsoft network device
- Log4j post compromise hunting
- Entra ID Registry keys access
- Entra ID Sign-in burst
- Microsoft purview
- Purview Information Protection
- Microsoft Sentinel cost
- Multiple rdp from single system
- New user created and added to the built-in administrators group
- Service principal assigned prvileged role
- Sign-ins from ips that attempt sign-ins to disabled accounts
- Threat Analysis & Response
- User Granted Access and created resources
- User account enabled and disabled within 10 min
- User account created and deleted within 10 min
- User login from different countries within 3 hours
- User State changed from Guest to Member
- Windows Security Events





