---
layout: post #post
title: Salesforce Review #post title
categories: Salesforce #post category, seperated by space
tags: Salesforce #post tag, seperated by space
---


All content from: http://www.salesforce-interviewquestions.com/p/interview-questions.html, http://www.salesforcetutorial.com/salesforce-interview-questions-answers-part2/, http://www.jitendrazaa.com/blog/tag/interview-questions/


## Salesforce Fundamental questions
1. What is Apex ?
    - It is the in-house technology of salesforce.com which is similar to Java programming with object oriented concepts 
    - we can write our own custom logic using Apex.
2. What is a Visualforce Page ?
    - Visualforce is the new markup language from salesforce, by using which, We can render the standard styles of salesforce. 
    - We can still use HTML here in Visualforce. Each visualforce tag always begins with “apex” namespace. 
    - All the design part can be accomplished by using Visualforce Markup Language and the business logic can be written in custom controllers associated with the Page.
4. Will Visual force still supports the merge fields usage like S-control ?
Visualforce Pages support embedded merge fields, like the {!$User.FirstName} used in the example.
6. What are Apex Governor Limits?
Governor limits are runtime limits enforced by the Apex runtime engine. Because Apex runs in a shared, multi-tenant environment, the Apex runtime engine strictly enforces a number of limits to ensure that code does not monopolize shared resources. Types of limits that Apex enforces are resources like memory, database resources, number of script statements to avoid infinite loops, and number of records being processed. If code exceeds a limit, the associated governor issues a runtime exception.
8. Cloud Computing is an approach to provide the following services -
    - SAAS (Software As A Service)
    - PAAS (Platform As A Service)
    - IAAS (Infrastructure As A Service)
9. Application build block:
    ||Declarative(simplicity+speed)|Programmatic(control+flexibility)|
    |Data model | Objects, fields, relationships | Web Service API, metadata API|
    |Business logic |  workflow, validation rules, approval process, assignment rules | Controllers, Apex, Web Service|
    |User Interface | record type, page layout, applications, tabs | Visualforce Page, Force.com Sites|
10. formula field: it calculate values using fields within a single record
11. rollup summary fields. These fields store values aggregated from the child records in the relationship.( it calculates the values from a set of child record)
12. record types: 
    - The report type determines which fields and records are available for use when creating a report. 
    - Each report type has a primary object and one or more related objects. 
1. reports: to summarize the information of the object we use reports
2. Bucket field in Reports is used to group values to the name we specify.
1. Bucket Field: Used in reports to categories and group report values
2. Junction Object: A Many-to-Many relationship created with two lookup master-detail relationship


## email to case:
1. Salesforce can automatically create a case when an email is sent to one of your company's email addresses, such as support@company.com. 
2. This Email-to-Case functionality auto-populates case fields from the content of each email. For example, an email subject heading becomes a case subject.
3. Email-to-Case requires downloading and installing the agent. Use Email-to-Case if you have a requirement to keep all email traffic within your firewall, and you want to accept email attachments larger than 25 MB from customers.
4. On-Demand Email-to-Case uses Apex email services to convert email to cases, without you having to download and install an agent behind your network's firewall. Use On-Demand Email-to-Case if you are not concerned about keeping email traffic within your firewall and you do not need to accept attachments larger than 25 MB from customers.
5. Configuration of the Email-to-Case Agent code process consists of the following:
    - Configuring the sfdcconfig.txt file - what username and password does the agent use to connect to Salesforce?
    -  Configuring the email2case.txt file - which mailboxes does the agent poll through IMAP?
    - Setting up and test routing addresses - what are the record type, origin, and priority of cases per mailbox being polled?
6. how to set up On-Demand Email-to-Case:
    - Determine the email routing addresses that your customers can use to submit cases to your support team.
    - Set up assignment rules, escalation rules, and auto-response rules.
    - In Salesforce enable Email-to-Case and configure your email routing addresses.（add a new email routing address, verify the new email routing address, then enable Email-to-Case:）
    - Add email related list to Case page layouts.
    - Configure your email system to forward case submissions to the email services address provided to you by Salesforce.
    - test:
        1. Manually send emails to the routing addresses.
        2. Verify that the emails convert to cases based on their routing address settings.
