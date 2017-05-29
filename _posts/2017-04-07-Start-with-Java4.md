---
layout: post #post
title: Start from Java 4 -- Collections, Hibernate #post title
categories: Java #post category, seperated by space
tags: Java #post tag, seperated by space
---


## Collections
1. from util package, an interface
2. Array vs. ArrayList: The issue with arrays is that they are of fixed length so if it is full we cannot add any more elements to it, likewise if there are number of elements gets removed from it the memory consumption would be the same as it doesn’t shrink. On the other ArrayList can dynamically grow and shrink as per the need
2. including:
    - List
    - Set: doesn't in order, no duplicates
    - Map
    - Queue: FIFO
3. CRUD: create, retrieve, update, delete
4. Collection(class):
    - sort();
    - max();
    - min();
5. Iterator: thread safe vs. Enumeration: thread not sage
    6. Iterator: hasNext(); Next();
    ```
    Iterator iter = arrlist.iterator();
    while (iter.hasNext()) {
            System.out.println(iter.next());
    }
    //LinkedList iterator:
    ListIterator listIt = linkedl.listIterator();
    //Iterating the list in forward direction use the same function as above
    // Iterating the list in backward direction
    while(listIt.hasPrevious()){
	       System.out.println(listIt.previous());
	} 
    // loops
    for(ClassName cn : list){...}
    list.forEach(System.out::println);
    ```
    7. Enumeration: hasMoreElements(); nextElement()
    ```
    Enumeration<String> e = Collections.enumeration(arrayList);
	while(e.hasMoreElements())
		System.out.println(e.nextElement());
    ```
6. Initialize ArrayList:
    1. Anonymous Inner class method: `ArrayList<String> cities = new ArrayList<String>(){{add("Delhi");...}};`
    2. Collections.ncopis(): `ArrayList<Integer> intlist = new ArrayList<Integer>(Collections.nCopies(10, 5));`, we get [5, 5, 5, 5, 5, 5, 5, 5, 5, 5]
7. Loop HashMap: `for (Map.Entry me : hmap.entrySet()) {`If we want to use HashSet<self-defined object>, we need to override both hashcode() and equal(). These two method are both from java....object class.
16. hashmap:
    1. sort by key :`Map<Integer, String> map = new TreeMap<Integer, String>(hmap); ` whatever the key is, when you put them to treemap (shift all entries to treemap), your key is automatically sorted.
    2. sort by value : actually is collection, the same as collection, Integer & String can invoke Collections.sort directly; obj -- compareTo
17. duplicate:
    1. add duplicates to set, get false
    2. hashmap: value equal, fine; key-value all equal, only one entry exists
9. Sort in descending order`Collections.sort(arraylist, Collections.reverseOrder());` 
10. If the elements in Collection's subclass(Set, List...) are objects, we should override compareTo in class first, then sort.
```
class someClass{
        public int compareTo(Object compareobj) {
                /* For Ascending order*/
                return this.prop - compareobj.prop;
                /* 
                    For Descending order
                    return compareobj.prop - this.prop;
                */
        }
}
public static void main(String args[]){
        ArrayList<someClass> arraylist = new ArrayList<someClass>();
        ...//add some someClass obj
        Collections.sort(arraylist);
}
```
11. `s1 = 'a'; s2 = 'h'; s1.compareTo(s2) <=0`
12. multiple properties: 
```
Collections.sort(arraylist, className.compareOneOfProp);
class className{
    ...
        public static Comparator<className> compareOneOfProp = (o1,o2) -> {return o1.OneOfProp - o2.OneOfProp;
        public static Comparator<className> compareOfAnotherProp = (o1,o2) -> {return o1.AnotherProp - o2.AnotherProp;
```
13. swap`Collections.swap(al, 1, 4);`
14. Array to ArrayList conversion: `Collections.addAll(emptyArrayList, theArray);` or `ArrayList<String> citylist= new ArrayList<String>(Arrays.asList(citynames));`
15. vector. Contructor:
    1. new Vector(); //capacity:10-20-30
    2. new Vector(int i); //capacity: 10-20-40...(double)
    2. new Vector(int i, int i); //capacity: 10-20-40...(double)

18. Date & Calendar
```
Calender cal = Calendar.getInstance();
cal.set(2017,0,1);
//month start from 0
```
9. StringTokenizer: like split
10. Random: class, function called next.int()
<!--11. author reference to book
12. database driver
13. -->


## Enum
1. An enum is a special type of data type which is basically a collection (set) of constants. 
2. While defining Enums, the constants should be declared first, prior to any fields or methods. 
2. When there are fields and methods declared inside Enum, the list of enum constants must end with a semicolon(;).




## JDBC
1. Connection
2. Statement: have some a drawback: `st.executeUpdate("insert into authors (name, age, zipcode) values(" + newName + "', " + newAge + ", '" + newZip + "')");` this can be too complex.
3. How to improve: **PreparedStatement:**
    1. PreparedStatement ps = con.prepareStatement("...values(?,?,?)");use Statement, it will be very difficult. so we use preparedStatement, who extends Statement interface
    2. ps.setString(1, aString);...
    3. int x = ps.executeUpdate();//insert an entry, x=1??
