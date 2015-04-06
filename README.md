# CppDesignPatterns
Code implemetation for some of the mostly used design patterns in C++
Source for design pattern code implementation is http://sourcemaking.com/design_patterns
=========================
Singleton Design Pattern
=========================
Intent -->
1. Ensure a class has only one instance, and provide a global point of access to it.
2. Encapsulated "just-in-time initialization" or "initialization on first use".

Problem -->
Application needs one, and only one, instance of an object. Additionally, lazy initialization and global access are necessary.

Check list -->
1. Define a private static attribute in the "single instance" class.
2. Define a public static accessor function in the class.
3. Do "lazy initialization" (creation on first use) in the accessor function.
4. Define all constructors to be protected or private.
5. Clients may only use the accessor function to manipulate the Singleton.


==============================
Factory Method Design Pattern
==============================
Intent -->
1. Define an interface for creating an object, but let subclasses decide which class to instantiate. Factory Method lets a class defer instantiation to subclasses.
2. Defining a "virtual" constructor.
3. The new operator considered harmful.

Problem -->
A framework needs to standardize the architectural model for a range of applications, but allow for individual applications to define their own domain objects and provide for their instantiation.

Check list -->
1. If you have an inheritance hierarchy that exercises polymorphism, consider adding a polymorphic creation capability by defining a static factory method in the base class.
2. Design the arguments to the factory method. What qualities or characteristics are necessary and sufficient to identify the correct derived class to instantiate?
3. Consider designing an internal "object pool" that will allow objects to be reused instead of created from scratch.
4. Consider making all constructors private or protected.


======================
Facade Design Pattern
======================
Intent -->
Provide a unified interface to a set of interfaces in a subsystem. Facade defines a higher-level interface that makes the subsystem easier to use.
Wrap a complicated subsystem with a simpler interface.

Problem -->
A segment of the client community needs a simplified interface to the overall functionality of a complex subsystem.

Check list -->
1. Identify a simpler, unified interface for the subsystem or component.
2. Design a 'wrapper' class that encapsulates the subsystem.
3. The facade/wrapper captures the complexity and collaborations of the component, and delegates to the appropriate methods.
4. The client uses (is coupled to) the Facade only.
5. Consider whether additional Facades would add value.

========================
Observer Design Pattern
========================
Intent -->
1. Define a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.
2. Encapsulate the core (or common or engine) components in a Subject abstraction, and the variable (or optional or user interface) components in an Observer hierarchy.
3. The "View" part of Model-View-Controller.

Problem -->
A large design does not scale well as new graphing or monitoring requirements are levied.

Check list -->
1. Differentiate between the core (or independent) functionality and the optional (or dependent) functionality.
2. Model the independent functionality with a "subject" abstraction.
3. Model the dependent functionality with an "observer" hierarchy.
4. The Subject is coupled only to the Observer base class.
5. The client configures the number and type of Observers.
6. Observers register themselves with the Subject.
7. The Subject broadcasts events to all registered Observers.
8. The Subject may "push" information at the Observers, or, the Observers may "pull" the information they need from the Subject.

=====================
Proxy Design Pattern
=====================
Intent -->
Provide a surrogate or placeholder for another object to control access to it.
Use an extra level of indirection to support distributed, controlled, or intelligent access.
Add a wrapper and delegation to protect the real component from undue complexity.

Problem -->
You need to support resource-hungry objects, and you do not want to instantiate such objects unless and until they are actually requested by the client.

1. A virtual proxy is a placeholder for "expensive to create" objects. The real object is only created when a client first requests/accesses the object.
2. A remote proxy provides a local representative for an object that resides in a different address space. This is what the "stub" code in RPC and CORBA provides.
3. A protective proxy controls access to a sensitive master object. The "surrogate" object checks that the caller has the access permissions required prior to forwarding the request.
4. A smart proxy interposes additional actions when an object is accessed. 

=======================
Command Design Pattern
=======================
Intent -->
1. Encapsulate a request as an object, thereby letting you parameterize clients with different requests, queue or log requests, and support undoable operations.
2. Promote "invocation of a method on an object" to full object status
3. An object-oriented callback

Problem -->
Need to issue requests to objects without knowing anything about the operation being requested or the receiver of the request.

Check list -->
1. Define a Command interface with a method signature like execute().
2. Create one or more derived classes that encapsulate some subset of the following: a "receiver" object, the method to invoke, the arguments to pass.
3. Instantiate a Command object for each deferred execution request.
4. Pass the Command object from the creator (aka sender) to the invoker (aka receiver).
5. The invoker decides when to execute().