7. sample settings/configuration： https://success.salesforce.com/ideaView?id=087300000006tre
8. Thread Id
    - unique id generated for each case generated via email
    - ensure that the email body and subject both are different, otherwise email-to-case creates an infinite loop of emails related to each case
9. example： http://focusonforce.com/configuration/salesforce-email-to-case-example/



1. web-to-case
3. trigger/workflow 
4. load data


## Dashboard and Reports
1. reports:
    - summary of data that's stored in the application
    - There can be at most 5 custom summary formula fields are allowed on a single report.
2. report formats:
    - tabular reports: 
        1. tabular reports are the simplest and fastest form reports in salesforce. These are similar to spread sheet. 
        2. They consist of  ordered set of fields in columns and match record listed in a row. 
        3. These reports can not be used to group data or graphs.
    - summary reports: 
        1. Summary reports are similar like tabular reports, but also allow users to group rows of data, view sub totals and create charts.
        2. These reports can be used in dashboards.
    - matrix reports: 
        1. allow you to group data both by row and column.
        2. can be used in dashboards and graphs.
        3. can not be used as source reports for analytical snapshot
    - joined reports: 
        1. Joined reports let you create different views of data from multiple report types.
        2. In joined reports, data is organized in blocks.
        3. Each block acts like a sub-report.
        4. can be used in charts.
3. Conditional highlighting 
    - cannot be used for tabular reports.
    - can be used for Summary and Matrix reports.
    - only applies to the first summary field column in the table.
    - 3 Ranges can be created in case of conditional highlighting.
    - for report: Shows you visual highlights depending on a threshold
3. dashboard: 
    - Dashboard is a container for reports, shows data from source reports as visual components.
    - components includes: Charts, Gauges, Tables, Matrix, Visualforce Pages.
    - A dashboard can hold up to 20 components.
    - A single dashboard can have up to 3 filters.
4. dynamic dashboard:
    - dynamic dashboards are dashboards show data according to users own security settings.
    - A sales manager would like to view a dashboard from the perspective of different users and switch between users without editing the dashboard, how would an administrator enable this?
        - Create the dashboard as a dynamic dashboard
        - Grant the sales manager the "View my Teams Dashboard" permission
5. It is possible for a user to see different set of data in report and in a dashboard based on the same report.
6. All dashboard viewers see data based on the security settings of the Running User regardless of their own personal security settings.
7. Running User concept in Dashboard allows users to view Data which normally they cannot view.
8. Dashboard snapshot on the home page displays First row of any available dashboards.






## Standard controller & custom controller:
1. Standard controller: by using standard controller you need not have to write apex code. Standard controller can be accessed on one object and referenced by visualforce page. It also  provides some save, cancel, clone for that object. Standard controller provides the same functionality what standard pages provide
2. custom controller: A custom controller is an Apex class that implements all of the logic for a page without leveraging a standard controller. Use custom controllers when you want your Visualforce page to run entirely in system mode, which does not enforce the permissions and field-level security of the current user.
3.  A controller extension 
    - is an Apex class that extends the functionality of a standard or custom controller. Use controller extensions when:
    - You want to leverage the built-in functionality of a standard controller but override one or more actions, such as edit, view, save, or delete.
    - You want to add new actions.
    - You want to build a Visualforce page that respects user permissions. Although a controller extension class executes in system mode, if a controller extension extends a standard controller, the logic from the standard controller does not execute in system mode. Instead, it executes in user mode, in which permissions, field-level security, and sharing rules of the current user apply.