4. what VM argument? min max memory,for heap,start execute, all objects on heap
5. oracle: procedure...store block, we can reuse, a lot long business logic, demand of supply,
6. 3 procedure: just execute, have argument, can return
1. operations in terminal(windows)
    1. connect system/password-->connected
    2. create or replace procedure helloproc(x IN number, y IN number, z IN number) as begin (actually have no idea what this procedure is)
        ```
        z:=x+y;
        end;
        /
        exec helloproc(10,20);

        //receive return value
        set SERVEROUTPUT ON
        declare x1 number;
        begin
        helloproc(100,200,x1);
        dbms_output.put_line(x1);
        end;
        /
        backslash, recall/re-execute previous ...
        ```
3. maven can only .. open source, so oracle can not use maven. nmp install, get oracle, register local server custom everything
4. pom.xml add dependency: oracle
6. JDBC drawback: queries, because queries is only for one database. If I change a database, I need to change ...
7. implement cashing, JDBC api, not able to do that 
8. class level -- mapping to a table


## Hibernate ( still have one note to read)
1.  Java persistent API include:
    1. JPA
    2. JTA
    3. Hibernate
    4. iBATis
    5. MyBATis
1. model class + test class 
2. 2 executable file: hibernate.cfg.xml and <orm-class-name>.hbm.xml
    1. create hibernate.cfg.xml, copy from document, 
        1. change mapping resource to someclassname.hbm.xml(depends on our project) 
        2. and change password
        3. set url
        4. example:(more details about url are in Q&A part)
            ```
            <?xml version="1.0" encoding="utf-8"?>
            <!DOCTYPE hibernate-configuration PUBLIC
            "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
            "http://hibernate.sourceforge.net/hibernate-configuration-3.0.dtd">
            <hibernate-configuration>
                <session-factory>
                    <property name="hibernate.bytecode.use_reflection_optimizer">false</property>
                    <property name="hibernate.hbm2ddl.auto">update</property>
                    <property name="hibernate.connection.driver_class">com.mysql.jdbc.Driver</property>
                    <property name="hibernate.connection.password">yourpwd</property>
                    <property name="hibernate.connection.url">jdbc:mysql://localhost:3306/tables?autoReconnect=true&amp;useSSL=false</property>
                    <property name="hibernate.connection.username">root</property>
                    <property name="hibernate.dialect">org.hibernate.dialect.MySQLDialect</property>
                    <property name="show_sql">true</property>
                    //important mapping for author
                    <mapping resource="Author.hbm.xml"></mapping>
                </session-factory>
            </hibernate-configuration>
            ```
    2. then create someclassname.hbm.xml: change field according to your program: the xml files: class author belong to author123 table
        ```
        <hibernate-mapping>
        //the class--yourclassname belongs to table--yourTableName with primary key:id
            <class name="com.demo.model.yourclassname" table="yourTableName">
                <id name="id">
                    <generator class="increment" />
                </id>
                <property name="name" length="60" />
                <property name="age" />
                <property name="zipcode" />    
            </class>
        </hibernate-mapping>
        ```
6. convert to maven(if it is not)
7. add dependencies of hibernate and mysql to pom.xml
8. in the test class, configuration, import form ...hibernate...
9. must t.commit(); or it only saved in JVM.
10. steps in terminal in sql:
    1. use tables
    2. (optional)source /Users/yourpath/yourTableName.sql;
    3. select * from yourTableName;
    4. others: desc table books
11. Q & A
    4. ssl :
        1. jdbc: jdbc:mysql://localhost:3306/tables?autoReconnect=true&useSSL=false;
        2. hibernate: jdbc:mysql://localhost:3306/tables?autoReconnect=true&amp;useSSL=false(;)
12. Another way to connect database, we do not need any xml configuration file (like someclassname.hbm.xml )for book class, but need annotation: @Entity, @Table(name = "book123")( class books belongs to table book123, like the xml configuration above)... before class declaration, and in class, we need id(primary key ) and generator setting to AUTO, all from javax.persistance not from hibernate.
13. steps in book test class:
    1. configuration cfg = new AnnotationConfiguration();
    2. Session ss
    3. Transition tra
    4. ss.add
    5. tra.commit()
    0. add mapping class = "com.demo.model.Book" in hibernate.cfg.xml 


## Problem occurred when setting java
1. When you want to check what jdks you have, keep in mind that all jdks you have are located in this directory : cd /Library/Java/JavaVirtualMachines/
2. what you need to add in ~/.bash_profile
```
JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_31.jdk/Contents/Home  
PATH=$JAVA_HOME/bin:$PATH  
CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar 
```
3. After modify the ~/.bash_profile, you need source it : `source ~/.bash_profile` , so that this file can come into effect.
