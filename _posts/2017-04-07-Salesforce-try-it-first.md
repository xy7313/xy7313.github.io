---
layout: post #post
title: Salesforce 1 -- Try It First #post title
categories: Salesforce #post category, seperated by spcace
tags: Salesforce #post tag, seperated by spcace
---

#### Intro of this series on Salesforce 
Notes from: https://trailhead.salesforce.com/trails 
All content from: https://trailhead.salesforce.com/trails 

## Start
1. what salesforce is?
    1. CRM
    2. marketing --> sale cloud + service cloud 
    3. account-opportunity
              -case
              -contacts-->lead
        when a lead convert to opporituny, it also become an account
    6. ?? md L account case/accout contacts
    7. ?? lkp  look up contact-lead, we delete contact, lead still there, we delete lead, contacts still there
    <!--8. can not pull data unless-->
    <!--9. can not get lead,  -->
    
## Trail

#### Trail Plan
1. Quick start: Create the Trailblazer App -- salesforce classic
2. Quick start: Create a New Process on the Account Object -- lightening process builder
4. admin beginner
3. crm essentials
4. admin intermediate

##### 1. Quick start: Create the Trailblazer App -- salesforce classic
1. Intro: build an app, which helps you on your personal journey to your local park — by keeping track of the places you want to go and the things you want to see. When you complete this quick start, you’ll have a working app with its own menu, a tab, and a custom object that tracks the names of places you want to visit.
1. When we want to build an app on the salesforce platform, there is a bunch of built-in functionality, such as:
    1. Database to organize information
    2. Security for protecting data and defining access across your organization
    3. Business logic to carry out particular tasks under certain conditions
    4. User interface to expose data and functionality
    5. Highly customizable mobile app
    6. Native social environment that allows you to interact with people or data
    7. Analytics and dashboards for viewing your data in meaningful ways
    8. Multiple APIs to integrate with external systems
    9. Ability to install or create third-party apps
2. When you create an app, you automatically create a data object. In Salesforce, we call that data object a custom object.（sheet/table）
3. Custom object:
    1. A custom object comes with standard fields and screens that allow you to list, view, and edit information about the object
    2. you can also add your own fields to track or list just about anything you can think of.
4. When you create an app with App Cloud, you automatically create a mobile version of the app.
5. For mobile app, Quick Actions are things you want to do immediately from your mobile device. These actions live in a special place called the Publisher. You can customize the Publisher so that your most important actions are there at your fingertips.
6. Salesforce has two different user interfaces: Lightning Experience and Salesforce Classic
7. Standard fields(after create new waypoint, we can see):
    1. Feed — The Chatter feed is where you see things you're interested in, like people, records, and groups. You can customize the feed to see exactly what you want to follow.
    2. Details — The ‘tab’-Waypoint custom object has four fields, the Name (I created) and three fields generated by the system (Created By, Owner, Last Modified By). As you build out your app, you can add more fields to refine the things you want to track.
    3. Activities — Activities are tasks and events associated with this record. Tasks are to-do items, and events are meetings. We don't go into Activities in this quick start, but keep it in mind, because it's a handy and powerful feature that you'll love.

8. Steps:
    1. Add APP
    2. Fill in the form( Plural Lable: pl of Lable)
    3. Create --> go to My App
    4. Create items of a tab 
    5. Change the heart symbol: Setup --> Create --> Tabs --> Edit
    6. For mobile: 
        1. create quick action: create --> global actions --> global actions --> new action --> target object: your tab name( waypoint )
        2. add that Quick Action to the Publisher:  Create --> Global Actions --> Publisher Layouts --> drag(Remove action by dragging it up to the Global Layout area, add action by dragging it from the Global Layout and dropping it into the Global Publisher below.)
        3. /one/one.app

##### 2. Quick start: Create a New Process on the Account Object -- lightening process builder
1. Intro: Lightning Process Builder is a workflow tool that helps automate business processes without writing a single line of code. This quick start creates a new process that updates Contact records whenever the Account billing address changes
2. Process Builder allows you to choose not just fields on Accounts, but fields that are related to Accounts.
3. you could add multiple actions for one criteria.
8. Steps:
    1. Search builder and select process builder --> click new -->type name --> when start: a record changes --> save --> +add project
    2. Process Criteria： 
    3. Process Action: 




## you know

1. resist the temptation to think ...
2. the golden rule is to always do ...
3. give you more granular control of customization
4. or vice versa
5. If you see a spinning wheel, your .. is still being processed
6. Speed up the onboarding process with a
7. Time off tracking
8. Assign work to queues and use Chatter to collaborate on requests, and track everything in
9. at an aggregate level.
10. versatile
11.  a user’s Salesforce account may have been compromised
12. find root cause
13. Important for both security tracking purposes and adoption
14. Sandboxes are a vital tool for administrators and developers and a worthwhile investment;
15. view all future jobs, including Apex jobs, dashboard refreshes, and reporting snapshots.
16. These are your primary stakeholders for 。。。
17. What are your main pain points at present?
18. What is your budget/timeline?
19. Before you can make your own app or service publicly available to potential customers,
20. paint yourself in to corner with that strategy
21. Remember before you roll out a new app get your users ready. To do that you will want to message out the change that is coming to the relevant users and when it will be coming.
22. Each table comprises a number of columns
23. square bracket
24. rollup  summary
25. start a group for a customer visit 
26. to align everyone.
1. engage them in helping drive Chatter success.
2. For Chatter to soar you need great content and a sense of community. You need a Community Manager curating quality content and driving user engagement
1. track data related to all of your interactions.
1. brush up on their needs and buying history,
1. are like a forgotten boat adrift at sea
1. deals usually progress from tentative to firm before they’re finalized
1. the likelihood that he will buy from you probably increases
1. stop by your booth at a conference
1. you mosey on over to your laptop, crack open a refreshing beverage, generate a few Salesforce reports, and enjoy the shower of praise
1. She appreciates your keen insight,
1. each department uses its own source of truth for that contact info
1.  an intricate system
1. You try your best to find two departments that use the same process for creating records, but you’d have more luck finding a vegetarian at a pig roast.
1. it’s no wonder your reports are riddled with duplicates, incomplete records, and stale data.
1. Knowing how your company uses data to support its objectives is great. But it’s about as useful as a VHS tape in a Roku if you can’t get the data into an accessible and useful format 
1. Every department was tasked with using Salesforce as the source of truth for data
0. Yes, that’s really it!
0. This ensures you can balance security and convenience, minimizing the risk of stolen or misused data while making sure all users can easily access the data they need.
0. limiting when and from where users can log in
0. escalated = increased