## Export
7. How to schedule export backup of salesforce data
    - Salesforce allows you to obtain a copy of all your data using the data export feature. 
    - You can generate backup files manually once every six days or schedule them to generate automatically at weekly or monthly intervals.
    - The backup file will come to you in the form a zip file that contains all of your organization’s data in a set of CSV (comma-separated values) files.  
    - Step by Step Instruction:
        - Click Setup >Data Management > Data Export > Schedule Export.
        - Select the desired encoding for your export file. Leaving the default is fine.
        - Check the Include in export checkbox if you want to include attachments in the export (optional)
        - Leave the default Replace carriage returns with spaces if you want your export files to have spaces instead of carriage returns.
        - Select Weekly as the the frequency for the exports.
        - Choose start and end dates. Set the end date to sometime in the distant future such as 20 years from the begin date.
        - Set the time of day for your scheduled export. The export is put in a job queue and the exact time of the export will depend on the amount of activity in the queue.
        - You can select the types of data to include in your export. It is best to include all data in your export file. This will make sure all your organizations data is exported.
        - Click Save.
    - tips：
        - Formula, roll-up summary fields and articles are not included in exports.
        - Scheduled backup exports of your data is limited to weekly exports.
        - You have 48 hours from the time you are notifiedthe backup is available to download the backup file.
        - The export notification email is only sent to the email address on file for the user who created the scheduled export. The email notification for backups goes to the email address in Salesforce of the person logged in who schedules the backup
        
## Deployment and test
7. Difference between Sandbox and developer edition in Salesforce
    - Sandbox: 
        - The salesforce.com Sandbox environment is an exact copy of your salesforce.com instance. 
        -  You can copy your live instance to a sandbox environment where you can test any changes, implementations, AppExchange apps or updates. 
        - You have to perform manually from sandbox to developer edition.
        - Workflow rules or automations will work in the sandbox as well.
        - Included in Unlimited Edition, but hefty for Enterprise, Professional or Group Edition.
    - Developer Edition
        - Developer Edition was an edition created for development of integrations and apps, specifically for the AppExchange. 
        - It is also a great tool for testing/training in salesforce.com.
        - Free
        -  It is a standard Enterprise Edition with very limited storage space. 
        - You cannot copy your configuration or data onto the Developer Edition, but you can customize it to match your instance’s look and feel. Once it is customized, you can use it for training, testing or anything else you want.
