---
layout: post #post
title: Salesforce Interview questions and answers #post title
categories: Salesforce #post category, seperated by spcace
tags: Salesforce #post tag, seperated by spcace
---


All content from: http://www.salesforce-interviewquestions.com/p/interview-questions.html, http://www.salesforcetutorial.com/salesforce-interview-questions-answers-part2/, http://www.jitendrazaa.com/blog/tag/interview-questions/



1. What is Apex ?
Ans: It is the in-house technology of salesforce.com which is similar to Java programming with object oriented concepts and to write our own custom logic.
2. What is a Visualforce Page ?
Ans: Visualforce is the new markup language from salesforce, by using which, We can render the standard styles of salesforce. We can still use HTML here in Visualforce. Each visualforce tag always begins with “apex” namespace. All the design part can be accomplished by using Visualforce Markup Language and the business logic can be written in custom controllers associated with the Page.
4. Will Visual force still supports the merge fields usage like S-control ?
Visualforce Pages support embedded merge fields, like the {!$User.FirstName} used in the example.
6. What are Apex Governor Limits?
Governor limits are runtime limits enforced by the Apex runtime engine. Because Apex runs in a shared, multi-tenant environment, the Apex runtime engine strictly enforces a number of limits to ensure that code does not monopolize shared resources. Types of limits that Apex enforces are resources like memory, database resources, number of script statements to avoid infinite loops, and number of records being processed. If code exceeds a limit, the associated governor issues a runtime exception.
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
8. Cloud Computing is an approach to provide the following services -
    - SAAS (Software As A Service)
    - PAAS (Platform As A Service)
    - IAAS (Infrastructure As A Service)
9. Application build block:
    ||Declarative(simplicity+speed)|Programmatic(control+flexibility)|
    |Data model | Objects, fields, relationships | Web Service API, metadata API|
    |Business logic |  workflow, validation rules, approval process, assignment rules | Controllers, Apex, Web Service|
    |User Interface | record type, page layout, applications, tabs | Visualforce Page, Force.com Sites|