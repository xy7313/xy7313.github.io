---
layout: post #post
title: Salesforce2 Admin Beginner#post title
categories: Salesforce #post category, seperated by spcace
tags: Salesforce #post tag, seperated by spcace
---

## 3. TRY TRAIL: Admin Beginner
##### 1. Salesforce Platform Basics
1. CRM : a place to store your customer data, processes to nurture and convert prospective customers, and ways to collaborate and engage
2. Salesforce is CRM, it also includes the platform, where customers and partners can use our suite of technologies to build amazing, connected apps.
3. Terminology
    1. Record: an item you are tracking in your database -- a row on the spreadsheet.
    2. Field: a place where you store a value, like a name or address -- a column on the spreadsheet.
    3. Object: a table in the database -- a tab on the spreadsheet
    4. Org: short for "Organization", the place where all your data, configuration, and customization lives -- your instance of Salesforce. you and your user log in to access it.
    5. Force.com: The suite of configuration tools and programming languages, and APIs native to Salesforce, including Apex and Visualforce
    6. App: A set of fields, objects, permissions, and functionality to support a business process. Not a thing you download onto your phone.
        1. example: if you’re having an event and you want people to sign in,  you could create an Event app in Salesforce. The process/entity becomes an object (‘Event’), and those columns become fields (‘Attendee Name’, ‘Title’, ‘Company’, ‘Email’) on the object.
        2. benefits:
            - Get real-time access to data as it’s entered, via mobile or desktop.
            - Create reports and dashboards to analyze attendees.
            - Send follow up emails to attendees after the event.
            - Relate attendees to marketing campaigns and sales information including order and purchase information.
            - Engage with attendees in a community.
            - Create automated processes to engage with the attendees over time.
            - Take advantage of instant scalability, instant mobile access, secure data storage and backups.
            - And much, much more
4. An example using platform:
    1. scenario:
    2. solution: create a custom field for preferred phone number, and add a new section on the page layout [1] just for phone numbers and your new custom field.
4. define declarative and programmatic development：
    1. Declarative refers to point-and-click functionality in Salesforce. It means that you can configure and customize Salesforce without writing code.
    2. Programmatic refers to code-driven functionality in Salesforce. It means that you can customize Salesforce using programmatic tools like Apex, Visualforce, and Lightning, and standard web technologies like JavaScript, CSS, and more.
5. the golden rule is to always try to build with clicks before going to code, as it is more sustainable and maintainable moving forward.
6. tips for identifying good processes to bring onto the platform
    1. reliance on spreadsheets
    2. Collaboration via email
    3. Documents shared on local file directories
    4. Time-intensive, manual steps
    5. Impact to a few departments maximum (just as you’re getting started; keeping your number of stakeholders to a minimum will help you make progress)
7. Architecture
    1. Trusted Multitenant Cloud:  
        1. protecting your data
        2.  Using standard functionality in Salesforce, you get a fine degree of security control over everything from user and client authentication, through administrative permissions to the data access and sharing model.
        3. advantage of a multitenant cloud: all of our customers, from small businesses to enterprise companies, are on the same code-base and all get the benefits of the same features, functionality, and automatic upgrades 3 times a year. (Salesforce’s upgrades are automatic and seamless)
        4. The cloud also means we can deliver Software as a Service (SaaS), which is important because it means you don’t have to install a program to use Salesforce. You just need an internet connection to log in.
    2. Scalable metadata platform: the structure of your Salesforce org
        1. imagine all of that data has just been exported. The structure is still there, but the data itself is gone. What you’d have left, that underlying structure, that is the metadata. It’s all of your standard and custom functionality, and all of your configuration and code.
        2. Salesforce’s SaaS model means we make the metadata immediately available for development, configuration
    3. fast app dev and customization: There is no installation of hardware and software, and there are standard options for defining security and user access, creating reports, and making the app social and mobile.
    4. largest enterprise ecosystem
    5. complete CRM
    6. API (Application Programming Interface): 
        2. it’s essentially a contract between two pieces of software, allowing them to connect to each other and exchange information (without knowing any of the inner details of how they work.)
        1. he API name is a unique identifier that the platform uses to determine what data or metadata you are trying to access.
