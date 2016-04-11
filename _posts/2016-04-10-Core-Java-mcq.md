---
layout: post
title:  "Core Java concept questions"
date:   2016-04-10 15:48:08
categories: jekyll update
---
  
  
  6.  Enhance vs. Traditional For Loop  
  In which of the following scenarios is it appropriate to use the enhanced for loop as opposed to the traditional for loop?
   A. when you need access to the index of the current element within the body of the loop  
   B. with an array  
   C. when you need to iterate an array in reverse  
  D. All of the above  
  
  
  7. Starting an Already Running Thread  
  Which of the following will happen if you try to start a thread that has already  been started?   
    a. it keeps running with no interruption  
    b. it thrown an IllegalThreadSateException  
    c. It termites and restarts  
    d. It restarts if it was terminated.  
  
  8. Transient keyword  
  When the keyword “transient” is applied to a viable, it ...    
      a. .. marks it for garbage collection immediately after use  
      b. …ensures every thread accessing it reads the latest value of the variable.  
      c. … makes it as inaccessible from outside the class.  
      d. … excludes it from serialization.  
  选的d
  
  10. Swing Layouts
  which of the following layouts does Swing use by default?
  a. DefaultLayout  b.CardLayout  c. GridLayout  d.FlowLayout
  
  14. Inner Class
  An inner class can be which of the following?
  a. private,   b final   c. anonymous  d. A and C  e All of the above
      inner classes can be defined in four different following ways as mentioned below:
      1) Inner class
      2) Method – local inner class
      3) Anonymous inner class
      4) Static nested class
       Inner class acts as a member of the enclosing class and can have any access modifiers: abstract, final, public, protected, private, static.
  
  
  15. Which of the following statements about declaring a method to be package private is TRUE?
  
  16.  Collection to Store List of Pairs
    ```code
       a. Hashmap
          b. Map.Entery
          c. Hashtable
          d. Properties
          e. TreeMap
          ```
  
  17. In a try/catch/finally block, finally gets called.
  Update: Finally ALWAYS gets executed, no matter what happens in the try or catch block (fail, return, exception, finish etc.).
  
  18. Object class methods
  Which of the following is a method declared by the Object class?
  Give the list of Java Object class methods.
  
  Answer: above of all
  <br />  clone() - Creates and returns a copy of this object.
  <br />  equals() - Indicates whether some other object is "equal to" this one.
  <br />  finalize() - Called by the garbage collector on an object when garbage collection
  <br />          determines that there are no more references to the object.
  <br />  getClass() - Returns the runtime class of an object.
  <br />  hashCode() - Returns a hash code value for the object.
  <br />  notify() - Wakes up a single thread that is waiting on this object's monitor.
  <br />  notifyAll() - Wakes up all threads that are waiting on this object's monitor.
  <br />  toString() - Returns a string representation of the object.
  <br />  wait() - Causes current thread to wait until another thread invokes the notify() <br />  method or the notifyAll() method for this object.
  
  19.  Which of the following is an effective way to render a variable constant?  
    <br /> A        declare it as final  
    <br /> B        declare it as static  
    <br /> C        declare it as an enum member  
    <br /> D        A and C  
    <br /> E        All of the above  
  
  20. Polymorphism  
  Based on the code snippet below, which of the following statements about the last line of the code, indicated by the "(X)", is TRUE?
  
  
  21. Core Library Knowledge  
  
  Based on the code snippet below, which of the following statements is FALSE?
  
  InputStreamReader ir = new BufferedReader( new FileReader( new File( "file.txt" ) ) );  
       A        This buffers the characters being read in and may be more efficient than reading straight from the FileReader.
      B        This is useful when reading characters rather than bytes.
      C        This exhibits the use of the Decorator design pattern.
      D        This can be used to read either a stream of bytes or characters.  
  选a  
  
  http://stackoverflow.com/questions/9648811/specific-difference-between-bufferedreader-and-filereader
  
  
  22. Auto example  
  The code snippet below is an example of which of the following?
  Long myLong = 21l;
      A        Autoboxing
      B        Autounboxing
      C        Autocasting
      D        Autoinstancing
  
  http://stackoverflow.com/questions/20922867/java-class-long-method-longvalue
  
  Autoboxing
  
  23.  Dynamically Combine Strings  
  To dynamically combine multiple strings into a single one in Java, you should...
      A        ...use the subclass String to add a constructor which takes in the contributing strings.
      B        ...use the String.join method.
      C        ...use StringBuilder.
      D        ...add them using the "+" operator, then call toString on the combined String and wrap it into a new String instance (like new String( combinedString ) to ensure that it gets interned.
  
  It is better to use StringBuilder
  ```java
   StringBuilder sb= new StringBuilder();
  
  for(String tempString:setInput){
     sb.append(",").append(tempString).append(",");
   }
  ```
  
  24.  Switch Statement
  Given the switch statement below, which of the following statements is FALSE?
      A        The expression must be of a primitive type, such as int, byte, or short.
      B        The variables 'value_1', 'value_2' etc. need to be known at compile time.
      C        The default case always comes last.
      D        The break at the end of each case is optional.
  
  25.  Final Block Execution
  Based on the code block below, the finally block will be executed.
  A true
  
  26.  ArrayList Capacity
  The capacity of an ArrayList...  
      A        ...is set to zero at initialization.
      B        ...is set to infinite at initialization.
      C        ...is at least as large as the size at initialization.
      D        ...cannot be specified.
  
  27. Reference Types  
  Which of the following class names is a legal Reference subtype in Java?  
      A        StrongReference
      B        GhostReference
      C        SoftReference
      D        All of the above
  
  28.  Supported Java Feature
  Which of the following features is supported by Java?  
      A        An elegant model for multiple inheritance.  
      B        The freedom from memory management.  
      C        User definable operator overloading.  
      D        The ability to do pointer arithmetic.  
  
  29.  Marker Interface
  Which of the following is considered a marker interface?
  
      A        Cloneable  
      B        Runnable  
      C        Iterable  
      D        Comparable  
  
  Marker interface is also called tag interface by some java gurus. In java we have the following major marker interfaces as under:
  
      Searilizable interface
      Cloneable interface
      Remote interface
      ThreadSafe interface
  
  30.  Read-Only List
  You are given a requirement to create a read-only list. Which of the following approaches should you use?
  
      A        Create members as final and add them to the list.
      B        Build your list and wrap it with a call to Collections.unmodifiableList().
      C
      D        Declare the list final.
   
   In Java you can use Collections.unModifiableList() method  to create read only List , Collections.unmodifiableSet() for creating read-only Set like read only HashSet and similarly creating a read only Map in Java, as shown in below example. Any modification in read only List will result in java.lang.UnSupportedOperationException in Java.
  
  31.  Finding Errors
  Which of the following indicates what is WRONG with the statement below?
  
      A
      B        The left hand side allows objects to be stored in the collection, while the right hand side restricts collection members to being strings.
      C        An ArrayList cannot be a list.
      D        All of the above
  
  32.  Declared Throwables
  Which of the following Throwables needs to be declared?
  A        Error
  B        RuntimeException
  C        CheckedException
  D        Exception
  
  选c
  There are two special cases: Error and RuntimeException: these two classes (and their subclasses) are considered unchecked exceptions, and are either frequent enough or catastrophic enough that you do not need to declare them in throws clauses. Everything else is a checked exception, and is ususally a subclass of Exception; these exceptions have to be handled or declared.
  
  33.  Concurrent Usage
  Which of the following is the LEAST suitable for concurrent usage?
  A        new ArrayList();
  B        Collections.unmodifiableList( new ArrayList() );
  C        Collections.synchronizedList( new ArrayList() );
  D        new ConcurrentLinkedQueue();
  我选的a
  http://stackoverflow.com/questions/561671/best-way-to-control-concurrent-access-to-java-collections
  
  34.  Java Interfaces
  Which of the following statements about interfaces in Java is TRUE?
  A        They can contain variable definitions.
  B        They can be extended by subinterfaces.
  C        They can contain method implementations.
  D        A and B
  E        All of the above
  
  answer: D
  https://en.wikipedia.org/wiki/Interface_%28Java%29#Defining_an_interface
  
  35.  Abstract Classes
  Which of the following indicates when you can use abstract classes?
  A        when inheriting behavior from multiple parents
  B        to extract common behavior into a parent
  C        when designing for inheritance where the final implementations are not known beforehand
  D        B and C
  E        All of the above
  http://www.javacoffeebreak.com/faq/faq0084.html
  
  D
  http://www.artima.com/objectsandjava/webuscript/CompoInherit1.html
  
  36.  Generics Knowledge
  Given the declaration below, the myCollection will only accept...
  
  Collection myCollection;
      
      A        ...instances of the class Object.
      B        ...any Object.
      C        ...nothing.
      D        ...instances of the class '?'.
  选b
  
  37.  JUnit
  Which of the following describes the purpose of JUnit?
  A        It is a framework to help with writing unit tests for your code.
  B        It is a framework to help with writing code involving unit conversions.
  C        It is a framework to help with packaging your code into units for distribution.
  D        It is a framework to convert all days/dates in your code to June.
  
  选a
  
  38.  AtomicInteger Class
  Which of the following statements about the AtomicInteger class is TRUE?
  A        It is useful for nuclear computations.
  B        It is a subclass of Integer.
  C        It supports the autoboxing of numerical values.
  D        It allows for atomic update and read operations on an integ
  
  选d
  
  39.  Final Keyword
  The keyword "final" can be applied to which of the following?
  A        a variable
  B        a method
  C        a class
  D        All of the above
  
  选d
  