6. How to migrate data from developer sandbox to production?
You have to use full sandbox to deploy the data from sandbox to production. You have to request salesforce for this or else you can use data loader to export the data from one org and import the same on another org.




      
## Web Service
2. How external app access salesforce?
    - Simple Object Access Protocol (SOAP) and Representational State Transfer (REST)
        - REST(architecture)
            - apex rest api: when we want to expose apex classes and methods we use this so that external app can access you code through rest architecture. 
            it supports both oauth and session id for authorization.
            - rest is client based protocol, do CRUD operations, can work with any database, any data structure. SOAP message, define logic in soap message. SF support both. 
        - SOAP
            - soap api: SOAP is a standards-based Web services access protocol that has been around for a while and enjoys all of the benefits of long-term use. Originally developed by Microsoft
            - sf-soap: soap API. Salesforce provides a WSDL (Web Service Description Language) files. They are called "Enterprise WSDL" and "Partner WSDL". (https://help.salesforce.com/articleView?id=000004760&language=en_US&type=1) Enterprise, can not used for different users because of different data structure; partner wsdl, use any object, use general calls, more flexible, maybe need type cast, eg: phone
        - soap Vs. rest: rest faster than soap, rest can do all translate. rest and soap are protocol, soap only xml, rest can do both(xml,json),rest is much easier to develop, soap is secure with structured contract defined,
    - access sf:
        - login login.sf.com, a server called "login" dealing with login service
        - server give a token back, 
        - session id
    - when sf want to access other systems, the API we should choose depends on what protocol that system uses. sf have tool which can convert .wsdl/.rest file(in that system) into neighbor object.
    - google：
        - both SOAP and REST share similarities over the HTTP protocol, SOAP is a more rigid set of messaging patterns than REST. The rules in SOAP are important because without these rules, you can’t achieve any level of standardization. REST as an architecture style does not require processing and is naturally more flexible. Both SOAP and REST rely on well-established rules that everyone has agreed to abide by in the interest of exchanging information.
2. API:
    - bulk api : it is specialized restful api, it is used to loading and querying lots of data lots of data in the scense 50000 above.

    - streaming api: it is used to setup notifications that triggers when the changes are made to the data

    - metadata api: it is used to retrieve, deploy, create,update or delete customizations from your org, the most common use is to migrate from sandbox or testing org to production.

    - tooling api: when we want integrate salesforce metadata with other systems.rest and soap are both supported we use tooling api to manage and deploy working copies of apex classes,triggers,visualforce,and components.

    - api request times for 20 seconds
    dev org-5
    trail-5
    pro-25
    sand-25


## Security -- Who sees what:
4. OWD -> role hierarchy -> sharing rules -> manual sharing.
1. **org-wide defaults** (also known as sharing settings)
    - OWD is the default access level on records for any object in sales force.
    - org-wide defaults determine what access and permissions users have to records they do not own.
    - how org-wide defaults work in conjunction with profile permissions? The permissions determine the baseline level of access a user has to all record. Org-wide defaults can then further restrict these permissions on records a user does not own.
1. **Profile** determine the objects a user can access, and the permissions a user has on an object record and which tab, app are visible.
3. **Permission Sets** - To improve the permissions for the users over profiles we should go for Permission Sets. To give additional permissions to few users who belongs to different profiles over Apps, Tabs, sObjects and fields.
2. A users baseline permissions on each object are determined by the profile. If you are using permission sets, these also set the baseline permissions in conjunction with the profile
1. By default after creating custom object OWD access level is Public Read/Write.
2. **role hierarchy** - a way to extend access to record, when org-wide default have been set to anything more restrictive than public read/write.  
    – The role hierarchy enables users above another user in the hierarchy to have the same level of access to records owned by or shared with users below.
3. implement sharing rules: we can implement sharing rules to open record access up to users when the org-wide defaults have been set to less than public read/write
4. **Sharing Rules** – used by administrators to automatically grant users within a given group or role access to records owned by a specific group of users.
5. **Manual Sharing**– Manual managed sharing allows the record owner or any user with Full Access to a record to share the record with a user or group of users.
6.  Profile vs. Permission sets:
    - profiles are like global....and permission sets are local.
    - While users have only one profile, they can have many permission sets.
    - For example, if you have one profile assigned to 20 different users. Now Suppose you want give some extra permission to one of user. You have two options here. a) To change Profile permissions : By this way those extra permissions will received by every user who is having that profile b) Second way is to create a permission set having those extra permission. You need to assign this permission set to particular user by navigating to User detail page. In this way, you dont have to worry about other users, as only specific user is getting those extra permissions.

3. what are sharing rules in salesforce?
    - Sharing rules are used by administrators to automatically grant users within a given group or role access to records owned by a specific group of users. Sharing rules cannot be added to a package and cannot be used to support sharing logic for apps installed from Force.com AppExchange.
    - Sharing rules can be based on record ownership or other criteria. You can’t use Apex to create criteria-based sharing rules. Also, criteria-based sharing cannot be tested using Apex.
    - All implicit sharing added by Force.com managed sharing cannot be altered directly using the Salesforce user interface, SOAP API, or Apex.
    - For example, use sharing rules to extend sharing access to users in public groups, roles, or territories. Sharing rules can never be stricter than your organization-wide default settings. They simply allow greater access for particular users.
    - you can create sharing rules based on record owner or field values in the record. This enables you to make automatic exceptions to your organization-wide sharing settings for defined sets of users.
3. Organization access:
    - IP Ranges(company level): Users outside the range are sent an activation code
    - IP Ranges(profile level): Users outside this range are denied access
    - Login Hours(profile level): specified hours are enforced
In Salesforce, permissions and access settings specify 
4. Object access: Profile - users baseline permission
    - Profile determine the objects a user can access, and the permissions a user has on an object record and which tab, app are visible.
    - standard profiles are provided by salesforce, these profiles may not be edited, but can be cloned and then edited to create custom profiles.
    - clone then edit, app/system
    - profile deals with credential permissions on tabs, objects, fields, record types etc and we can map only one profile to one uses and with out profile we cannot create user.
    - (Profile give users access to objs, tabs, fields, record types and many other functions.)
    - a profile provides access for general functions that a type of user performs.
