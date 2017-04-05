---
layout: post #post
title: Core Jave Interview Questions & Answers #post title
categories: Java Interview #post category, seperated by spcace
tags: Java Interview OOP #post tag, seperated by spcace
---

## Core Jave Interview Questions & Answers
## 1. basis:
#### 1.1 concepts terminologies
1. 语句— statement
2. Instance variable
3. Instance method(without static)
4. func( parameter variables ){…}


#### 1.2 common methods

###### 1.2.1. string
4. s.substring(0, 1);
23. s.substring(1);
24. s.equals("b");
25. s = s.trim();
26. s.indexOf("a");
27. s.indexOf("a", 1); 
//indexOf(int ch, int fromIndex)
Returns the index within this string of the first occurrence of the specified character, starting the search at the specified index.
28. s.lastIndexOf("a");
//Returns the index within this string of the last occurrence of the specified character, searching backward starting at the specified index.
1. Integer.valueOf(s); // returns an Integer object
32. Integer.parseInt(s); // returns an int primitive
33. String.valueOf(s); // integer to string
1. 
  ```
StringBuilder sb = new StringBuilder();
sb.append("a");
sb.insert(0, "a"); //(idx, str)
sb.deleteCharAt(sb.length() ‐ 1);
sb.reverse();
sb.toString();
  ```

###### 1.2.2. array arraylist
2. int max = Integer.MAX_VALUE;
3. int min = Integer.MIN_VALUE;
4. Arrays.sort()
16. List<Integer> list = new ArrayList<Integer>();
17. list.add(0);
58. list.add(0, 1);
19. list.get(0);
60. list.size();
61. list.remove(list.size() ‐ 1);
62. Collections.sort(list);
63. Collections.sort(list, Collections.reverseOrder());
64. 
  ```
Collections.sort(list, new Comparator<Integer>() {
           @Override
            public int compare(Integer o1, Integer o2) {
                   return o1 ‐ o2;// 0‐>1
                   // return o2‐o1; 1‐>0
             }
 });
//java8 lambda 
Arrays.sort(points,(a,b)->(a[1]-b[1])); // int[][] points
PriorityQueue<Map.Entry<Integer, Integer>> maxHeap =  new PriorityQueue<>((a,b)->(b.getValue()-a.getValue()));  
// pq: pq.add(0); pq.remove(); pq.peek(); pq.isEmpty(); pq.size();
```

###### 1.2.3. stack
72. Stack<Integer> stack = new Stack<Integer>();
73. stack.push(0);
74. stack.pop();
75. stack.peek(); // The method call returns the object at the top of this stack. Thrown EmptyStackException if this stack is empty.
76. stack.isEmpty();
77. stack.size();
**more**：pop 和 peak 区别：peek()： This method looks at the object at the top of this stack without removing it from the stack.

##### 1.2.4. queue
1. Queue<Integer> q = new LinkedList<Integer>();
80. q.add(0);
81. q.remove();
82. q.peek();
5. q.isEmpty();
6. q.size();

##### 1.2.5 hashmap/ hashset
1. if (map.containsKey('c')) {...}
2. if (map.containsValue(1)) {...}
3. for (Character d : map.keySet()){...}
4. for (Integer i : map.values()) {...}
97. map.isEmpty();
98. map.size();
7. set.add(0);
8. set.remove(0);
9. set.contains(0);
10. set.isEmpty();


## 2. interview questions
###### [2.1 interface vs abstract class](#jump1)
###### [2.2 Pass by reference vs. pass by value](#jump2)
###### [2.3 Final / finalize /finally](#jump3)
###### [2.4  OOP](#jump4)
###### [2.5 OOP concepts](#jump5)
###### [2.6 overloading/overriding](#jump6)
###### [2.7 hashmap vs. hash table  vs. hashset](#jump7) 
###### [2.8  Array vs. ArrayList vs. LinkedList](#jump8)
###### [2.9 stringbuilder vs string buffer](#jump9)
###### [2.10 error vs. exception](#jump10)
###### [2.11 between method and constructor](#jump11)
###### [2.12  void main](#jump12)
###### [2.13  Primitive types](#jump13)
###### [2.14 when try catch?  How will you handle the exception without using try-catch block?](#jump14)
###### [2.15 access modifier](#jump15)
###### [2.16 static](#jump16)
###### [2.17  J2EE, J2SE, JSP](#jump17)
###### [2.18  why do we need package the program](#jump18)
###### [2.19 MVC](#jump19)
###### [2.20 what is JDK,JRE,JVM](#jump20)
###### [2.21 GC](#jump21)
###### [2.22 Java里shared memory在哪儿](#jump22)

