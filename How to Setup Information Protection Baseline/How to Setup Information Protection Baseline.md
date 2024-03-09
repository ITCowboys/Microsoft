# Create an Information Protection Baseline

## What is Microsoft Purview Information Protection

Microsoft Purview Information Protection (formerly known as Azure Information Protection) is a comprehensive solution designed to help organizations discover, classify, protect, and manage their data, regardless of where it's stored or with whom it's shared. Here's a short technical summary of its key components and functionalities:

1. **Data Discovery and Classification**: Microsoft Purview provides advanced tools for identifying and categorizing data across various environments, including on-premises, in cloud services, and in devices. It uses both automated and manual classification methods, leveraging built-in or custom classification labels.
1. **Labeling and Protection**: Once data is classified, labels can be applied automatically or by users, based on the classification. These labels can carry encryption, access restrictions, and visual markings like watermarks. Microsoft Purview uses Azure Rights Management (Azure RMS) for data protection, ensuring only authorized users can access the data.
1. **Policy Enforcement**: Administrators can set up policies to control how data is classified and protected. These policies can be applied across the organization to enforce compliance with regulatory requirements and internal data governance policies.
1. **Monitoring and Analytics**: Purview offers detailed tracking and reporting capabilities, allowing organizations to monitor how classified and protected data is being accessed and shared. This helps in detecting potentially risky behaviors and aids in compliance reporting.
1. **Integration and Compatibility**: Microsoft Purview Information Protection integrates with a wide range of Microsoft products and services, such as Microsoft 365, Azure services, Windows, and third-party applications, providing a seamless data protection experience across different platforms.
1. **Cross-Platform Support**: It extends its data protection capabilities beyond Microsoft environments, offering support for various types of non-Microsoft files and services, ensuring comprehensive protection regardless of the data's location.

![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Information%20Protection%20Baseline/Source/Picture1.png)

In essence, Microsoft Purview Information Protection empowers organizations to effectively manage and secure their data, helping them meet compliance requirements and protect sensitive information against unauthorized access and leaks.

## Create an Information Protection Baseline

To get you started with Microsoft Purview Information Protection we have developed a nice and easy Baseline which you can use within your own organization! This Baseline will create 4 Sensitivity Labels which can be applied to Files and Emails. **Note:** these will not apply to Groups or Teams!

We recommend starting with the 4 labels below:

- Public
  - No restrictions!
- Internal
  - Only accessible for people within your Microsoft tenant
- Confidential
  - Restrictions like printing, forwarding and more!
- External Confidental
  - Make sure your data is only accessible with the right external users.

After implementing and adoption within your organization you can take a look into defining more labels, for example create some labels that are only available to the HR-team and can’t be accessed outside this team. Nice and Secure 😊

|**Setting**|**Public**|**Internal**|**Confidential**|**External Confidential**|
| :- | :- | :- | :- | :- |
|*Files*|X|X|X|X|
|*Emails*|X|X|X|X|
|*Control Access*|X|X|X|X|
|*Apply Content Marking*|No|No|Yes, Header|Yes, Header|
|*Access Control*|Remove|Configure|Configure|Configure|
|*Assign Permissions now*|None|Yes|Yes|Yes|
|*User access to content expires*|None|Never|Never|Never|
|*Allow Offline Access*|None|Never|Never|Never|
|*Assign permissions to*|None|All Users and Groups|All Users and Groups|All Users and Groups + Authenticated Users|
|*Permissions*|None|Co-Author|View, Edit, Save, Reply All, Edit Rights, Allow Macros|View, Edit, Save, Reply All, Edit Rights, Allow Macros|
|*Auto-Labeling*|None|None|None|None|

The next subjects within this Baseline document will be:

- Enable Office for Web Integration
- Creating the Sensitivity Labels
- Applying the Sensitivity Labels
- Creating an auto-labeling Policy
- Excluding certain email addresses (ticket system for example) with DLP so labels are automatically removed
- Set auto-labeling for data at rest with Microsoft Defender for Cloud Apps


### Enable Office for Web Integration

1. Within compliance.microsoft.com -> Information Protection you will see the following screen including the yellow popup
   ![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Information%20Protection%20Baseline/Source/Picture2.png)
1. Click on “Turn on now”
1. You are now able to access Sensitivity Labels from the Office Web Apps!

### Creating the Information Protection Labels
Here you will see an example of creating a Information Protection Label, please use the Baseline from this document to Create all 4 labels