5. Permissions sets: 
    - To improve the permissions for the users over profiles we should go for Permission Sets. To give additional permissions to few users who belongs to different profiles over Apps, Tabs, sObjects and fields.
    - can extend a user's access and permission
    - some users need access to additional objs and settings and you don't want to grant that access to everyone with the profile
    - assign a permission set to the users who need it.
5. Profile vs. Permission sets:
    - While users have only one profile, they can have many permission sets.
1. org-wide defaults (also known as sharing settings)
    - org-wide defaults determine what access and permissions users have to records they do not own.
    - how org-wide defaults work in conjunction with profile permissions? The permissions determine the baseline level of access a user has to all record. Org-wide defaults can then further restrict these permissions on records a user does not own.
2. role hierarchy: a way to extend access to record, when org-wide default have been set to anything more restrictive than public read/write
3. implement sharing rules: we can implement sharing rules to open record access up to users when the org-wide defaults have been set to less than public public read/write


##### Field Level Security
1. restrict a profiles view to a certain field
2. Field Level Security or Page Layout can not be used to make a field required
3. Formulas ignore Field Level Security settings

##### summary: 
1. record level permission set. 4 record access level: 
org-wide default: user can see other users' record when other users' record are set as org-wide default
2. role: 
sharing: horizontal sharing with different department
manually sharing: sharing to anyone you want access greater.
3. profile/permission set: object/field level
profile-baseline /permission set-additional




## Workflow, trigger, process builder
1. trigger: many objects, before and after
    - Trigger will perform actions before / after the record creation/update, it not only work on records, but also on diff places of declarative functionality of force.com platform
    - such as before object records are inserted into the database, or after records have been deleted.
2. workflow: 
    - Workflow enables you to set up workflow rules. 
    - A workflow rule identifies what kinds of record changes or additions trigger specified workflow actions, such as sending email alerts and updating record fields.
    - Workflow rules and actions are associated with a specific object (and can cross objects only to update fields on a related master record).
    - Workflow lets you automate standard internal procedures and processes to save time across your org. 
    - A workflow rule is the main container for a set of workflow instructions. These instructions can always be summed up in an if/then statement.
    - Workflow will perform operations after record creation/update, 
    - only on one object
3. visual workflow：
Visual Workflow enables you to create flows, which are triggered by users rather than events. Unlike Workflow, which always executes rules and actions behind the scenes, Visual Workflow offers screens for displaying and collecting information from the user running the flow.
4. workflow(outbound) vs process builder:
    - In short, you can do everything you can do with workflows using process builder as well, except for sending outbound messages with point&click. 
    - With process builder, you can also update all child records starting from the parent record, which is not possible with workflows (only vice versa is possible using cross object field updates). 
    - I've heard rumors that process builder will replace workflows in the future, which seems a logical step to take for sfdc.
5. Where to use trigger and where to use work flow?
    1. Workflow is point and click which doesn't need any coding. When you want to take action (email, task, field update or outbound message) for the same object or from Child to parent object, you can use Workflow rules.
    2. Trigger: It's a programmatic approach and event driven (insert, update, merge, delete). You can call it as advance version of Workflow.
    3. Trigger works across all the objects.
    4. You can create a new record through trigger which is not possible through workflow
    5. Workflows work only after some actions. Trigger works before and after some actions.
6. what are the differnt kinds of workflow actions:
    - new field update
    - new email alert
    - new task
    - new outbound message
7. types of email templates:
    - text 
    - HTML
    - custom template
    - visualforce
1. A customer service manager would like to automatically assign cases to the most appropriate agent to handle the request







## test & size
##### Roles:
1. DEV
    - back-end
    - front-end UI
2. UX
3. QA
    - manual testing
    - automation testing
4. BA
5. Architect 
6. Scrum Master - Team Leads
7. Project Manager
8. DBA
9. Delivery Manager

##### test(order)
- unit testing
- system testing
- smoke
- regression
- load/performance
- UAT user acceptance testing, client QA worked on this part
- production

##### Terms
- MOM minutes of meeting
- RCA root cause analysis
- IA impact analysis
