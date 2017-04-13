---
layout: post #post
title: Start from Java 5 #post title
categories: Java #post category, seperated by space
tags: Java #post tag, seperated by space
---


## Java Server Pages(JSP)
1. server side , java platform
    1. CGI
    2. Perl
    3. Servlets
    4. JSP: ont top of servlet, every JSP has servlet, technically
    5. other platforms: PHP, ASP.net
2. Servlet: primary implementation in java platform to show html
3. Web containers / web servers:
    1. Tomcat
    2. jetty
    3. apache
    4. JavaWebServer
4. Application servers: - Enterprise Architecture
    1. JBoss
    2. WebLogic
    3. WebSphere
    4. Glassfish
    5. Oracle Java EE Server
5. technical difference between 3, 4, 4, scalable, all can use 3, also can use 4. Some 3 can not handle, use 4
6. all applications we run was desktop applications.
7. a web proj:
    1. webContent
        - *.html
        - *.jsp
        - style folder
            - *.css
        - script folder
            - *.js
        - images
            - *.png...
        - WEB-INF
            - web.xml
                - *.JAR
            - classes folder
                - *.class files of entire source files
            - *.tld
    2. src
        - all java source packages and files (*.java)
            - Business layer files
            - Controller classes
            - service / DAO layer
            - Servlets, are also called controller
            - POJO / Model Objects / ORM (object oriented mapping)
        - *.xml
        - *.properties
        - *.json
    3. pom.xml    
9. Steps:
    1. dwon load tomcat --> right click in eclipse --> other --> create server --> apache tomcate
    2. new web dynamic web prj --> set target runtime == tomcat --> do not finish directly, click next, next and check the box with generate web.xml
    3. check doPost or doGet depends on your demand in somewhere
    3. create index.html in WebContent folder: index.html it the file we gonna show/run. (this is set in web.xml, we can commit the files we do not need)
10. Two ways :
    1. jsp: html with java embedded
        1. declaration tag, global variable, eg: 
        ```
        <head> 
            <%! 
                Connection con; 
            %> 
        </head>
        ``` 
            1. !
            2. only once
            3. must in <head></head>
        2. normal  `<% ... %>`
        3. expression `<%= aVariable %>`
    2. servlet, java html embedded, it has drawbacks, when we need complex html, so use jsp.

12. login, 
    1. create profile
    2. session
13. we need : shift business in jsp to java class
    1. wt not to do:

1. directive
    - page
        - import (when want to import in jsp, we need directive page)
    - include
    - taglib
2. action tage
    - use Bean
    - setProperty
    - getProperty
    - forward 
    - include
3. taglibs
    - 
4. implicit object
    - request
    - response
    - session
    - out
    - pageContent