非重点：
###### 2.   HashSet vs. TreeSet vs. LinkedHashSet
###### 2.   HashMap vs. TreeMap vs. HashTable vs. 


## 3. anwers
<span id="jump1"></span>
###### 3.1 interface vs abstract class
we use them for different purposes
 1. We use abstract class when we want to share code among several closely classes.
 2. We use interface when we expect that unrelated classes would implement the interface.
 3. For example, the interface Comparable and Cloneable are implemented by unrelated class.

differences
1. abstrat class--extend, interface--implement
4. interface is a a collection of abstract methods, which only contains method signatures and fields, not implementations. Abstract class can contain a mix of methods declared with or without implementation.
2. with interface, all fields are automatic public, static, final, and all methods you declare or defined are public. But with abstract class, you can declare fields that are not static and final, and define public, protected, and private concrete method.
3. we can extend only one class, whether or not it is abstract, whereas you can implement any number if interfaces.

<span id="jump2"></span>
###### 3.2 Pass by reference vs. pass by value
1. java is pass-by-value 
2. Pass by value (primitives): make a copy in memory of the actual parameter's value that is passed in.
3. Pass by reference (objects): pass a copy of the address of the actual parameter.

<span id="jump3"></span>
###### 3.3 Final / finalize /finally
1. Final
  1. final is a key word, used to apply restrictions on class, method and variable. 
  2. final class can not be inherited, 
  3. final method can not be overridden// [,əuvə'ridn]
  4. final variable value can not be changed
  5. used to declare constants
2. Finally
  1. Finally is a block, used in try catch statement to place important code.
  2. it will be executed whether exception is handled or not
  3. it means that no matter what happened, the code in finally block will be executed
3. Finalize
  1. Finalize is a method, used to perform clean up processing just before object is garbage collected.

<span id="jump4"></span>
###### 3.4  OOP
1. Object Oriented Programming: programming language model organized around  objects rather than "actions" and data rather than logic
3. Your program consists of a number of "objects", which are combinations of data  and operations that you can do with that data. We can sent "Messages" to objects, and the messages make them perform operations. that is call a method.  The program consist of collections of objects that send messages to each other.

<span id="jump5"></span>
###### 3.5 OOP concepts
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

7. How will you access the properties of that class?
!!!!!!!!!!!!!

<span id="jump6"></span>
###### 3.6 overloading/overriding
1. Overloading :  define two method, same name but they have different parameters 
2. Overriding:  When you redefine a method which has already define in parent class(using exact same paremeters)

<span id="jump7"></span>
###### 3.7 hashmap vs. hash table  vs. hashset 
1. HashMap 
  1. is implemented as a hash table, and there is no ordering on keys or values.
  2. what happens when a duplicate key is putting into a hashmap? Overwrite that key if hashmap has the same key. the old value is simply replaced.
2. HashSet 
is Implemented using a hash table. Elements are not ordered. The add, remove, and contains methods have constant time complexity O(1).
  1. set： Set interface: A Set contains no duplicate elements. That is one of the major reasons to use a set.
When and which to use is an important question. In brief, if you need a fast set, you should use HashSet;
2. Hashtable vs hashmap
  1. hashtable is synchronized, whereas  HashMap  is not （in contrast to HashMap）. It has an overhead for synchronization. All methods of Hashtable are synchronized which makes them quite slow due to contention if a number of thread increases. This makes  HashMap  better for non-threaded applications, as unsynchronized Objects typically perform better than synchronized ones.
    - Synchronized:  keyword prevents concurrent access to a block of code or object by multiple Threads
  2. Hashtable  does not allow  null  keys or values.  HashMap  allows one  null  key and any number of  null  values.

