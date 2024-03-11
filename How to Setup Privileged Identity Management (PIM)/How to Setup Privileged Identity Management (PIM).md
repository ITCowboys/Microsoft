# How to Setup Privileged Identity Management (PIM)

## What is Privileged Identity Management (PIM)

Microsoft Entra Identity Privileged Identity Management (PIM) is a service designed to manage, control, and monitor access within Microsoft Entra, Azure, and other Microsoft Online Services through the enforcement of just-in-time privileged access, assignment of time-bound access, and requirement of approval to activate privileged roles. Here's a concise technical summary of its key features and functionalities:

1. **Just-in-Time Access**: PIM enables the granting of privileged access on an as-Noded basis, significantly reducing the risk associated with standing administrative access. Users or administrators are given access for a specific duration, after which the rights are automatically revoked.
1. **Conditional Access Policies**: Integration with Microsoft Entra Conditional Access allows organizations to enforce policies that require additional verification or criteria to be met before granting privileged access, enhancing security posture against potential threats.
1. **Role-Based Access Control (RBAC)**: With PIM, administrators can assign time-limited access to resources using Azure's RBAC capabilities. This helps in ensuring that users have access only to the resources necessary for their role and only when they Nod it.
1. **Approval Workflow**: Administrators can set up workflows requiring approval for activating privileged roles. This adds an additional layer of oversight, ensuring that access is granted appropriately and in accordance with organizational policies.
1. **Audit Logs and Alerts**: PIM provides detailed audit logs and alerting capabilities, allowing organizations to monitor privileged access, view historical data on access assignments, activations, and approvals, and detect potential security issues through abnormal access patterns.
1. **Multi-factor Authentication (MFA) Requirement**: To enhance security further, PIM can enforce multi-factor authentication for activating privileged roles, ensuring that only authenticated users can gain access.
1. **Cross-platform Support**: While primarily focused on Microsoft Entra and Azure resources, PIM also extends its capabilities to manage and secure access to other Microsoft Online Services, offering a unified approach to privileged access management across the Microsoft cloud ecosystem.

![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Privileged%20Identity%20Management%20(PIM)/Source/Picture12.jpg)

In essence, Microsoft Entra Identity Privileged Identity Management (PIM) provides organizations with powerful tools to minimize risks associated with privileged access, enforce compliance with internal and external regulations, and ensure that privileged access management aligns with the principle of least privilege.

## The Basics of Privileged Identity Management

**Direct Assignments**

These assignments occur outside of the PIM process and are essentially not used. The only exception to this should be the Break Glass Account.

**Permanent Assignments**

These assignments are always in effect and do not Nod to be approved within the PIM process. Utilizing this type of assignments can be useful for standardly granting read rights to certain users.

**Eligible Assignments**

These are the roles that a user is allowed to activate through the PIM process. The requests for these roles are handled via the PIM Approval Flows. The approval process can be designed differently for each role**.**

**Approval Flows**

Granting rights based on a request can be summarized in a short process flow as follows.

![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Privileged%20Identity%20Management%20(PIM)/Source/Picture13.jpg)

This reveals several core concepts:

- The request must be approved by another user,
  - Often, this is an administrator or someone in a higher hierarchical position.
- The request automatically expires after a certain period,
  - This is to prevent "infinite" admins.
- The rights are automatically revoked.

The described approval flow is commonly applied to important (high privileged) roles with mutation rights. For less critical roles with read rights, the process is somewhat simpler.

![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Privileged%20Identity%20Management%20(PIM)/Source/Picture14.jpg)

Here, it is evident that the approval is automated. The user is immediately granted their read rights. However, the condition that the rights automatically expire after a certain period remains in place.

## Implementing Privileged Identity Management in your Tenant

## Creating a Privileged Identity Management Baseline

Please make sure you create a Privileged Identity Management Baseline for your Roles, Assignments and potential Approvals. We have create an example below!

