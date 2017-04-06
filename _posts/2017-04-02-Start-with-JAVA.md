---
layout: post #post
title: Start from Java #post title
categories: Java #post category, seperated by spcace
tags: Java #post tag, seperated by spcace
---

## Start from Java

#### concepts list:
1. class
2. object
3. constructors
4. methods
5. inheritance
6. overloading/overriding
7. access specifiers
    1. private : The private members can be accessed only within the same class, but not outside the class.
    2. default -- same package (Default is not a keyword but reserved word in Java)
    3. protected -- same package, subclass
    4. public -- same package, subclass, others
8. access modifiers
    1. static 
    2. final
    3. abstract
    4. transient
    5. volatile
    6. synchronized
    7. native
9. abstract class
10. interface
11. inner classea
12. package 

#### Details:
1. terminal run java project:
    1. javac className.java
    2. java className
    3. start point of any program: main()
    1. As per the OOPS of Java, main() must be inside a class, it is also a member of a class
    2. before creating any object, main() must be identified from within the clas
    3. main() is declared as static, which can be accessed without creating any object
4. class: An object is an instance of a class used to access the members of a class.
5. method: A block which has a name, a return type (void if does not return anything) & contains set of statements to be executed is called as a method. 
    - method signature: return type, method name, parameters(doesn't include access specifiers like public...)
2.  scope of 
    1. local variable: only within a particular block. **Variables which are declared inside a block can be accessed only within the same block is called as Local Variables.**
    2. global variable: (There is no direct concept of global variable in java) 
        1. class variable(static): A class variable is a variable defined in a class  of which a single copy exists, regardless of how many instances of the class exist.
        ```
        class classVariable{
                //one fixed memory location shared by every instance
                private static int i = 0;
                ...
        }
        ```
        2. quiet like instance variable: declared in class, out of method, are only initialized when the class is instantiated.(Variables, which are  declared outside of any block but inside a class can be accessed throughout the class)
6. static：
    1. Any method which is static can access only other static members(static context)  directly,
    2. Any method which is static wants to access non-static members, an object of a class must be created.
    3. Where as a non-static method can access both static & non-static members directly. 
    4. The static modifier, in combination with the final modifier, is also used to define constants. The final modifier indicates that the value of this field cannot change.
    5. static variable: memory share variable x the whole class
    6. static method, static block: (and static variables) are all execuated before main `static { statement1; ...}`
    7. static class
    8. only 5,6,7, static variable, static method, static block, static class these four things can be static 
    9. Can class be static?
        Inner class can be static, top-level class can not.
    10. Is there will be a static variable inside of a function?
        Local variables can not be static, no private static(后半句很有可能是记错了)
        an explaination form stackoverflow
        ```
        /*
        where I use the private static variables is when you need to use a variable in a static function. For the static functions you can only use static variables, so you make them private to not access them from other classes. That is the only case I use private static for.
        Here is an example:
        */
        Class test {
                public static String name = "AA";
                private static String age;

                public static void setAge(String yourAge) {
                    //here if the age variable is not static you will get an error that you cannot access non static variables from static procedures so you have to make it static and private to not be accessed from other classes
                    age = yourAge;
                }
        }
        ```
6. inner class
    1. 
    2. 




7. constructor:
    1. defination:
        1. A block which contains same name as a class name, which does not have any return type,
        2. used for initializing the variables & objects
        3. will be executed automaticcly when an object of a class is initialized
    2. properties:
        1. By default, every class has default constructor, which initializes and object, and will be lost when a specific constructor is defined manually.
        2. A class can have any number of constructors, with a difference in type/number of parameters is called constructor overloading
        3. If we have two constructor in a class, and we called the default constructor, then we want to invoke another constructor, we can use keyword: this()
        ```
        class Example1{
                Example1(){

                }
                Example1(int i){

                }
        }
        ```
        4. if we use this() to invoke another constructor, we must put this() in the first line, or we will get a syntax error. 
        5. if we want to customize a constructor with parameters meanwhile, there is some obj using the default contructor, we need to write the default constructor, then write the new constructor(yes, we need to write 2 constructors).
        6. `class G extend F{ ... }` F's default constructor is invoked first, then invoke G's default or G(arg) constructor
8. Polymorphism: In a class, if more than one method is defined with a same name, then there must be a difference in type/number of parameters is called as Polymorphism (Method Overloading).
    - In method overloading, if the return type is changed, then there must be a change in type/number of parameters also.
9. toString
    1. The toString() method returns a textual representation of an object. A basic implementation is already included in java.lang.Object and so because all objects inherit from java.lang.Object it is guaranteed that every object in Java has this method.
    2. It is automatically invoked when the object is passed to println, print, printf, String.format() assert or the string concatenation operator. 
    3. if we want print a specific format of an object, we need to override toString() method in class
10. this
    1. to identify global variables within a local scope
    2. to invoke constructor of the same class from one constructor using this()
11. overriding：if a subclass contains a method, which has the same name, return type and parameters as a super class method, it's called method overriding
    1. private method of super class can not be overriding, it is just called redefined (because the private method is not visible in the subclass.).
    2. can not restrict it. eg: The default method of super class can be overridden by default, protected & public method of subclass; The protected method of super class can be overridden by protected & public method of subclass; The public method of super class can be overridden by only public method of subclass.
12. abstract:
    1. method: if only a method name must be declared, but not a body--abstract method
    2. class: In a class if any one of the method is abstract, then the whole class must be declared as abstract.
    3. Only a class & method can be declared as abstract. But not a variable.
    4. 
13. interface










#### some english
1. as per: both per and as per have existed in English in the sense “according to” for a very long time
2. identified from : be identified from within the class
3. instantiated: when the class is instantiated
4. semicolon  ['sɛmɪkolən] 分号