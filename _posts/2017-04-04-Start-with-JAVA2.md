---
layout: post #post
title: Start from Java 2 #post title
categories: Java #post category, seperated by spcace
tags: Java #post tag, seperated by spcace
---

## Inner Class
1. Definition: A class defined in another class is called as an Inner Class.
The class which contains an Inner class is known as an enclosed class or Outer class.
2. Scope: The scope of an Inner class is limited to the boundary of Outer Class.
3. Inner class and Outer class:
    1. An Inner class can access all the members from Outer class including private members directly.(different from subclass). 
    2. However, an Outer class can access the Inner class members only through an object of Inner class.
    3. Any static method of outer class can access the member of non-static inner class as : <Object of Outer class>.<Runtime/Anonymous Object of Inner class>.member
    example(way-2):
    ```
    class OuterA {
            int x = 25;
            private String name = "Smith";

            class InnerA {

                double d = 23.45;

                void showIn() {
                    System.out.println(d);
                    System.out.println(name);
                    System.out.println(x);
                }	

            }

            // this method is part of the first way to invoke showIn() inside main
            void showOut() {
                InnerA obj = new InnerA();
                obj.showIn();
            }

            public static void main(String a[]) {
                OuterA o1 = new OuterA();
                //two ways to invoke showIn()
                //1. 
                o1.showOut();	
                //2. InnerA is a member of o1, just like other variables and methods
                o1.new InnerA().showIn();
                /*
                    what we can not do:
                    OuterA.InnerA in = new InnerA(); 
                    in.showIn();
                    because the prefix of OuterA.InnerA is supposed to be a package name rather than class name
                */
            }
    }
    ```
    4. An Inner class defined within a method can access everything from outside the method but only final type of variables or objects from within the method in which it is defined.（wt？？）
4. & static:
    1. Whenever an Inner class contains at least one static member, the whole Inner class must be declared as static Inner class.
    2. A static Inner class can access only static members of Outer class directly & to access Non-static members it has to create an Object of Outer class.




## Abstract Class Vs Interface
0. abstract:
    1. method: if only a method name must be declared, but not a body--abstract method
    2. class: In a class if any one of the method is abstract, then the whole class must be declared as abstract. The class which extends an abstract class, it must override all the abstract methods of the super class, otherwise, the subclass must also be declared as abstract.
    3. Only a class & method can be declared as abstract. But not a variable.
    4. abstract and static cannot be used together for a method.
    5. An abstract class can not be instantiated as it is termed as incomplete (non-concrete) in terms of its definition.(The class which is having all the methods defined with a body is called as concrete class.)
1. interface
    1. definition:
    contains only abstract methods, which will be used for multiple inheritance.
    2. rules:
        1. A class can implement any number of Interfaces
        2. A class which implements an interface must override all the methods of Interface, otherwise the class must be declared as abstract.
        2. All the methods of an interface must be overridden by “public” access specifier.
        2. An interface cannot be instantiated.(the same as abstract class)


## final:
- final class can not be inherited (compile error)
- final method can not be overriden in subclass (compile error)
- the value of a final variable can not be changed
- the reason to declare a method or class "final" is to improve the speed of a program