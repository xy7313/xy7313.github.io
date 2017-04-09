---
layout: post #post
title: Start from Java 3 #post title
categories: Java #post category, seperated by space
tags: Java #post tag, seperated by space
---

## Singleton
1. How to implement singleton: make constructor private
2. Eager initialize: before invoke, it has initialized already. The class is loading, the variable is initialized.
```
public class EagerInitialized {
        //private constructor to avoid client applications to use constructor
        private EagerInitialized(){

        }
        
        //initialize an object using keyword: static to ensure only one object exist.
        private static final EagerInitialized instance = new EagerInitialized();

        //we need a public method to make an EagerInitialized obj visible to others
        public static EagerInitialized getInstance(){
                return instance;
        }

        public static void main(String a[]) {
                EagerInitialized obj = EagerInitialized.getInstance();
                //...
        }
}
```
3. Lazy initialize: declare first but not initialize
```
public class LazyInitialized {
        /*
        1. private constructor to avoid client applications to use constructor
        2. initialize an object using keyword: static to ensure only one object exist.
        3. we need to check if the instance existed before we create a new one
        */
        private LazyInitialized(){

        }
        
        private static final LazyInitialized instance;

        public static LazyInitialized getInstance(){
            if(instance == null) instance = new LazyInitializedSingleton();
            return instance;
        }

        public static void main(String a[]) {
            LazyInitialized obj = LazyInitialized.getInstance();
                //...
        }
}
```

4. Double check:
6. Bill PUGH: create singleton using inner class.

## Exception Handling
1. When a runtime error occurs, the JVM "throws" an exception, prints an error message, and quit
2. try catch:
    1. The code inside "try" braces will execute
    2. If the try code executes normally, we skip over the catch clauses.
    3. If the try code throws an exception, JAVA doesn't finish the try code and it jumps directly to the catch clause, which matches the exception.
    4. when the catch clause finished executing, java jumps to the next line immediately after all catch clauses.
    5. Execute code in finally clause, if there is any finally clause exist.
    6. an example:
    ```
    FileInputStream f = new FileInputStream("fileName");
    try{
            statementX;
            return 1;
    } catch (IOException e) {
            e.printStackTrace();
            return 2;
    } finally {
            f.close;
    }
    ```
    7. Rules:
        1. A try block must have either catch or finally block
        2. A try block can have multiple catch blocks.
        3. In a try block, if both super class Exception & an actual Exception are declared, as the super class Exception catches all the Exceptions indirectly, the actual Exception must not be declared after the super class Declaration(or we get an error : exception has been caught). ** So, always the Super class Exception must be the last catch block declaration. **
        4.  A try block can be defined inside another try/catch/finally block, called as Nested try block.

3. Error vs. Exception
    1. An Error "indicates serious problems that a reasonable application should not try to catch."
    2. An Exception "indicates conditions that a reasonable application might want to catch." In a program, when some statements are not being executed, it gives a runtime error which is called as Exception
    3. For All kinds of Exceptions the super class is java.lang.Exception.
 
4. Checked/unchecked Exception
    1. Checked exceptions are the exceptions that are checked at compile time; Unchecked exceptions are the exceptions that are not checked at compiled time.
    2. If some code within a method throws a checked exception, then the method must either handle the exception or it must specify the exception using throws keyword.
    3. Error along with RuntimeException & their subclasses are unchecked exceptions. All other Exception classes are checked exceptions.（in another words, in Java exceptions under Error and RuntimeException classes are unchecked exceptions, everything else under throwable is checked.)
    4. Examples:
        1. Unchecked Exceptions
            - IOException: FileNotFoundException, EOFException...
            - SQLException: ConnectionException...
        2. Checked Exceptions
            - NullPointerException
            - ArithmeticException
            - NumberFormatException
	        - ConnectionException			
            - ClassNotFoundException
			- IllegalArgumentException
    6. More about check exception and uncheck exception: http://netjs.blogspot.com/2015/05/difference-between-checked-unchecked-exception-java.html 

5. Customize exception
    1. The user defined exceptions should be created by extending java.lang.Exception class;
    2. must have at least an Error Message to prompt to the user; 
    3. must be thrown manually by using a Keyword “throw”.
    4. must be declared with a throws clause.
    5. The method which is declared with the throws declaration must be called within a try catch block or that block must also be declared with the “throws” keyword.
    6. Example:
    ```
    class InvalidArgException extends Exception {

            double arg;

            InvalidArgException(double arg) {
                    this.arg = arg;
            }

            public String toString() {
                    return "InvalidArgException : " + arg;
            }
        
    }
    ```
    ```
    class TestArgument {    
            public void test(double arg) throws InvalidArgumentException {
                    if(arg < 10 && art > 0) System.out.println("Great!!");
                    //throw a new customized exception
                    else throw new InvalidArgumentException(arg);
            }
            public static void main(String a[]) {
                    Test t = new TestArgument();
                    try{
                        t.test(Double.parseDouble(a[0]));
                    } catch(InvalidArgumentException iae) {
                        iae.printStackTrace();
                        System.out.println(iae);
                    }
            }
    }
    ```
    7. 

## Serialization
1. Objects are temporary, files are permanent. When we want to write object to file, we serialize the object first.
2. Example:
```
//we have a class A, which implements Serialization, if not implements this mock interface, our writing can not succeed.
class A implements Serialization{
        private int id;
        private String name;
        A(){

        }
}

//service class to write and read(serialize and deserialize the obj)
class B{
        public static void main(String a[]) {
               //Chain of stream:

        }
}
```
3. mock interface: they do not have any functions.


