---
layout: post #post
title: Salesforce Review #post title
categories: Salesforce #post category, seperated by space
tags: Salesforce #post tag, seperated by space
---


All content from: http://www.salesforce-interviewquestions.com/p/interview-questions.html, http://www.salesforcetutorial.com/salesforce-interview-questions-answers-part2/, http://www.jitendrazaa.com/blog/tag/interview-questions/


## Salesforce Fundamental questions, what's XX? 
1. What is Apex ?
Ans: It is the in-house technology of salesforce.com which is similar to Java programming with object oriented concepts and to write our own custom logic.
2. What is a Visualforce Page ?
Ans: Visualforce is the new markup language from salesforce, by using which, We can render the standard styles of salesforce. We can still use HTML here in Visualforce. Each visualforce tag always begins with “apex” namespace. All the design part can be accomplished by using Visualforce Markup Language and the business logic can be written in custom controllers associated with the Page.
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
10. 

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





## Apex basic
1. Standard controller & custom controller:
    - Standard controller: by using standard controller you need not have to write apex code. Standard controller can be accessed on one object and referenced by visualforce page. It also  provides some save, cancel, clone for that object. Standard controller provides the same functionality what standard pages provide
    - custom controller: A custom controller is an Apex class that implements all of the logic for a page without leveraging a standard controller. Use custom controllers when you want your Visualforce page to run entirely in system mode, which does not enforce the permissions and field-level security of the current user.
    - A controller extension 
        - is an Apex class that extends the functionality of a standard or custom controller. Use controller extensions when:
        - You want to leverage the built-in functionality of a standard controller but override one or more actions, such as edit, view, save, or delete.
        - You want to add new actions.
        - You want to build a Visualforce page that respects user permissions. Although a controller extension class executes in system mode, if a controller extension extends a standard controller, the logic from the standard controller does not execute in system mode. Instead, it executes in user mode, in which permissions, field-level security, and sharing rules of the current user apply.
        
## Web Service
2. How external app access salesforce?
    - apex rest api: when we want to expose apex classes and methods we use this so that external app can access you code through rest architecture. it supports both oauth and session id for authorization.
    - soap api: sf-soap: soap API. Salesforce provides a WSDL (Web Service Description Language) files. They are called "Enterprise WSDL" and "Partner WSDL". (https://help.salesforce.com/articleView?id=000004760&language=en_US&type=1) Enterprise, can not used for different users because of different data structure; partner wsdl, use any object, use general calls, more flexible, maybe need type cast, eg: phone
    - soap Vs. rest: rest faster than soap, rest can do all translate. rest and soap are protocol, soap only xml, rest can do both(xml,json),rest is much easier to develop, soap is secure with structured contract defined,
    rest is client based protocol, do CRUD operations, can work with any database, any data structure. SOAP message, define logic in soap message. SF support both. 
    - access sf:
        - login login.sf.com, a server called "login" dealing with login service
        - server give a token back, 
        - session id
    - when sf want to access other systems, the API we should choose depends on what protocol that system uses. sf have tool which can convert .wsdl/.rest file(in that system) into neighbor object.



## Security -- Who sees what:
3. what are sharing rules in salesforce?
    - Sharing rules are used by administrators to automatically grant users within a given group or role access to records owned by a specific group of users. Sharing rules cannot be added to a package and cannot be used to support sharing logic for apps installed from Force.com AppExchange.
    - Sharing rules can be based on record ownership or other criteria. You can’t use Apex to create criteria-based sharing rules. Also, criteria-based sharing cannot be tested using Apex.
    - All implicit sharing added by Force.com managed sharing cannot be altered directly using the Salesforce user interface, SOAP API, or Apex.
    - For example, use sharing rules to extend sharing access to users in public groups, roles, or territories. Sharing rules can never be stricter than your organization-wide default settings. They simply allow greater access for particular users.
3. Organization access:
    - IP Ranges(company level): Users outside the range are sent an activation code
    - IP Ranges(profile level): Users outside this range are denied access
    - Login Hours(profile level): specified hours are enforced
In Salesforce, permissions and access settings specify 
4. Object access: Profile
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
4. workflow vs process builder:
    - In short, you can do everything you can do with workflows using process builder as well, except for sending outbound messages with point&click. 
    - With process builder, you can also update all child records starting from the parent record, which is not possible with workflows (only vice versa is possible using cross object field updates). 
    - I've heard rumors that process builder will replace workflows in the future, which seems a logical step to take for sfdc.
 




self intro
1. 2 y exp of sf, 4 y of java,
2. tech: SalesForce: Sales Cloud, Service Cloud, Apex, Visual Force and Apex Data Loader. 
SOAP and REST API Web Services. 
2. good one tech
4. prj summary
5. diff rest/soap
6. org-default/sharing rules
7. profile/permission set:
8. workflow/trigger
9. migrate sandbox--production
10. 
