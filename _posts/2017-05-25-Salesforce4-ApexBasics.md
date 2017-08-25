---
layout: post #post
title: Salesforce 4 -- Apex Basics #post title
categories: Salesforce #post category, seperated by space
tags: Salesforce #post tag, seperated by space
---


Notes from: https://trailhead.salesforce.com/trails 
All content from: https://trailhead.salesforce.com/trails 

## 5. Developer Beginner （ Get the platform developer1 certificate, yay!）

###### 1. Formula Fields
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

###### 2. Data Security
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

###### 3. Process Automation
- Salesforce provides multiple tools to automate your org’s repetitive business processes: **Lightning Process Builder, Visual Workflow, Workflow, and Approvals**. 
- Process and workflow: In fact, a single process can do what it would normally take multiple workflow rules to do. The only thing you can do with workflow that you can’t do with processes is send outbound messages without code.
- If the process is too complicated for the Process Builder or requires more advanced functionality, create a flow by using the Cloud Flow Designer.
- If you need to build a wizard to collect information, Visual Workflow is the tool for you.  Create a flow that displays information to and requests information from a user. Then take the information that they enter and perform actions in Salesforce with it.
- a useful table(https://trailhead.salesforce.com/trails/force_com_dev_beginner/modules/business_process_automation/units/process_whichtool)
- Do I need to get information from a user? -if yes, use visual workflow, if no, use process builder
- Whenever possible, automate your if/then statements with Process Builder instead of workflow rules.
- When a user first requests approval for a new position, initial submission actions occur. The default initial submission action locks the record. This action ensures that other users (except for approvers and administrators) can’t change the record while the record is pending approval.
- tasks: 
    - In some instances, a case must automatically escalate. Create a workflow rule that will set the escalated flag and send a task to the case owner if a case is not closed and its priority is set to High.
    - You've been given a requirement to keep Contact addresses in sync with the Account they belong to. Use Process Builder to create a new process that updates all child Contact addresses when the address of the Account record is updated. 

###### 4. Apex Basics：
1. Apex supports:
    - classes, interfaces, properties, collections
    - Object array notation
    - Expressions, variables, and constants
    - Conditional statements (if-then-else) and control flow statements (for loops and while loops)
    - Cloud development as Apex is stored, compiled, and executed in the cloud.
    - Triggers
    - soql
    - Transactions and rollbacks
    - The global access modifier
2. Data type:
    - primitives: Integer, Double, Long, Date, Datetime, String, ID, Boolean, among others
    - sObject
    - collection: list, set, map
    - A typed list of values, also known as an enum
    - User-defined Apex classes
    - System-supplied Apex classes
3. List
    - declaration:`List<String> colors = new List<String>();` or `String[] colors = new List<String>();`
    - Get elements from a list
        ```
        String color1 = moreColors.get(0);
        String color2 = moreColors[0];
        System.assertEquals(color1, color2);
        ```
    - List elements can be read by specifying an index between square brackets, just like with array elements. Also, you can use the get() method to read a list element. 
4. sObject
    - doc: https://developer.salesforce.com/docs/atlas.en-us.206.0.object_reference.meta/object_reference/sforce_api_objects_concepts.htm 
    - add fields: `Account acct = new Account(Name='Acme');`
5. DML(Data Manipulation Language)
    - insert/update/upsert/delete/undelete/merge
    - The **upsert** DML operation creates new records and updates sObject records within a single statement, using a specified field to determine the presence of existing objects, or the ID field if no field is specified.
    - The **merge** statement merges up to three records of the same sObject type into one of the records, deleting the others, and re-parenting any related records.
6. You can perform DML operations either on a single sObject, or in bulk on a list of sObjects. 
7. BULK - Performing a DML operation on a list of sObjects counts as one DML statement for all sObjects in the list, as opposed to one statement for each sObject.
8. **upsert** `upsert sObjectList Account.Fields.MyExternalId;` Upsert uses the sObject record's primary key (the ID), an idLookup field, or an external ID field to determine whether it should create a new record or update an existing one:
9. upsert example
    ```
    Contact jane = new Contact(FirstName='Jane',
                            LastName='Smith',
                            Email='jane.smith@example.com',
                            Description='Contact of the day');
    insert jane;

    // 1. Upsert using an idLookup field
    // Create a second sObject variable.
    // This variable doesn’t have any ID set.
    Contact jane2 = new Contact(FirstName='Jane',
                            LastName='Smith',  
                            Email='jane.smith@example.com',
                            Description='Prefers to be contacted by email.');
    // Upsert the contact by using the idLookup field for matching.
    upsert jane2 Contact.fields.Email;

    // Verify that the contact has been updated
    System.assertEquals('Prefers to be contacted by email.',
                    [SELECT Description FROM Contact WHERE Id=:jane.Id].Description);
    ```
10. **Deleted** records aren’t deleted permanently from Force.com, but they’re placed in the Recycle Bin for 15 days from where they can be restored.
11. DML Statement Exceptions `DmlException e;     e.getMessage();`
12. These Database methods are static and are called on the class name. eg: `Database.insert(recordList, false);`
13. Database methods have an optional allOrNone parameter that allows you to specify whether the operation should partially succeed. 
    - When this parameter is set to **false**, if errors occur on a partial set of records, the successful records will be committed and errors will be returned for the failed records. `Database.insert(recordList, false);` 
        - Also, no exceptions are thrown with the partial success option.
        - `Database.SaveResult[] results = Database.insert(recordList, false);` //The Database methods return result objects containing success or failure information for each record. For example, insert and update operations each return an array of Database.SaveResult objects.
    - By default, the allOrNone parameter is **true**, which means that the Database method behaves like its DML statement counterpart and will throw an exception if a failure is encountered.
    - In addition to these methods, **the Database class contains methods that aren’t provided as DML statements**. For example, methods used for transaction control and rollback, for emptying the Recycle Bin, and methods related to SOQL queries. 
14. when use which one?
    - Use DML statements if you want any error that occurs during bulk DML processing to be thrown as an Apex exception that immediately interrupts control flow (by using try. . .catch blocks).
    - Use Database class methods if you want to allow partial success of a bulk DML operation—if a record fails, the remainder of the DML operation can still succeed. 
15. SOQL：`Account[] accts = [SELECT Name,Phone FROM Account];` // wrap the SOQL statement within square brackets and assign the return value to an array of sObjects.
16. perform fuzzy matches by using the LIKE operator. For example, you can retrieve all accounts whose names start with SFDC by using this condition: WHERE Name LIKE 'SFDC%'. The % wildcard character matches any or no character. The _ character in contrast can be used to match just one character.
17. To get child records related to a parent record, add an inner query for the child records.
18. Inner Query: //To get child records related to a parent record, add an inner query for the child records. 
    ```
    Account[] acctsWithContacts = [SELECT Name, (SELECT FirstName,LastName FROM Contacts)
                                FROM Account 
                                WHERE Name = 'SFDC Computing'];
    // Get child records
    Contact[] cts = acctsWithContacts[0].Contacts;
    System.debug('Name of first associated contact: ' 
                + cts[0].FirstName + ', ' + cts[0].LastName);
    ```
19. You can traverse a relationship from a child object (contact) to a field on its parent (Account.Name) by using dot notation.
    ```
    Contact[] cts = [SELECT Account.Name FROM Contact 
                    WHERE FirstName = 'Carol' AND LastName='Ruiz'];
    Contact carol = cts[0];
    String acctName = carol.Account.Name;
    System.debug('Carol\'s account name is ' + acctName);
    ```
20. Querying Record in Batches By Using SOQL For Loops
    ```
    insert new Account[]{new Account(Name = 'for loop 1'), 
                     new Account(Name = 'for loop 2'), 
                     new Account(Name = 'for loop 3')};

    // The sObject list format executes the for loop once per returned batch
    // of records
    Integer i=0;
    Integer j=0;
    for (Account[] tmp : [SELECT Id FROM Account WHERE Name LIKE 'for loop _']) {
        j = tmp.size();
        i++;
    }
    System.assertEquals(3, j); // The list should have contained the three accounts
    System.assertEquals(1, i); // Since a single batch can hold up to 200 records and, only three records should have been returned, the loop should have executed only once
    ```
21. Salesforce Object Search Language (SOSL) is a Salesforce search language that is used to perform text searches in records. SOSL is similar to Apache Lucene.
22. `List<List<SObject>> searchList = [FIND 'SFDC' IN ALL FIELDS   RETURNING Account(Name), Contact(FirstName,LastName)];` //When SOSL is embedded in Apex, it is referred to as inline SOSL, searches for accounts and contacts that have any fields with the word 'SFDC'.
23. SOQL Vs. SOSL
    - Like SOQL, SOSL allows you to search your organization’s records for specific information. Unlike SOQL, which can only query one standard or custom object at a time, a single SOSL query can search all objects.
24. syntax of SOSL: `FIND 'SearchQuery' [IN SearchGroup] [RETURNING ObjectsAndFields]` 
    - **SearchQuery** is the text to search for (a single word or a phrase). Search terms can be grouped with logical operators (AND, OR) and parentheses. 
    - search terms can include wildcard characters (*, ?). The * wildcard matches zero or more characters at the middle or end of the search term. 
    - The ? wildcard matches only one character at the middle or end of the search term.
    - **SearchGroup** can take one of the following values: ALL FIELDS, NAME FIELDS, EMAIL FIELDS, PHONE FIELDS, SIDEBAR FIELDS
    - **ObjectsAndFields** is optional. It is the information to return in the search result—a list of one or more sObjects and, within each sObject, list of one or more fields, with optional values to filter against. If not specified, the search results contain the IDs of all objects found.
25. example of SOSL : 1.  `...RETURNING Account(Name, Industry WHERE Industry='Apparel')` //filter
    2. 
    ```
    List<List<sObject>> searchList = [FIND 'Wingo OR SFDC' IN ALL FIELDS 
                   RETURNING Account(Name),Contact(FirstName,LastName,Department)];
    Account[] searchAccounts = (Account[])searchList[0];
    Contact[] searchContacts = (Contact[])searchList[1];
    ```




















## Security Specialist
1. Here are the three protocols that Salesforce and other identity vendors follow to implement identity solutions.
    - SAML（SAML is an XML-based protocol）
    - OAuth 2.0
    - OpenID Connect






## Sens:
1. Operating on a list of sObjects is a more efficient way for processing records.
2. All those statements, except a couple, are familiar database operations.
3. can be quite handy.
4. using a specified field to determine the presence of existing objects, or the ID field if no field is specified.
5. In addition to persisting the ID value in the database, the ID value is also autopopulated on the sObject variable that you used as an argument in the DML call.
6. The fields are specified after the SELECT keyword in a comma-delimited list.