1. Within compliance.microsoft.com -> Information Protection -> Labels, Click on Create a Label
1. Fill in the name and description of the label
  ![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Information%20Protection%20Baseline/Source/Picture3.png)

1. Apply the label on Files and Email
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Information%20Protection%20Baseline/Source/Picture4.png)

1. Select Control Access (and) Content Marking based on your Label Baseline
 ![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Information%20Protection%20Baseline/Source/Picture5.png)

1. If Applicable select “Go to co-authoring setting”
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Information%20Protection%20Baseline/Source/Picture6.png)
1. Turn on co-authoring setting
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Information%20Protection%20Baseline/Source/Picture7.png)
1. Let remove encryption (needed when declassifying data)
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Information%20Protection%20Baseline/Source/Picture8.png)
1. We don’t want to auto-label files with a Public label
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Information%20Protection%20Baseline/Source/Picture9.png)
1. Create Label

### Applying the Sensitivity Labels

Now it’s time to publish our labels to All users!

Within compliance.microsoft.com -> Information Protection -> Label Policy, Click on Publish Labels

![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Information%20Protection%20Baseline/Source/Picture10.png)

1. Choose the Labels you just created
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Information%20Protection%20Baseline/Source/Picture11.png)
1. Publish to all users and groups
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Information%20Protection%20Baseline/Source/Picture12.png)
1. Make sure a justification and label are mandatory
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Information%20Protection%20Baseline/Source/Picture13.png)
1. Default label for Documents -> Internal
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Information%20Protection%20Baseline/Source/Picture14.png)
1. Default label for Emails -> Same as Document and Inherit from attachment
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Information%20Protection%20Baseline/Source/Picture15.png)
1. Name your Policy: Default Label Policy

![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Information%20Protection%20Baseline/Source/Picture16.png)




### Creating an auto-labeling Policy

Now we want to make sure that certain information is automatically labeled as Internal. Within compliance.microsoft.com -> Information Protection -> Auto-Labeling, Click on Create Auto Labeling Policy

1. Choose GDPR Enhanced
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Information%20Protection%20Baseline/Source/Picture17.png)
1. Naam: GDPR Enhanced – Internal
1. All Sites & OneDrive Accounts
1. Common Rules
1. Auto-Apply Internal Label
1. Run in simulation mode and turn on after 7 days.
1. Repeat all these steps but select PCI (Financial) as an info type



### Excluding certain email addresses (ticket system for example) with DLP so labels are automatically removed

In some cases are email addresses embedded into the primary process of the organization. For example sending emails to a internal Ticket system, or just emailing financial data (payslips, bankjobs) to Applications. In order to make sure not encrypted content is being sent we want to make sure encryption is removed in certain cases.

Next we will give you an example on how to exclude an internal email address from getting emails that are encrypted (and not readable from the application).

Within compliance.microsoft.com -> Data Loss Prevention -> Policies, Click on Create Policy

1. Custom Policy
1. Name: Remove Label to Email (Application cq. Topdesk)
1. Exchange Online Only
1. Create Rule
   1. Name: Remove Label
   1. Set content as shown below:

![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Information%20Protection%20Baseline/Source/Picture18.png)

### Set auto-labeling for data at rest with Microsoft Defender for Cloud Apps

We also want that all files that are present when implementing Information Protection are also begin protected. So we are going to create a policy which will Label all existing files as “Internal”

As a pre-requisite please follow the steps in: <https://github.com/ITCowboys/Microsoft/blob/main/Microsoft%20Defender%20Tenant%20Settings%20-%20XDR%2C%20Identities%2C%20Endpoints%2C%20Devices/Microsoft%20Defender%20(Tenant)%20Settings%20Baseline.md#cloud-apps-settings> this will make sure we can work with Files in Microsoft Defender for Cloud Apps.

Go to security.microsoft.com -> Cloud Apps -> Policies -> Policy Management and click “New Policy -> File Policy”

1. Name: Auto Labeling Policy Internal
1. Category: DLP
1. Severity: Low
1. Created – After(Date) – 02-01-0020 (So all files 😊)
1. All files
1. All file owners
1. Governance Actions
   1. OneDrive for Business
      1. Apply Sensitivity Label – Internal
   1. SharePoint Online
      1. Apply Sensitivity Label - Internal

All existing files will now be labelled as Internal (this might take a while.. )



