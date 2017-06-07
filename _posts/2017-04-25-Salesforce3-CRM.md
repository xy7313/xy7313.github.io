---
layout: post #post
title: Salesforce 3 -- CRM Essential #post title
categories: Salesforce #post category, seperated by space
tags: Salesforce #post tag, seperated by space
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