|**Role**|**Type Rol**|**Activation Time**|**Assignment Type**|**Approval**|**Security Group**|**Approval Group**|
| :- | :- | :- | :- | :- | :- | :- |
|Application Administrator                |Microsoft Entra Build-in|4 hours|Eligible Assignment|Yes|G\_Azure\_Role\_appadmins|G\_Azure\_pim\_approvers|
|Compliance Administrator               |Microsoft Entra Build-in|4 hours|Eligible Assignment|Yes|G\_Azure\_Role\_comadmins|G\_Azure\_pim\_approvers|
|Global Administrator                      |Microsoft Entra Build-in|4 hours|Eligible Assignment|Yes|G\_Azure\_Role\_gloadmins|G\_Azure\_pim\_ga\_approvers|
|Security Administrator   |Microsoft Entra Build-in|4 hours|Eligible Assignment|Yes|G\_Azure\_Role\_secadmins|G\_Azure\_pim\_sec\_approvers|
|Exchange Administrator |Microsoft Entra Build-in|4 hours|Eligible Assignment|No|G\_Azure\_Role\_exoadmins||
|SharePoint Administrator|Microsoft Entra Build-in|4 hours|Eligible Assignment|No|G\_Azure\_Role\_spoadmins||
|Intune Administrator |Microsoft Entra Build-in|4 hours|Eligible Assignment|No|G\_Azure\_Role\_intadmins||
|Teams Administrator|Microsoft Entra Build-in|4 hours|Eligible Assignment|No|G\_Azure\_Role\_tmsadmins||
|User Administrator                       |Microsoft Entra Build-in|4 hours|Eligible Assignment|No|G\_Azure\_Role\_usradmins||
|Groups Administrator |Microsoft Entra Build-in|4 hours|Eligible Assignment|No|G\_Azure\_Role\_groadmins||
|Power Platform Administrator |Microsoft Entra Build-in|4 hours|Eligible Assignment|No|G\_Azure\_Role\_ppadmin||
|Privileged Authentication Administrator |Microsoft Entra Build-in|4 hours|Eligible Assignment|No|G\_Azure\_Role\_paadmins||
|Owner (Management Group)|Azure Resource|4 hours|Eligible Assignment|Yes|G\_Azure\_Role\_mgadmins|G\_Azure\_pim\_azu\_approvers|

|**Role**|**Type Role**|**Assignment Type**|**Security Group**|
| :- | :- | :- | :- |
|Global Reader|Microsoft Entra Build-in|Permanent Assignment|G\_Azure\_Role\_greaders|
|Security Reader               |Microsoft Entra Build-in|Permanent Assignment|G\_Azure\_Role\_sreaders|
|Reader (Management Group)|Azure Resource|Permanent Assignment|G\_Azure\_Role\_azreaders|



## Setting up Privileged Identity Management 

Next we are going to show you how to setup a Microsoft Entra Role and a Azure Resource Role!

## Integrated Microsoft Entra Roles

Within the Azure Portal, go to -> Privileged Identity Management -> Microsoft Entra  Roles

![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Privileged%20Identity%20Management%20(PIM)/Source/Picture15.jpg)

1. Select Roles
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Privileged%20Identity%20Management%20(PIM)/Source/Picture16.jpg)

1. Select your Role of Choice, for example: Application Administrator
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Privileged%20Identity%20Management%20(PIM)/Source/Picture17.jpg)

1. Select Settings -> Edit
1. Configure your desired Activation Time, Require MFA, Justification, Ticket Information and Approval (if needed)
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Privileged%20Identity%20Management%20(PIM)/Source/Picture18.jpg)

1. On the Assignment Blade, Uncheck the box for permanent active assignments, and require justification and MFA on active assignments
  ![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Privileged%20Identity%20Management%20(PIM)/Source/Picture19.jpg)

1. Change Notifications as you desire.
1. Now you have updated your Role settings you are able to Assign the role to a Security Group
![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Privileged%20Identity%20Management%20(PIM)/Source/Picture20.jpg)

1. Make sure you consolidate any existing assignments into a Security Group for easy Management!

## Azure Resource Roles

For Azure Resource Roles we need to perform the same steps, with some additional actions. Go to Privileged Identity Management ![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Privileged%20Identity%20Management%20(PIM)/Source/Picture21.jpg)

1. We need to onboard Scopes for PIM, this could be Management Groups, Subscriptions, Resource Groups of Resources. In this example we will onboard a Subscription
1. Select the Subscription and “Manage Resource”
  ![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Privileged%20Identity%20Management%20(PIM)/Source/Picture22.jpg)

1. Go to Roles and Select the Role of Choice, for example: Reader
  ![image](https://github.com/ITCowboys/Microsoft/blob/main/How%20to%20Setup%20Privileged%20Identity%20Management%20(PIM)/Source/Picture23.jpg)
  
1. Follow the same steps as for Microsoft Entra Roles.
1. You have now successfully implemented your first PIM roles and Assignments!
