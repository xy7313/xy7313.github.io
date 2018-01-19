---
layout: post #post
title: Web Technologies + DB/SQL + Linux/unix #post title
categories: Web #post category, seperated by space
tags: Web Interview DB #post tag, seperated by space
---


index:
###### [1. web](#jump1)
###### [2. algorithm](#jump2)
###### [3. DB/SQLy](#jump3)
###### [4. Linux/unix](#jump4)
###### [5. OS](#jump5)
###### [6. OOD](#jump6)
###### [7. VCS - Git](#jump7)

<span id="jump1"></span>

## web tech

- The communication protocols, 
- languages/APIs, 
- other mechanisms that enable the internet to function. 
- HTTP, 
- Browsers, 
- DNS, 
- HTML/XML, 
- AJAX, etc
- [routers](https://www.lifewire.com/how-routers-work-816456) 
    - Routers are small electronic devices that join multiple computer networks together via either wired or wireless connections.
    - By maintaining configuration information in a part of memory called the routing table, routers also can filter both incoming or outgoing traffic based on the addresses of senders and receivers.
- Cookies
- DNS: domain name servers, 
- Load balancers, 
- firewalls, 
- Knowledge of Front End programming languages (HTML, CSS, JavaScript), 
- protocols (HTTP and TCP/IP) and 
- general understanding of how the internet works. 



#### 1. HTTP
1. HTTP/1.1 
    - stands for Hypertext Transfer Protocol.
    - stateless, (does not keep state between different message exchanges.)
    - application-layer protocol for communicating between distributed systems
    - is the foundation of the modern web.
    - allows for communication between a variety of hosts and clients
    - support a mixture of network configurations
    - usually takes place over TCP/IP
    - port:80. https port:443
    - 1.1 new features: persistent connections, chunked transfer-coding and fine-grained caching headers
    - HTTP allows servers to **redirec**t a client request to a different location. 
        - If content has moved to a different URL or domain name, redirection can be used to avoid breaking old URLs or bookmarks.
        - It is possible to convert a POST request to a GET request using redirection.

    - communication between a host and a client occurs, via a request/response pair
        - client initiates an HTTP request message and get a http response in return
    - [http1, url, status code, verbs, ajax,Request and response headers](https://code.tutsplus.com/tutorials/http-the-protocol-every-web-developer-must-know-part-1--net-31177)
    - [http2, connections,Caching, connection handling and authentication.](https://code.tutsplus.com/tutorials/http-the-protocol-every-web-developer-must-know-part-2--net-31155)

#### 2. utf-8 vs. unicode
2. Unicode assigns each character a unique number, or code point.
3. UTF-8 is a character encoding - a way of converting from sequences of bytes to sequences of characters and vice versa.
4. UTF is a type of encoding that uses a variable number of bytes per character, UTF-8 means the unit size is 8 bits. 
The standard then defines a few of these bits as flags: if they're set, then the next unit in a sequence of units is to be considered part of the same character.
4. UTF-8 encodes each valid code points in Unicode using one to four 8-bit bytes.[9] Code points with lower numerical values, which tend to occur more frequently, are encoded using fewer bytes.
3. Communications protocols such as HTTP tend to work best with UTF-8, as the unit size in UTF-8 is the same as in ASCII,.
1. UTF-8 is a particular way of encoding Unicode.

#### 3. What happens after you typed a URL in your browser and pressed return key?

- goal：You type in the URL and hit go. The browser needs to translate that URL www.somesite.com into an IP address so it knows what computer on the internet to connect to
- pre/assumption: In an extremely rough and simplified sketch, assuming the simplest possible HTTP request, no proxies, IPv4 and no problems in any step:

- So your browser will see if it already has the appropriate IP address cached away from previous visits to the site.
- If not, it will make a DNS query to your DNS server (might be your router or your ISP’s DNS server)
- Once your browser knows what IP to use, it will connect to the appropriate webserver and ask for the page. 
- The webserver then returns the requested page and your browser renders it to the screen.

#### 4. TCP/IP
1. Host A sends a TCP SYNchronize packet to Host B

2. Host B receives A's SYN

3. Host B sends a SYNchronize-ACKnowledgement

4. Host A receives B's SYN-ACK

5. Host A sends ACKnowledge

6. Host B receives ACK. 
7. **TCP socket connection is ESTABLISHED.**

[graph here](http://www.tcpipguide.com/free/t_TCPConnectionEstablishmentProcessTheThreeWayHandsh-3.htm)

three frames.

- SYN: This is the synchronization phase. This TCP segment sets the sequence number to be used for the upcoming data transfer.

- SYN-ACK: The reply from the remote host does two things: Verifies the sequence number that will be used. Acknowledges the original request.

- ACK: This data is sent from the originating host, and acknowledges the sequence number and the acknowledgement from the targeted host.


#### 5. how Cookies are used by web companies both to the advantage of the user and the company itself (e.g. ads).
1. Cookies are pieces of information generated by a Web server and stored in the user's computer, ready for future access. Cookies are embedded in the HTML information flowing back and forth between the user's computer and the servers. Cookies were implemented to allow user-side customization of Web information. 
2. benifits/advantage/pros
    - Cookies allow a web application to respond to you as an individual. 
    - By gathering and remembering information about your preferences, the web application can tailor its operation to your needs, likes and dislikes. 
    - cookies allow web developers to create better web applications，which are more personal, easier to use.
    - Conveniency: Cookies can make filling out address forms quick and efficient. Most online shopping websites nowadays allow cookies for address and email information
    - Personalization: Amazon uses cookies to offer you related products, Google uses cookies to better understand your searches,
    - Effective Advertising
    - Ease of Control: It is actually really easy to manage your cookies if you know how. Most browsers make it easy for you to clear your browsing history. 
4. disvantage/cons
    - Privacy: The main concern for most users is privacy. Cookie enabled web browsers keep track of all the websites you have visited. This means that with permission, third parties can access the information stored by these cookies. These third parties can be advertisers, other users, or even the government in some cases.
    - Security: Cookie security is a large problem. The concern is that many security holes have been found in different browsers. Some of these holes were so serious that they allowed malicious webmasters to gain access to users’ email, different passwords, and credit card information.
    - Secrecy: Although third party cookies can be blocked through your browser settings, most people don’t have the technical expertise to do this. Most browsers purposely make it difficult to find this setting in order to prevent you from turning them off. No cookies mean no data, which in turn means less money.

#### 8. HTTP pipelining/persistence, 
ref: [pipelining](https://brianbondy.com/blog/119/what-you-should-know-about-http-pipelining)
- **HTTP pipelining** HTTP pipelining is a feature of HTTP 1.1 persistent connections. It is a technique in which multiple HTTP requests are sent on a single TCP connection without waiting for the corresponding responses.
- server-side: making sure that network buffers are not discarded between requests
- proxies: Most HTTP proxies do not pipeline outgoing request
- HTTP is based on TCP, and one of TCP's guarantees is ordered delivery. This means that all of the requests sent out on the same socket, will be received in that order on the server. 
- HTTPS pipelining is also possible with secure HTTP connections and it gives an even greater degree of speed because of the extra needed SSL/TLS handshakes.
- Which browsers support HTTP pipelining? (And how to enable it)
    - Google Chrome: No
    - Safari: No
    - Internet Explorer: No
    - Opera: Yes
    - Firefox: Yes, but you need to enable it by following the below steps.

- **HTTP persistent connection**, also called HTTP keep-alive, or HTTP connection reuse, is the idea of using a single TCP connection to send and receive multiple HTTP requests/responses

- **why http pipelining**:
TCP/IP packets can be reduced. several HTTP requests could fit into a single packet. 
What this means is that you can get much faster page loads by using HTTP pipelining.

<span id="jump2"></span>
## Algorithm

#### 1. clarify
1. are there any time or space complexity requirements?  
2. is the range of these values limited in some way. 
    - ex:If the set fit memory, but my input not fit the memory, I can just process it into chunks. I put it in a set, accumulated set. If we can do it parallel, then it’s kind of the same thing. so we have multiple computers each not particular processing each bit of the input. each one producing a set of complement this bit has seen 
    each computer is testing this program in the right order when I merge them, we can say oh, those tow are correctly.
    when I have four in this computer and four in that computer, I could merge them and I would need to be careful that I reconcile them. but other than that, I think that would be the only consideration

3. How about ... (corner case, edge case)?

#### 2. Algorithm
1. think out loud, say your thought
2. data structure
3. hashmap
    - hash function,
    - load factor: 1-0 resizing to 2*capacity when the number of element inserted in array > capacity * load factor 
    - collision:
        - linear probing, move to the next item one by one
        - seperate chaining, linkedlist, worst case O(n)
#### 3. test your solution
(corner case, edge case)


#### 4. Classic problems
np, co-np, np completeness, recursion(gcd,extended gcd, union-find's find)
* Decision Problem
A decision problem is a problem whose answer is YES or NO
* P (Polynomial time)
The class P is the set of all decision problems that can be solved in polynomial time in the size of their encoding (ie. polynomial number of operations)
* NP (Nondeterministic Polynomial time)
The set of all decision problem such that if the answer is YES then there is a certificate of validity that can be checked in polynomial time in the size of their input (**a yes answer for a decision problem can be verified in polynomial time**)
* co-NP
The set of all decision problem such that if the answer is NO then there is a certificate of validity that can be checked in polynomial time in the size of their input (**a no answer for a decision problem can be verified in polynomial time**)
* NP-Completeness(CNF-SAT, cli)
    - A decision problem P is NP-Complete if two conditions are satisfies:(1) It is NP; (2) Every other problem P' in NP is polynomially reducible to P.
    - A problem is NP-Hard iff a polynomial-time solution for it would imply a polynomial-time solution for every problem in NP.
    - A problem is NP-Complete iff it is NP-Hard and it is in NP itself.
* Theorem1: P is a subset of NP. Also, P is a subset of co-NP
* example: (algorithms)[http://www.cse.iitd.ernet.in/~naveen/courses/CSL630/all.pdf]
    - np complete:
        - 3set
        - 3SAT
        - TSP: Given a list of cities and the distances between each pair of cities, what is the shortest possible route that visits each city exactly once and returns to the origin city?
        - RUDRATA cycle： Given a graph, find a path that contains each vertex exactly once. 
        - independent set/clique: G=(V,E), S belongs to V, S is independent set if there are no edges between vertices in S.
        - knapsack: Given a set of items, each with a weight and a value, determine the number of each item to include in a collection so that the total weight is less than or equal to a given limit and the total value is as large as possible
    - np[all np](http://cs.lmu.edu/~ray/notes/npc/)
        - Travelling salesman problem (decision version)
        - Independent set problem
        - Boolean satisfiability problem (SAT)
        - Vertex cover problem
        - Knapsack problem
        - Hamiltonian path problem： a path in an undirected or directed graph that visits each vertex exactly once.
    - np-hard: Sodoku -- Does a given Sodoku puzzle have a solution?
        - Partition： partition problem is the task of deciding whether a given multiset S of positive integers can be partitioned into two subsets S1 and S2 such that the sum of the numbers in S1 equals the sum of the numbers in S2.
    - p
        - 2SAT, HORN SAT
        - MINIMUM SPANNING TREE
        - INDEPENDENT SET on trees
        - EULER PATH： Given a graph, find a path that contains each edge exactly once. 

<span id="jump3"></span>
## Databases/SQL
Data modeling fundamentals, database architecture/efficiency, SQL commands/syntax, complex query design, etc 
- A well-structured database:
    - Maintains data accuracy and integrity.
    - Provides access to the data in useful ways.
    - Saves disk space by eliminating redundant data.
- steps:
    - Understanding the purpose of your database, not only at beginning of design process, but keep this in mind throughout the process.
    - talk to the people who will use it, find out what data they need to use
    - Analyze business forms, such as invoices, timesheets, surveys
    - to check that if we need to Comb through any existing data systems (including physical and digital files)
- sql: Structured Query Language is the basic way of asking a database server to talk to you. 
    - **foreign key** 
        - A FOREIGN KEY is a key used to link two tables together. 
        - A FOREIGN KEY is a field (or collection of fields) in one table that refers to the PRIMARY KEY in another table.
    - **union**: merges the contents of two structurally-compatible tables into a single combined table. omit duplicate records
    - **UNION ALL**: same...include duplicate records. performance of UNION ALL will typically be better than UNION.
    - A **primary key** is usually used as the index for a particular table — a value that the table can depend upon to be a reliable unique value in every row.
    - **join**need to search across multiple tables simultaneously, a join can help make that happen 
        - Equijoins are easy to specify and easy to validate
    - **difference between ‘=’ and ‘LIKE’?** LIKE allows partial matching / use of wildcards, while = checks for exact matches.
    - **COUNT()** get the quantity of results from a query. ex `SELECT COUNT(*) AS NumberOfOrders FROM Orders`
    - **INSERT** submits data into a database as a new row,
    - **DROP** removes a table from a database or a database from a server. 
    - **UPDATE** allows values to be modified where they meet specific criteria
    - example: `select case when null is null then 'Yup' else 'Nope' end as Result;`
    - **Group by** summarizing
    - **Order by** specify the sort criteria.
    - **Join** 
        - (INNER) JOIN: Returns records that have matching values in both tables
        - LEFT (OUTER) JOIN: Return all records from the left table, and the matched records from the right table
        - RIGHT (OUTER) JOIN: Return all records from the right table, and the matched records from the left table
        - FULL (OUTER) JOIN: Return all records when there is a match in either left or right table
    - **neseted query** a nested query can be replaced with a JOIN, allowing for much more efficient use of resources. difficult to troubleshoot and even harder to manage
    - **sql injection** `SELECT UserId, Name, Password FROM Users WHERE UserId = 105 or 1=1;` or `SELECT * FROM Users WHERE Name ="" or ""="" AND Pass ="" or ""=""` when we type "" or ""="" as username and password.
    - **answer to sql injection** input sterilization. One of the main answers to SQL Injection, input sterilization allows the database to selectively ignore data coming in from an input field and strip out non-required data. 
    - **Flat File** A flatfile is a catch-all term used for concepts like Comma Separated Values (.csv). 
- noSQL VS. Relational DB
    - Does not follow any order	vs. organized and structured
    - Very Good	scalability vs. average
    - Limited as no join clause when query vs. SQL
    - K-V pairs, in json vs. data and relationship stored in different tables
- DB schema: 
A database schema is a way to logically group objects such as tables, views, stored procedures etc. Think of a schema as a container of objects.
- What is Replication?
Database replication allows for real-time automated backups between multiple database servers. This allows for the creation of either a fall-over server, or warm backup for use in case the main server goes down.
-  XML?
Extensible Markup Language (XML) is a fast way to display data that not only conforms to a structure that can be read by machines, but is also easily understandable by humans. 
- DB normalization
Once you have a preliminary design for your database, you can apply normalization rules to make sure the tables are structured correctly. Think of these rules as the industry standards.
- index `make index on`
    - Although indexes speed up data retrieval, they can slow down inserting, updating, and deleting, since the index has to be rebuilt whenever a record is changed.
    - postgresql: index-default, index-gin(index inside json)read more, update less: index,
- complex query :
    - break up the query into managable parts, Complex queries can sometimes just be a collection of simple queries.
    - Beware of mixed levels of aggregation: If you have to put monthly, quarterly and year-to-date values in the same result set, you'll need to calculate them separately in queries grouped on different values.
    - when to UNION: Having to include items from different tables in different rows is an obvious use.
    - Enforcing the same style over tables, columns, etc. helps the readability a lot too.
    - Enforcing the same style over queries
    - **Where possible, I generate test data to verify that boundary conditions and other exceptional cases don't cause my query to fail.**
        - Test each of the queries in a union query separately.
        - Test subqueries separately.
        - Test complex expressions separately.
        - Look at raw data before I apply built-in functions to it.

[Conclusion](https://www.simple-talk.com/sql/performance/designing-efficient-sql-a-visual-approach/)
To write an efficient query, you need to know how much data you have to acquire and where it’s going to be. You also need to know what options you have for acquiring the data and how much effort you are going to waste visiting data that you don’t need so that you can decide the best order for visiting tables.

For complex queries the best way to design the query is to start by drawing a diagram of all the tables involved, showing the joins between the tables, indicating the volume of data involved, and describing the indexes that allow you to get from one table to the next. A diagram of this sort will make it much easier to understand the efficiency of the possible paths that your query could take through the tables.



<span id="jump4"></span>
## Linux/Unix
Must be comfortable working in a Linux environment (as a user, not an admin) and will be expected to have a good working knowledge of user­-level Linux commands, shell scripting, regular expressions, etc.
- grep pipeline regard the input 
- auex
- sed: Strean EDitor, eg: replace all occurrences of string1 in current directory with string2
    - sed is the stream editor, in that you can use | (pipe) to send standard streams (STDIN and STDOUT specifically) through sed and alter them programmatically on the fly
    - eg:`sed -i -e 's/few/wt/g' afile.txt` 
        - `s/`: subsitute the found expression 'few' with 'wt' in afile.txt. 
        - `/g` stands for "global", meaning to do this for the whole line. If you leave off the /g (with s/few/asd/, there always needs to be three slashes no matter what), only the first few will be changed to wt. 
        - `-i` option is used to edit in place on the file hello.txt.(in-place: save back to the original file))
        - `-e` option indicates the expression/command to run, in this case s/.
        - Note: It's important that you use -i -e to search/replace. If you do -ie, you create a backup of every file with the letter 'e' appended.
        - Note2: On OS X you can't use `sed -i -e `since the extension of the backup file would be set to -e, so we need to use `sed -i '' -e 's/foo/bar/' target.file`
        ```
        few people
        ==>
        wt people
        ```  
        - Replace any of foo, bar or baz with foobar: `sed -Ei 's/foo|bar|baz/foobar/g' file`
- or, we just using `perl -i -pe 's/vy/xy/g' ./* `, but this one will fail for file names ending in | or space.
- cat: `cat file1 file2` prints the content of file1 followed by file2 to stdout.
- tee 
- top  usage of your machine
- history
- touch 
- tar cvf archive_name.tar dirname/
- `grep -i "the" demo_file` Search for a given string in a file(-r recursively)/`$ grep -A 3 -i "example" demo_text` Print the matched line, along with the 3 lines after it.
- `find -iname "MyCProgram.c"` find file
- `ssh -l jsmith remotehost.example.com` login to remote host
- Remove duplicate lines using awk
- [delete lines that sum to zero](https://unix.stackexchange.com/questions/170588/delete-lines-that-sum-to-zero?noredirect=1&lq=1): `awk '{s=0; for (i=3;i<=NF;i++) s+=$i; if (s!=0)print}' infile > outfile`
- su do /su -username:  Switch to a different user account using su command.
- gzip / gzip -d
- ps 
    - `ps -aux|grep 11338(pid)`:
        - a = show processes for all users
        - u = display the process's user/owner
        - x = also show processes not attached to a terminal
    - sort processes by their port numbers in increasing order (no solutions found). sort processes by current CPU/memory usage can be implemented using `ps aux  | sort -r` or -m
    
- src `scp root@10.134.49.138:/root/yangxiaolu/vr_validation.jar .`scp root@对 地址:/ 件路径+名字 【.(放当前 录) /search(放某  录)】
- mkdir
- vim
- chmod
- ifconfig
- man crontab / manue, Display the man page of a specific command.
- `tail filename.txt` Print the last 10 lines of a file by default.
- wget uri : download uri file
- netstat -nap|grep (searchhub端 号)【显 进程的所有信息】 
- curl localhost：8080 显示页面内容，一般不显示头, `curl --heat url` 显示头, `curl -i url` 显示所有内容
- pwd
- cd
- ls -la
- uname -a
- cat /etc/*rel*
- more /etc/passwd in xy
- id/ pid
- env
- env|more
- df -h / df -h ./ df -h|awk '{print $4}'|sort -nr
- permission, owner, member in my group, others
- chmod 777
- ll -a|grep -i mar/  ll -a|grep "Mar">username
- netstat -ap | grep -i listen|more
- hohup df -h &
- swapon
- free -h
- at ^c
- [I/O Redirection](http://gd.tuwien.ac.at/linuxcommand.org/lts0060.html)
    - Standard Output: Most command line programs that display their results do so by sending their results to a facility called standard output. 
        - `ls > file_list.txt`: the ls command is executed and the results are written in a file named file_list.txt. Since the output of ls was redirected to the file, no results appear on the display.
        - `ls >> file_list.txt`:  If you want the new results to be appended to the file, use ">>" like this(use '>', we will overwrite file_list.txt)
    - Standard Input: Many commands can accept input from a facility called standard input. To redirect standard input from a file instead of the keyboard, the "<" character is used
        - `sort < file_list.txt`: we used the sort command to process the contents of file_list.txt. The results are output on the display since the standard output is not redirected in this example. We could redirect standard output to another file
    - Pipes: connect multiple commands together with what are called pipes. With pipes, the standard output of one command is fed into the standard input of another.      
         
 

<span id="jump5"></span>
## OS
OS(semophores, newtexts, lock, process, thread, resource allocation, context switching, corcurrency)
- process vs. thread:  threads are a part of a process, i.e. a process may contain one or more threads, but a thread cannot contain a process.
- Starvation: one or more threads denied resources
- semophores： Synchronized counting variable a semaphore is a variable or abstract data type that is used for controlling access, by multiple processes, to a common resource in a parallel programming or a multi user environment
    - Two operations: P() and V()/p: while value = 0, sleep; decreame value/v:Increment value; If there are any threads sleeping waiting for value to become non-zero, wakeup at least 1 thread
- lock
- resource allocation
- context switching: In computing, a context switch is the process of storing and restoring the state of a process or thread so that execution can be resumed from the same point at a later time.
 CS saves this return address to the TCB(thread control block)
- synchronization mechanism to avoid race conditions by ensuring exclusive execution of critical sections
- corcurrency
- fork(): After a new child process created, both processes will execute the next instruction following the fork() system call.
- What is deadlock?
    - permanent blocking of threads
    - Deadlock is a situation when two or more processes wait for each other to finish and none of them ever finish.
    - One real Life example would be: "a person says he always lies".
    - If he's a liar, he's telling the truth. Here truth and lie can be considered two processes that don't let each other finish
    - Another example to which you all can relate. "You need experience to get a job and a job to get experience"
- What are the necessary conditions for deadlock?
    - Mutual Exclusion: There is s resource that cannot be shared.
    - Hold and Wait: A process is holding at least one resource and waiting for another resource which is with some other process.
    - No Preemption: The operating system is not allowed to take a resource back from a process until process gives it back.
    - Circular Wait: A set of processes are waiting for each other in circular form.
- How to break the deadlock?
    - The above are necessary but not sufficient conditions, even if all the conditions exist the system may or may not be in a deadlock, but if it's missing then deadlock won't happen.




<span id="jump6"></span>
## Programming/OO
You will be asked to write some code in at least one of the interviews (in your preferred language). Syntax is not as important as structured thinking, but proper syntax never hurts. Object oriented theory and concepts may also be covered
1. Abstraction: 
The process of picking out (abstracting) common features of objects and procedures.

2. Class:
    1. A category of objects. The class defines all the common properties of the different objects that belong to it.
    2. A class, in the context of Java, are templates that are used to create objects, and to define object data types and methods.

3. Encapsulation: //   [ɪn,kæpsə'leʃən]
    1. Encapsulation enable programmers to hide the data of one class from another class. This is needed to protect the normal behavior of one class. We implemented it  using key words including public, private, and protect
    2. Encapsulation in Java is a mechanism of wrapping the data (variables) and code acting on the data (methods) together as a single unit. 
    3. In encapsulation, the variables of a class will be hidden from other classes, and can be accessed only through the methods of their current class

4. Inheritance: // [in'heritəns]
a feature that represents the "is a" relationship between different classes. Inheritance in OOP enable a programmer to extend the capabilities of class without changing the class. 

5. Interface: the languages and codes that the applications use to communicate with each other and with the hardware.

5. Object: a self-contained entity that consists of both data and procedures to manipulate the data.

6. Polymorphism: // [,pɔli'mɔ:fizm] 
    1. Subclasses of a class can define their own unique behaviors and yet share some of the same functionality of the parent class. 
    2. Polymorphism enables programmers to use a different object in place of another provided that object can do the task (implements the same interface).


<span id="jump7"></span>
## VCS - Git
1. all VCS can be categorized into two types: **central** or **distributed**.
    - Git is the application that keeps track of everything related to the changes on your project over time
    - GitHub is a host for Git repositories with collaboration features that let you apply and test changes to your code. (Code, Issues, Pull Requests, and Projects.)
    - **Git vs. Github** Git Is a Version Control Application, GitHub Is a Collaboration Platform. Together, Git and GitHub form the heart of the modern developer’s toolkit.
2. a few key terms
    - Repositories: A collection of source files used to compile your project. It’s easiest to imagine it as a project folder. 
    - Commits: A snapshot of your project as it existed at a specific point in time. You create commits as you work on your project to indicate points when you added and removed discrete units of work.
    - Branch: A series of commits that represent the changes in your project over time. Every repository has a default branch, which contains the production-ready version of your code. Create additional branches when you’re working on new features, fixing bugs, or making other changes to your project. These branches keep your experimental code separate from your tested production code.
    - Merge: The combined history of two or more branches. Most of the time, you’ll merge your feature branch into the default or deployed branch of the repository in order to move the features into production.
    - Tag: A pointer to a specific commit, which provides a persistent reference to an event. Typically, tags are used with semantic versioning to represent points when your application was released.
3. git command
    - The local and remote repositories only interact when you run one of the four network commands in Git: `git clone`, `git fetch`, `git pull`, and `git push`.
    - Git uses the config settings for your user name and email address to generate a unique fingerprint for each of the commits you create. 
    ```
    $ git config --global user.name "First Last"  
    $ git config --global user.email "you@email.com"    
    ```    
    - `git branch branchname` + `git checkout branchname` or `git checkout -b branchname` With Git, checkout moves an important pointer called HEAD, and in this case, moves us to a different branch. HEAD points to the tip of your branch.
    - `git log --oneline --graph --decorate` displays the same ASCII graph that is displayed using the --graph modifier, but also includes the branch name(s) for the different commits being displayed.
    - By default, the `git diff` command helps you review the changes between the last commit of your project and the various states of your files
    - use `git revert` if the commit has been pushed to the remote, you want to change or **undo a previous change**.
    - use `git commit --amend` to make a modification to the last commit you made. don't use git commit --amend if you have already pushed your commits to the remote.
    - `git reset` rewind the history of our project, but, it alters the commit history, only use reset when you have not pushed your commits to your remote
        - `git reset --soft` takes the identified commit(s) and places all of the changes in the staging area. This is helpful if you want to take a group of commits and squash them into a single larger commit.
4. two stage commit



#### Request and response headers
1. request message -- sent via Uniform Resource Locators (URLs)
2. ![url](https://cdn.tutsplus.com/net/authors/jeremymcpeak/http1-url-structure.png)
    - port can be set explicitly, 
    - resource path is the local path to the resource on server
3. web debugging proxies:  Fiddler on Windows and Charles Proxy for OSX.
4. request verb:
    - GET: fetch an existing resource. 
        - The URL contains all the necessary information the server needs to locate and return the resource.
    - POST: 
        - create a new resource. POST requests usually carry a payload that specifies the data for the new resource.
    - PUT: 
        - update an existing resource. The payload may contain the updated data for the resource.
    - DELETE: delete an existing resource.
PUT and DELETE are sometimes considered specialized versions of the POST verb, and they may be packaged as POST requests with the payload containing the exact action: create, update or delete.
5. lesser used verbs that HTTP support:
    - HEAD: 
        - similar to GET, but without the message body. 
        - It's used to retrieve the server headers for a particular resource, generally to check if the resource has changed, via timestamps.
    - TRACE: 
        - used to retrieve the hops that a request takes to round trip from the server. Each intermediate proxy or gateway would inject its IP or DNS name into the Via header field. This can be used for diagnostic purposes.
    - OPTIONS: used to retrieve the server capabilities. On the client-side, it can be used to modify the request based on what the server can support.









