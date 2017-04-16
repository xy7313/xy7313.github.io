---
layout: post #post
title: Start from Java 5 #post title
categories: Java #post category, seperated by space
tags: Java #post tag, seperated by space
---

Class notes
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
    1. download tomcat --> right click in eclipse --> other --> create server --> apache tomcate
    2. new web dynamic web prj --> set target runtime == tomcat --> do not finish directly, click next, next and check the box with generate web.xml
    3. check doPost or doGet depends on your demand in somewhere
    3. create index.html in WebContent folder: index.html it the file we gonna show/run. (this is set in web.xml, we can commit the files we do not need)
    4. never check box: always use this server
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
        2. normal  ??`<% ... %>`
        3. expression `<%= aVariable %>`
    2. servlet, java html embedded, it has drawbacks, when we need complex html, so use jsp.
12. login.jsp, we need:
    1. create profile
    2. session: destroy is not for session, is for jsp life cycle
    3. connection only once, so we do not implement this part of java in normal .., for initialization propose, we implement in jsp init
    4. jsp life cycle (3) ?? : jsp init, jsp execute, cleanup
    5. connect db, so need convert to maven
13. we need : shift business logic in jsp to java class
14. response.sendDirect("index.html"). automatically redirect and send.
15. session.removeAttribution("name??")..if(session,attr()==null) ??  logout, we have a new session with a new sessionId, When we do not use cookie.
16. 4 scopes: request(default scope), page, session, application. request died, java object died, so if we remove scope = "session", the counter is always 1
17. if user login from different browser ==> we need a flag to mark if this user has logged in(or the new session replace the old session??)
18. useBean, setProperty associated with request, replace request.getParameter


1. directive
    - page
        - import (when want to import in jsp, we need directive page)
    - include
    - taglib
2. action page
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







## Question list
1. Difference between handling checked exceptions and handling unchecked exceptions
2. An Inner class defined within a method can access everything from outside the method but only final type of variables or objects from within the method in which it is defined.（wt??）
3. no private static?
4. only want 3 objs of a class