<span id="jump8"></span>
###### 3.8  Array vs. ArrayList vs. LinkedList
1. Array
  1. Array is a container object that holds a fixed number of values of a single type.
  1. Array has fix size, and the size is set when we initialize an array.
  2. Array can contain primitive types, can be multi-dimensional, **while ArrayList is resizable, cannot contain primitive types, only one-dimensional.**
2. ArrayList and LinkedList both implements List interface, maintain the insertion order, non-synchronized (can use Collections.synchronizedList to synchronize). 
  1. Arraylist is implemented by array. 
  2. Linked list is implemented by doubly linked list.
3. Operations:
  1. Search: ArrayList search operation is pretty fast compared to the LinkedList search operation. get(int index) in ArrayList gives the performance of O(1) while LinkedList performance is O(n).
     - Reason: ArrayList maintains index based system for its elements as it uses array data structure implicitly which makes it faster for searching an element in the list. On the other side LinkedList implements doubly linked list which requires the traversal through all the elements for searching an element.
  2. Deletion: LinkedList remove operation gives O(1) performance while ArrayList gives variable performance: O(n) in worst case (while removing first element) and O(1) in best case (While removing last element).
    - Reason: LinkedList’s each element maintains two pointers (addresses) which points to the both neighbor elements in the list. Hence removal only requires change in the pointer location in the two neighbor nodes (elements) of the node which is going to be removed. While In ArrayList all the elements need to be shifted to fill out the space created by removed element.
  3. Inserts Performance: LinkedList add method gives O(1) performance while ArrayList gives O(n) in worst case.  Reason is same as explained for remove.
  4. Memory Overhead: ArrayList maintains indexes and element data while LinkedList maintains element data and two pointers for neighbor nodes hence the memory consumption is high in LinkedList comparatively.

<span id="jump9"></span>
###### 3.9 stringbuilder vs string buffer
1. String class is used to manipulate character strings that cannot be changed. Objects of type String are read only and immutable.
2. The StringBuffer class is used to represent characters that can be modified.
3. StringBuilder is faster than StringBuffer because it's not synchronized. StringBuffer thread safe

<span id="jump10"></span>
###### 3.10 error vs. exception
1. An Error "indicates serious problems that a reasonable application should not try to catch."
2. An Exception "indicates conditions that a reasonable application might want to catch."
3. Error along with RuntimeException & their subclasses are unchecked exceptions. All other Exception classes are checked exceptions.
4. In Java exceptions under Error and RuntimeException classes are unchecked exceptions, everything else under throwable is checked.

<span id="jump11"></span>
###### 3.11 method vs. constructor.
1. Constructors can't be called directly; they are called implicitly when the new keyword creates an object. Methods can be called directly on an object that has already been created with new.
2. Constructors must be named with the same name as the class name. They can't return anything, even void (the object itself is the implicit return).
Methods must be declared to return something, although it can be void.

<span id="jump12"></span>
###### 3.12  void main
1. Void is the return type of this method, indicating that this method doesn't return anything.
2. Main is the name of a function. main() is special because it is the start of the program.

<span id="jump13"></span>
###### 3.13  Primitive types
1. Byte: 8-bit signed two's complement integer, [-128, 127]. The byte data type can be useful for saving memory in large arrays, where the memory savings actually matters.
2. Short: 16-bit signed two's complement integer. Save memory in large arrays of floating point numbers.
3. Int: 32-bit signed two's complement integer, [-231, 231-1]. In Java SE 8 and later, you can use the int data type to represent an unsigned 32-bit integer, which has a minimum value of 0 and a maximum value of 232-1. Static methods like compareUnsigned, divideUnsigned etc have been added to the Integer class to support the arithmetic operations for unsigned integers.
4. Long: 64-bit two's complement integer, [-263, 263-1]. In Java SE 8 and later, you can use the long data type to represent an unsigned 64-bit long, which has a minimum value of 0 and a maximum value of 264-1.
5. Float: single-precision 32-bit IEEE 754 floating point. Save memory in large arrays of floating point numbers. This data type should never be used for precise values, such as currency. For that, you will need to use the java.math.BigDecimal class instead. Numbers and Strings covers BigDecimal and other useful classes provided by the Java platform.
6. Double: double-precision 64-bit IEEE 754 floating point. For decimal values, this data type is generally the default choice. As mentioned above, this data type should never be used for precise values, such as currency. 7. Boolean: true / false. Use this data type for simple flags that track true/false conditions. This data type represents one bit of information, but its "size" isn't something that's precisely defined.
8. Char: single 16-bit Unicode character. It has a minimum value of '\u0000' (or 0) and a maximum value of '\uffff' (or 65,535 inclusive).