8. Setup： 
    1. Setup consists of a tab bar, a navigational sidebar, and a main window. 
    2. Setup Search uses type-ahead functionality to help you jump quickly to the item you want. advanced search
    3. If you’re not at your desk and you need to get your admin duties on, you can take Setup on the go with the SalesforceA mobile app.
        1. Username
        2. Super secret password
        3. ?? Correct instance: You can connect to a sandbox environment for testing purposes, or a custom domain if configured for your org
    4. trust.salesforce : The Recent System Status section shows information from trust.salesforce.com about your instance's system performance over the last 24 hours. 
9. develop your AppExchange strategy: all from- https://trailhead.salesforce.com/trails/force_com_admin_beginner/modules/starting_force_com/units/starting_developer_console 
    1. Identify the departments using Salesforce (either now or in the future). These are your primary stakeholders for AppExchange app installations.
    2. Research AppExchange apps for the business cases provided by your stakeholders. Interview your stakeholders thoroughly to gather the requirements needed to select and evaluate the apps.
        1. What business problem are you trying to solve?
        2. What are your main pain points at present?
        3. How many users?
        4. What is your budget?
        5. What is your timeline?
    1. Download apps into a sandbox or Developer Edition org for preview and testing. An important step is to ensure that the app you’re installing doesn’t interfere with any customizations you’ve done or other apps you’ve already installed.
        2. Sandboxes are copies of your organization in a separate environment. They are used for development and testing： https://help.salesforce.com/articleView?id=create_test_instance.htm&language=en_US&type=0 4 types: developer sandbox, dev pro sandbox(lager tata sets), partial copy sandbox(includes a sample of your production org’s data as defined by a sandbox template), full sandbox(support performance testing, load testing, and staging,  a replica of your production org, including all data, But the length of the refresh interval makes it difficult to use Full sandboxes for development.) **We recommend that you apply a sandbox template so that your sandbox contains only the records that you need for testing or other tasks.**
    4. Evaluate your choices. Consider budget, app functionality, and any feature gaps. Consider inviting your stakeholders into the sandbox or Developer Edition org to preview the app functionality, or invite your stakeholders to a demo of the app.
    5. Execute and document. Prepare your users for the change in user experience (if any), including providing training or documentation as needed
10. Install from AppExchange:
    1. In general, an AppExchange best practice is to install first in a sandbox or Developer Edition org. A few considerations:
        1. Some of the packages come bundled with custom fields, objects, Apex classes, and more.
        2. All of these customizations have names, which may conflict with existing names in your org.
    2. give permissions to admins only, all users, or specific profiles
    3. The AppExchange is a complete marketplace offering cloud-computing applications and consulting services

##### 2. Data Modeling
1. There are two types of objects.
    1. Standard Objects—These are objects included with Salesforce, by default, for example the objects used to store data in standard tabs such as accounts, contacts, or opportunities.
    2. Custom Objects—These are new objects you create to store information unique to your organization. Custom objects extend the functionality that standard objects provide. **For example, if you’re building an app to track product inventory, you can create custom objects called Merchandise and Invoices, as shown in the figure below.**
2. Objects can have relationship fields that define how records in one object relate to records in another object. These fields play the same role as primary and foreign keys in a database
3.  All attributes of an object are described with metadata, making it easy to create and modify records either through a visual interface or programmatically.
6. Fields
    1. Identity Field：
        - called ID
        - manages the identity data in every record
        - as a result you can view every record (across all objects) by simply using a URL of the above form
        - eg: https://yourInstance.salesforce.com/0015000000Gv7qJ
    2. System Fields
        - All objects have a number of read-only system fields automatically associated with them. eg: CreatedDate, LastModifiedById
    3. Name Fields:
        -  required field that has a special place in the life of the object
        -  It's not required to be a unique identifier, but it is supposed to be the primary way users distinguish one record from another
        - A name can be one of two types: a text string or an auto-number field.
            - auto-number field, you must specify the format for the field and the starting number. Auto number fields increment by one each time a record is created.
    4. Custom Fields: . All fields in an object must be defined as a particular data type. more here: https://www.adminhero.com/a-primer-on-salesforce-fields-and-relationships/
    5. Relationship Fields: stores the ID of the parent record in a relationship
        1. Lookup: Lookup relationships can be used to create one-to-one and one-to-many relationships.
        2. Master-Detail: 
            - Master-detail relationships can be used whenever there is a tight binding between two objects.
            - They can also be used to create many-many relationships.
            - The master object in a master-detail relationship can also contain rollup summary fields : store values aggregated from the child records in the relationship
    5. Other Features of Objects
        1. formulas (rich expression ) - set up validation rules,create workflow rule criteria
        2. validation
        3. triggers, written in the Apex language
        4. Labels—Every object and record has a label and can include a description, for help, which is automatically included in the user interface.
        5. Notes and attachments
        6. Track Field History
