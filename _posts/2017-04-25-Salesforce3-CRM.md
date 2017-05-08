---
layout: post #post
title: Salesforce 3 -- CRM Essential #post title
categories: Salesforce #post category, seperated by spcace
tags: Salesforce #post tag, seperated by spcace
---


Notes from: https://trailhead.salesforce.com/trails 
All content from: https://trailhead.salesforce.com/trails 

## 4. CRM Essential
1. Accounts are companies that you're doing business with, and contacts are the people who work for them.
2. If you’re doing business with a single person, like a solo contractor or an individual consumer, you use a special account type called a Person Account.
3. Understanding how to use accounts and contacts is key to getting the most out of Salesforce CRM.
4. Account View: When you open the account record, you see the information collected on the company as a list of records related to it, such people who work there, deals in the works, service requests, uploaded documents, and more.
5. The Social Accounts, Contacts, and Leads feature adds social network information from Twitter, Facebook, YouTube, and Klout to your records. To use it, you must have an account on each social network that you’re using, and you have to link the account or contact record to a user profile on each social network.
6. Managing Accounts and Contacts
    1. Establish naming conventions for accounts
    2. Don’t allow orphan contacts. Always associate contacts with an account.
    3. Audit your accounts and contacts. Use exception reporting in Salesforce to find accounts and contacts without activities in the last 30, 60, or 90 days. Or create an “inactive” checkbox field on your account and contact objects, and use mass update to denote inactive accounts. Set up an automated process to mark accounts and contacts inactive for you, based on criteria you specify.
    4. Handle inactive accounts and contacts. For example:
        - Organize an outreach campaign to re-engage with them
        - Exclude them from list views, reports, automated processes, campaigns, and more so you can focus marketing, sales, and service efforts on active customers .
    5. Maintain active ownership
7. Three Key Account and Contact Relationships
    - Contacts to Multiple Accounts lets you relate a contact to more than one account so you can track the relationships between people and the companies they work with.
        - add **roles** to direct and indirect contacts so you know who’s your best bet. 
        - **Account Hierarchy** lets you see what companies ABC Genius is affiliated with. 
        - **Account Teams** tells you which sales reps are working on the ABC Genius deal so you can better coordinate with your internal team
8. how to establish accounts for businesses with multiple locations. two basic choices:
    - Global Enterprise Account
    - Location-Specific Accounts(recommended)
9. Sales Process and using opportunities
    - **Opportunities** are deals in progress, you can create opportunities for existing accounts or by converting a qualified lead
    - **an opportunity** moves through a series of stages linked to type of tasks being performed, who’s got the ball, and how likely it is that the sale will be made
    - **stages** you usually go through might look like this: prospecting --> developing --> negotiation/review --> closed won/closed lost
    - Each stage is **associated with a probability** that the deal will be completed successfully. The default probability is set by the administrator. 
    - Each stage must be assigned a probability. Probabilities are used when creating forecasts, which are not covered in this course.
    - Create an **Opportunity Record Type**. The record type is how you link a particular page layout and sales process to a type of product. Record types determine which types of sales opportunities pass through which sales process.
    - **Opportunity Teams** are a bit like Account Teams. Both allow you to relate particular people at your company to accounts or opportunities. But where Account Team members can be expected to form a long-term relationship with the customer, an Opportunity Team is a temporary group composed of people who can help you close the deal.
10. Converting and assigning leads
    - **Leads** are people and companies that you’ve identified as potential customers.
    - **big advantages to using leads** like knowing what’s in your pipeline and focusing your energy on the right deals. You can better track, report on, and target marketing campaigns to prospective customers. Leads may help you concentrate on the potential deals most likely to close. They also help executives maintain visibility and help on key deals
    - **how to catch leads**:  Leads created from a web form or other automatic process. add leads by importing a file into Salesforce or through an automatic process, such as a Web-to-Lead form that collects leads from your business website.
    - **assignment rule** Before setting up lead assignment rules for your company, you should carefully review your existing business process to determine how leads should be assigned. After leads have been assigned according to your process, be sure to include a catch-all assignment rule to catch any leads who don’t somehow qualify for any other rules.
    - **convert** 
        1. When you qualify a lead, you can convert the lead record into an opportunity. Qualifying a lead indicates that you believe that the lead has a use for and interest in your products, and that a sale to the lead is a definite possibility
        2. When you convert a lead, Salesforce uses the information stored in the lead record to create a business account, a contact, and an opportunity. 
        3. If your organization has person accounts enabled and the lead record didn’t include a company name, the lead is converted into a person account and an opportunity.