<span id="jump14"></span>
###### 3.14 when try catch?  How will you handle the exception without using try-catch block?
1. When you want to do any "work" after exception is thrown you will definitely go for using "Try/Catch" block.
2. By default, the JVM handles uncaught exceptions by printing the stack-trace to System.err stream. Java allows us to customize this behavior by providing our own routine which implements Thread.UncaughtExceptionHandler interface.

<span id="jump15"></span>
###### 3.15 access modifier
![屏幕快照 2017-03-30 04.50.46.png](http://upload-images.jianshu.io/upload_images/260723-91977fd194836ca2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

<span id="jump16"></span>
###### 3.16 static
1. Static indicates that this method can be called without creating an instance of this class
1. In Java, a  static  member is a member of a class that isn’t associated with an instance of a class. Instead, the member belongs to the class itself. As a result, you can access the static member without first creating a class instance.
2. static members belong to the class instead of a specific instance.
3. It means that only one instance of a static field exists

<span id="jump17"></span>
###### 3.17  J2EE, J2SE, JSP
1. JavaSE (Standard Edition): For general-purpose use on desktop PCs,servers and similar devices.

2. JavaEE (Enterprise Edition): Java SE plus various APIs useful formulti-tier client–serverenterprise applications. Theplatform was known as Java2 Platform, Enterprise Editionor J2EEuntil the name was changed to JavaEEin version 5. The current version is called JavaEE 6.

3. Java ServerPages (JSP) are server-side Java EEcomponents that generate responses, typically HTMLpages, to HTTP requests from clients. JSPsembed Java code in an HTML page by using the special delimiters<% and %>. A JSP is compiled to a Java servlet,a Java application in its own right, the first time it is accessed.After that, the generated servlet creates the response.

<span id="jump18"></span>
###### 3.18  why do we need package the program.
A package is a namespace that organizes a set of related classes and interfaces

<span id="jump19"></span>
###### 3.19 MVC
MVC:  is a software architecture - the structure of the system
MVC:  (Model, View, Controller) is a pattern for organising code in an application to improve maintainability.

<span id="jump20"></span>
###### 3.20 what is JDK,JRE,JVM
1. JVM:  
  1. The Java Virtual Machine (JVM) is an abstract computing machine. The JVM is a program that looks like a machine to the programs written to execute in it. 
  2. (Java Virtual Machine) is an abstract machine. It is a specification that provides runtime environment in which java bytecode can be executed
2. JRE:  is an acronym for Java Runtime Environment.It is used to provide runtime environment.It is the implementation of JVM. It physically exists.
3. JDK:  is an acronym for Java Development Kit.It physically exists.It contains JRE + development tools.

<span id="jump21"></span>
###### 3.21 GC
Generational garbage collector
1. because: most objects have short lifetimes, a few live very long
2. 2 or more generations
3. old generation: The objects that did not become unreachable and survived from the young generation are copied here. + young generation: Most of the newly created objects are located here.
4. Composition of the Young Generation 
  1. One Eden space
  2. Two Survivor spaces

<span id="jump22"></span>
###### 3.22 Java里shared memory在哪儿
static  heap stack, static和heap都可以，depends on your program

不太重要：
###### 3.   HashSet vs. TreeSet vs. LinkedHashSet
Set interface: A Set contains no duplicate elements. That is one of the major reasons to use a set.
When and which to use is an important question. In brief, if you need a fast set, you should use HashSet; if you need a sorted set, then TreeSet should be used; if you need a set that can be store the insertion order, LinkedHashSet should be used.
HashSet is Implemented using a hash table. Elements are not ordered. The add, remove, and contains methods have constant time complexity O(1).
TreeSet is implemented using a tree structure(red-black tree in algorithm book). The elements in a set are sorted, but the add, remove, and contains methods has time complexity of O(log (n)). It offers several methods to deal with the ordered set like first(), last(), headSet(), tailSet(), etc.
LinkedHashSet is between HashSet and TreeSet. It is implemented as a hash table with a linked list running through it, so it provides the order of insertion. The time complexity of basic methods is O(1).

###### 3.  HashMap vs. TreeMap vs. HashTable vs. LinkedHashMap vs. ConcurrentHashMap
HashMap is implemented as a hash table, and there is no ordering on keys or values. TreeMap is implemented based on red-black tree structure, and it is ordered by the key. LinkedHashMap preserves the insertion order
Hashtable is synchronized, in contrast to HashMap. It has an overhead for synchronization. All methods of Hashtable are synchronized which makes them quite slow due to contention if a number of thread increases. ConcurrentHashMap is thread safe without synchronizing the whole map. Reads can happen very fast while write is done with a lock. There is no locking at the object level. Unlike Hashtable and Synchronized Map, it never locks whole Map, instead, it divides the map into segments and locking is done on those. Though it performs better if a number of reader threads are greater than the number of writer threads.






## 4.其他 
######4.1 For real-time video conference application, how do you choose between TCP and UDP?
TCP for stored video and UDP for live video
本题的关键在于比较TCP和UDP的特点，并且根据real-time video conference这个特定的应用场景进行选择。前面提到过，TCP的重传机制会增加延迟，所以不适用于当前场景。其次，视频音频编码本身可以容忍数据出错甚至数据丢失。因此，并不需要采用TCP进行可靠的数据传输。当某一视频帧出现丢包时，可以直接跳过这一帧或者继续播放上一帧。再次，一旦出现网络堵塞的状况，发送端应该主动丢弃一部分数据。原因是，即使这些视频帧发送到了接收端，也可能已经“过期”了，不会被解码显示。采用自己设计的UDP更便于实现对数据包的控制。然而，即使使用UDP，也需要实现TCP的某些模块：比如需要flow control和congestion control来判断接收端的播放情况和网络情况，并且也需要反馈机制判断接收端的接收状况。尽管对于当前场景我们不需要ACK每个数据包，但是接收端可以反馈当前收到的最新完整视频帧的序号。这样，如果一旦发生丢包，发送端可以以接收端收到的最新视频帧为基础，压缩后继的视频。

  Video streaming meets with TCP in their nature. First, video streaming adopts pre-fetching and buffering to achieve smooth play-out. TCP provides such (network) buffer, as well as the reliable transmission guarantee for no loss of frame (a frame could still miss the play-out deadline and discarded, however). Second, TCP's bandwidth probing and congestion control will attempt to use all of the available bandwidth between server and client, fetching content as quick as possible while being friendly to other (TCP) traffic on the same links.
However, live streaming opts in UDP, because little pre-fetching can be done and buffering will add delay to the video play-out. Since UDP serves only the most basic transport layer functionality, it is used jointly with other application layer protocols such as RTSP  to do video streaming. Firewalls (from enterprise, ISPs) dislike these protocols, making video traffic difficult to traverse through or being throttled.
In order to deliver videos, platforms adopt/rent Content Delievery Networks (CDN). Most of the CDN servers (e.g. Akamai's) are configured to support web services as their primary course. Thus, streaming video over HTTP works out the box without setting up dedicated servers, and most of the firewalls won't block HTTP traffic. In fact, Dynamic Adaptive Streaming over HTTP (DASH) has become a common practice. Although in theory HTTP can be encapsulated other protocols, they still need to provide reliable transfer, which again precludes UDP. Notably, for companies such as Google and Netflix, they build their own CDN.

  Drawbacks of using TCP for live video:
  1. Typically live video-streaming appliances are not designed with TCP streaming in mind. If you use TCP, the OS must buffer the unacknowledged segments for every client. This is undesirable, particularly in the case of live events; presumably your list of simultaneous clients is long due to the singularity of the event. Pre-recorded video-casts typically don't have as much of a problem with this because viewers stagger their replay activity; therefore TCP is more appropriate for replaying a video-on-demand.
  2. IP multicast significantly reduces video bandwidth requirements for large audiences; TCP prevents the use of IP multicast, but UDP is well-suited for IP multicast.
  3. Live video is normally a constant-bandwidth stream recorded off a camera; pre-recorded video streams come off a disk. The loss-backoff dynamics of TCP make it harder to serve live video when the source streams are at a constant bandwidth (as would happen for a live-event). If you buffer to disk off a camera, be sure you have enough buffer for unpredictable network events and variable TCP send/backoff rates. Note that if TCP loses too many packets, the connection dies; thus, UDP gives you much more control for this application since UDP doesn't care about networkt transport layer drops.
FYI, please don't use the word "packages" when describing networks. Networks send "packets".

######4.2 What happens after you typed a URL in your browser and pressed return key?
如果要连到远程服务器，首先需要知道服务器的IP地址和端口。其次需要发送接入请求到服务器，服务器返回响应数据。因此，如何寻址和如何建立链接是本题的关键。本题属于知识性问题，没有太多的解题技巧，直接给出解答如下
  1. 进行寻址：如果在浏览器缓存中存有URL的对应IP，则直接查询其IP；否则，访问DNS(Domain Name System)进行寻址(Domain Name Resolution)。
  2. DNS或者URL cache返回网页服务器的IP地址。
  3. 浏览器与网页服务器通过三次握手建立TCP连接。由于是网页浏览服务，故浏览器连接到服务器的80端口。
  4. 浏览器与服务器建立HTTP会话(session)，接收来自服务器的HTTP数据。
  5. 浏览器解析HTTP数据，在本地窗口内渲染并显示网页。
  6. 当浏览器页面被关闭时，终止HTTP会话并关闭链接。
7. 

  In an extremely rough and simplified sketch, assuming the simplest possible HTTP request, no proxies, IPv4 and no problems in any step:
1. browser checks cache; if requested object is in cache and is fresh, skip to #9
2. browser asks OS for server's IP address
3. OS makes a DNS lookup and replies the IP address to the browser
4. browser opens a TCP connection to server (this step is much more complex with HTTPS)
5. browser sends the HTTP request through TCP connection
6. browser receives HTTP response and may close the TCP connection, or reuse it for another request
7. browser checks if the response is a redirect or a conditional response (3xx result status codes), authorization request (401), error (4xx and 5xx), etc.; these are handled differently from normal responses (2xx)
8. if cacheable, response is stored in cache
9. browser decodes response (e.g. if it's gzipped)
10. browser determines what to do with response (e.g. is it a HTML page, is it an image, is it a sound clip?)
11. browser renders response, or offers a download dialog for unrecognized types
Again, discussion of each of these points have filled countless pages; take this only as a short summary. Also, there are many other things happening in parallel to this (processing typed-in address, speculative prefetching, adding page to browser history, displaying progress to user, notifying plugins and extensions, rendering the page while it's downloading, pipelining, connection tracking for keep-alive, checking for malicious content etc.) - and the whole operation gets an order of magnitude more complex with HTTPS (certificates and ciphers and pinning, oh my!).


You type in the URL and hit go. The browser needs to translate that URL www.somesite.com into an IP address so it knows what computer on the internet to connect to (That URL is just there to make it easier for us humans - kinda like speed-dial for phone numbers I guess). So your browser will see if it already has the appropriate IP address cached away from previous visits to the site. If not, it will make a DNS query to your DNS server (might be your router or your ISP's DNS server) - see http://en.wikipedia.org/wiki/Domain_name... for more on DNS. Once your browser knows what IP to use, it will connect to the appropriate webserver and ask for the page. The webserver then returns the requested page and your browser renders it to the screen.


以上答案大部分来自google，wiki， stackoverflow。