7. When create a new object and customize fields
    1. unique naming
    2. thoughtful architecture: the cleanest and most efficient way to capture data
    3. Default field values: Don’t assign default values to fields that are both required and unique, as this can cause uniqueness errors.
    4. Careful renaming
    5. Global data updates:
    6. help for users: help text of field and help page for an object
8. When create object relationships:
    1. With relationships, you can display data about other related object records on a particular record's detail page.
    2. A relationship field stores the ID of the parent record in a relationship, as well as optionally providing user interface representations in both the parent and child records.
    3. lookup -- an example: 
        - a lookup relationship field on a job application object, reference position records. 
        - this will be reflected both with a new Position field on the job application record and with a new Job Applications related list on the position record
        - You can also put multiple lookup relationship fields on a single object, which means that the Job Application object can also point to a Candidate object.
    4. master-detail: （created on obj-child/detail, related to obj-parent/master）the master record controls certain behaviors of the detail and subdetail record.
        - the ownership and sharing of detail records are determined by the master record, and when you delete the master record, all of its detail records are automatically deleted along with it. Master-detail relationship fields are always required on detail records.
        - For example, say your recruiting app has a Review custom object that contains an interviewer's feedback on a job application. If you delete a job application record, you will probably want all of its review records deleted as well. In this case, you would create a master-detail relationship on the Review custom object with the Job Application object as the master object.
        - rollup summary fields. These fields store values aggregated from the child records in the relationship
    5. differences:
    6. convert: You can convert a master-detail relationship to a lookup relationship as long as no roll-up summary fields exist on the master object. You can convert a lookup relationship to a master-detail relationship, but only if the lookup field in all records contains a value.
    7. User is a standard object that comes with all organizations on the platform. It contains information about everyone who uses the app in your organization.
    8. ou can also create a hierarchical relationship between objects. A hierarchical lookup relationship is available only for the user object.
        - For example, create a custom hierarchical relationship field to store each user's direct manager.
    9. many-to-many
         - For example, suppose your recruiting app has a custom object called Website that stores information about various employment websites. You want to track which open positions are posted to those sites. Use a many-to-many relationship because:
            - One position could be posted on many employment websites.
            - One employment website could list many positions.
        - Instead of creating a relationship field on the Position object that directly links to the Website object, we can link them using a **junction object**. A junction object is a custom object with two master-detail relationships, and is the key to making a many-to-many relationship.
9. Schema Builder



##### 04/14 Security
advantages workflow has compared to process
single task --  workflow, one object

preview
1. master-detail, change one object that will impact another: 2examples: 1. master rollup summary field, child amount changes, this field of master changes; 2. delete master, child gone
2. advantage of having dashboard: give you a very quick glance on what is going on 

main topic:
1. part all users in specific groups, defined in profile 
2. profile is a field? some value i can choose is account,case,...??
3. public r/w, public r/only, private ..
4. lock down on object level
5. user profile, standard profile can not be changed, if our demand is similar like standard setting, we make some changes by permission set, if we have totally different demand, we create a new profile
6. share
7. record type: ..account, for each record type, we can have a business layout. subject to profile


##### 04/17 developer beginner--apex

1. declaratively configuration before
2. an example declarative then Programmatic:
    1. new object
    2. new custom field, lookup relations, relate to account
    3. new a couple of fields there
    4. create a custom tab
    5. when want to show information of account on the current page
    6. model(your database) + view + controller(in the middle): salesforce have some built in functions.
    7. apex class -- controller, can put any objects on the same page. manipulate the logic, how the data display
    8. apex standardController = "Account" + relatedlist + id in url,

## Question list
1. data model, create object relationships, resulting API name: trail_c, all custom fields API name: fields1_c...(why? I have not set it)：https://trailhead.salesforce.com/trails/force_com_admin_beginner/modules/data_modeling/units/creating_custom_objects_fields
2. relationship between position and job application. a new Position field ((means the lookup relationship field)) on the job application record ： https://trailhead.salesforce.com/trails/force_com_admin_beginner/modules/data_modeling/units/object_relationships
3. profile permission: permission is field of profile obj? or field of the obj we want to access?