11. Data Quality
    -  how to assess the quality of your company’s data.
        - The first step in assessing data quality is to figure out how your company uses customer data to support its business objectives. Sounds like a good start.
        You meet with managers and reps across Gelato and ask them:
        What are your business objectives?
        What customer data do you need to support those objectives?
        How are you using that customer data?
        Where is your customer data stored?
12. SKIP CPQ


## 5. Admin Intermediate
1. Formula Fields
    - Let’s take a single field from an Account and show it on a Contact using what’s called a **cross-object formula**.
    - Say, for example, you have a hundred opportunities listed in a report, but only a handful of users own all these opportunities. How do you find the number of distinct users? This task sounds difficult, but it’s one of the easiest formulas you can write. It’s called the **Power of One**.
    - You can use the **Power of One** on any object. For example, if you had a report with 10 accounts, each with three opportunities, your Opportunities report returns 30 records. Adding the Power of One formula field to Account allows you to see the number of distinct accounts represented in the records.
    - VALIDATION:(formula = true, not valid)
        1. Validates that the Account Number is numeric if not blank. Error Message: Account Number is not numeric.
        ```
        	    AND(
            NOT(ISBLANK(AccountNumber)),
            NOT(ISNUMBER(AccountNumber))
        )
        ```
        2. Validates that a custom date field contains a date within the current year.
        `YEAR( My_Date__c ) <> YEAR ( TODAY() )`
        3. Validates that the range between two custom fields, Salary Min and Salary Max, is no greater than $20,000. Error Message:	Salary range must be within $20,000. Adjust the Salary Max or Salary Min values.
        `(Salary_Max__c - Salary_Min__c) > 20000`
2. Data Security
    -  you can provide just the right level of data access to thousands of users without having to specify permissions for each user individually.
    - Although you can configure the security and sharing model entirely using the user interface, it is implemented at the API level. That means any permissions you specify for objects, records, and fields apply even if you query or update the data via API calls. 
    - **Organization**: At the highest level, you can secure access to your organization by maintaining a list of authorized users, setting password policies, and limiting login access to certain hours and certain locations.
    - **Objects**:  By setting permissions on a particular type of object, you can prevent a group of users(by profile) from creating, viewing, editing, or deleting any records of that object.
        - For example, you can use object permissions to ensure that interviewers can view positions and job applications but not edit or delete them.
        - There are two ways of setting object permissions. You can use profiles or permission sets.
    - **Fields**: you can use field-level security to restrict access to certain fields, even for objects a user has access to. 
        - For example, you can make the salary field in a position object invisible to interviewers but visible to hiring managers and recruiters.
    - **Records**: To control data with greater precision, you can allow particular users to view an object, but then restrict the individual object records they're allowed to see. 
        - For example, record-level access allows an interviewer to see and edit her own reviews, without exposing the reviews of other interviewers. You can manage record-level access in these four ways.
        - record level access: **Organization-wide defaults** specify the default level of access users have to each others' records.
            - You use organization-wide sharing settings to lock down your data to the most restrictive level, and then use the other record-level security and sharing tools to selectively give access to other users.
        - record level access: **Role Hierarchies** open up access to those higher in the hierarchy so they inherit access to all records owned by suers below them in the hierarchy.
            - each role in the hierarchy should represent a level of data access that a user or group of users needs.
        - record level access: **Sharing rules** enable you to make automatic exceptions to organization-wide defaults for particular groups of users, to give them access to records they don’t own or can’t normally see.
            -  Sharing rules, like role hierarchies, are only used to give additional users access to records—they can’t be stricter than your organization-wide default settings.
        - record level access: **Manual sharing** allows owners of particular records to share them with other users. 
    - **When implementing security and sharing rules** for your organization, make a table of the various types of users in your organization. In the table, specify the level of access to data that each type of user needs for each object and for fields and records within the object. You can then refer to this table as you set up your security model.
    - Auditing features include: Record Modification Fields; Login History;Field History Tracking; Setup Audit Trail
    - The System Administrator profile also includes two special permissions: View All Data，Modify All Data。
    - A permission set is a collection of settings and permissions that give users access to various tools and functions. permission sets extend users’ functional access without changing their profiles.  
        - For example, to give users access to a custom object, create a permission set, enable the required permissions for the object, and assign the permission set to the users.
        - two common scenarios in which permission sets are useful.To grant access to custom objects or entire apps. To grant permissions—temporarily or long term—to specific fields.
3. Process Automation
    - Salesforce provides multiple tools to automate your org’s repetitive business processes: **Lightning Process Builder, Visual Workflow, Workflow, and Approvals**. 
    - 





## Security Specialist
1. Here are the three protocols that Salesforce and other identity vendors follow to implement identity solutions.
    - SAML（SAML is an XML-based protocol）
    - OAuth 2.0
    - OpenID Connect