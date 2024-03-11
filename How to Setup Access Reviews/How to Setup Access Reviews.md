# How to Setup Access Reviews

## What is Microsoft Entra Access Reviews

Microsoft Entra Access Reviews is a feature within the Microsoft Entra suite designed to help organizations efficiently manage and secure identities and access across various applications and services. This tool is pivotal in ensuring that users have appropriate access rights and in maintaining compliance with internal and external regulations. Here's a concise technical summary of its key functionalities:

1. **Automated Review Campaigns**: Access Reviews allows organizations to automate the process of reviewing user access to resources, such as Azure AD groups, Azure AD applications, and SharePoint Online sites. This automation helps in regularly assessing and verifying the necessity of access rights assigned to users.
1. **Comprehensive Oversight**: It provides a centralized view for administrators to track and manage access reviews, making it easier to identify excessive or inappropriate permissions that might pose a security risk.
1. **Configurable Settings**: Administrators can tailor access review campaigns based on specific requirements, such as defining the frequency of reviews, selecting the scope of review (e.g., specific groups or applications), and determining who should perform the review (e.g., group owners, application owners, or the users themselves).
1. **Delegation and Collaboration**: The tool supports delegating the review process to the actual owners of the resources, fostering accountability and ensuring that those with the most knowledge of the resource are making access decisions. It also allows for collaboration among reviewers, enhancing the accuracy of access reviews.
1. **Actionable Insights and Remediation**: Upon completion of a review, Access Reviews provides actionable insights, including recommendations for removing unnecessary access. It can automate the process of revoking access, reducing the risk of unauthorized access and ensuring compliance with least privilege principles.
1. **Integration with Governance Policies**: Access Reviews is integrated with Microsoft Entra’s governance policies, supporting broader identity governance strategies. This integration helps in enforcing access policies and compliance standards across the organization.
1. **Reporting and Compliance**: It offers detailed reporting capabilities, enabling organizations to audit access reviews, monitor compliance with access policies, and demonstrate adherence to regulatory requirements.

![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Access%20Reviews/Source/Picture1.png)

Microsoft Entra Access Reviews is an essential tool for organizations looking to streamline their access review processes, enhance security by ensuring appropriate access, and maintain compliance with governance and regulatory standards.



## Implementing Access Reviews in your Tenant

## Creating an Access Reviews Baseline

Please make sure you create a Access Reviews Baseline for your Reviews.. We have created an example below with 5 use cases!

|**Details**|**Review Type**|**Reviewers**|**Duration**|**Recurrence**|**Auto Apply**|**If  reviewers don’t respond**|
| :- | :- | :- | :- | :- | :- | :- |
|Let Guests review their own accounts Quarterly|All Groups with guest users – Guest users only|Users review their own access|7 Days|Quarterly|Yes|` `Remove Access|
|Review Users assigned to Enterprise Application|Applications <Your Business Apps> - All Users|Application Owners|7 Days|Monthly|Yes|No Change|
|Review Users assigned to PIM Roles (groups)|Teams + Groups – Select your PIM Security Groups|HR or Management|7 Day|Monthly|Yes|No Change|
|Review Conditional Access Exclusions Security Groups|Teams + Groups – Select your Security Groups|Architects of Senior Staff|7 Days|Monthly|Yes|No Change|



## Setting up Access Reviews 

Next we are going to show you how to setup an Microsoft Entra Access Review!

Within the Azure Portal, go to -> Identity Governance -> Access Reviews

![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Access%20Reviews/Source/Picture2.png)

1. Select “New Access Review”
1. In this Example we are going to a create an Access Review for Guests to confirm their account Quarterly to keep access to the Tenant.
1. Select Teams + Groups – All M365 Groups with guest users – Guest users only
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Access%20Reviews/Source/Picture3.png)

1. Select users review their own access and fill in the recurrence fields

![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Access%20Reviews/Source/Picture4.png)
1. Configure that if Guests don’t respond access is revoked
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Access%20Reviews/Source/Picture5.png)

1. Create! That’s all 😊
