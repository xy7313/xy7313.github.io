---
layout: post #post
title: Salesforce Some Test Questions And Answers #post title
categories: Salesforce #post category, seperated by spcace
tags: Salesforce #post tag, seperated by spcace
---




All content from the internet.
## Dashboard and Reports
1. reports:
    - summary of data that's stored in the application
    - There can be at most 5 custom summary formula fields are allowed on a single report.
2. report formats:
    - tabular reports: 
        1. tabular reports are the simplest form reports in salesforce. These are similar to spread sheet. 
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

## Field Level Security
1. restrict a profiles view to a certain field
2. Field Level Security or Page Layout can not be used to make a field required
3. Formulas ignore Field Level Security settings

## Case Assignment Rules
1. A customer service manager would like to automatically assign cases to the most appropriate agent to handle the request
2. 

## Simple Concepts
1. Bucket Field: Used in reports to categorise and group report values
2. Junction Object: A Many-to-Many relationship created with two lookup master-detail relationship
