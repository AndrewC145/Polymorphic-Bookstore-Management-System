# Polymorphic Bookstore Management System

## Reflection Questions

1. Abstraction Understanding: How does the abstract Material class enforce a contract for its subclasses? What would happen if we made Material a concrete class instead?

The abstract Material class enforces a contract for its subclasses through using the abstract keyword on methods such as getCreater() and getDisplayInfo(), or simply just declaring abstract methods, meaning that it will need to be implemented by the subclasses that extend from the Material class. Using abstract on the Material Class, it shares common code and behaviour for its subclasses, but certain methods may be very different, so they must provide their own implementation.

If Material were a concrete class instead, this breaks the purpose of object-oriented programming, since we do not want Material to be instantiated and that it should only be inherited for its subclasses. Also, the subclasses are expected to override the required abstract methods to implement their own logic to it, and a contract is no longer enforced.

2. Polymorphism in Practice: Describe a real-world scenario where you would use polymorphism similar to this bookstore system. How would it improve code maintainability?

An example where polymorphism can be used is an employee management system. For example the base class is Employee, with a default method of calculating their pair, so int calculateWeekPay(), returning 1500 by default, and then for every other subclass extending that Employee superclass, such as Intern, Manager, Worker, Supervisor, etc, will override the calculatePay() method and implement their own specific logic. Ex. class Manager extends Employee, @Override int calculateWeekPay() { return 5000 }

It would improve code maintainability by if a new type of employee were to be added, there is no need to edit the parent class, but only the subclass that is inheriting from it, essentially allowing for more code reusability since the class can be used with different types of objects, as well as different classes, in this case, Manager, Intern, etc to be treated as part of a common superclass; Employee.

3. Interface Design: Why is the Media interface valuable even though AudioBook and VideoMaterial already extend Material? What principle does this demonstrate?

The media interface demonstrates the I in the SOLID principles, interface segregation, separating larger interfaces into smaller ones, so we only implement classes depending on the required methods needed. For example, if it wasn’t split up and everything was put inside the Material class, only AudioBook and VideoMaterial would need access to methods like getDuration, getFormat, etc whereas other subclasses like Book and PrintedBook have no use for them and those methods are irrelevant but would have to be implemented.

So, the Media interface is valuable as it separates methods that are required by certain subclasses and types of Materials, rather than just putting everything into one big Material class where some methods are unnecessary and will go unused. 

6. Design Patterns: Which design pattern from the lab do you find most useful? How would you apply it in your own projects?

I found the factory design pattern the most useful. One instance of where this project uses factory pattern is with the `MaterialFactory` class. It forces all child class of `Material` to be created through the factory class, ensuring that no constructors are exposed. The `MaterialFactory` simply takes 2 parameters, the type of material, and its properties. This security feature ensures that no outside program can create instances of materials without knowing the parameters. Also, the factory itself have validate methods that ensures that the data correctness before creating any object. 

I would apply the Factory Pattern in any project that involves managing a hierarchy of interchangeable products or entities whose specific type is determined at runtime based on external input or configuration. For example a notification push system. There can be different types of notifications such as email, SMS, internal alerat and push notification.

7. Performance Considerations: What are the performance implications of using ArrayList vs HashMap for the bookstore? When would you choose each?

To understand the difference in performance, we need to take a look at two main factors: search speed and insert speed.

`ArrayList` can insert items at constant time, given that all we have to do is allocate a new space in memory and have the previous last element point towards it. For instance where I need to add items fast, I will use an `ArrayList`.

However, we cannot ignore the efficiency of `HashMap` when it comes to searching. Thanks to the hashing function, it can quickly calculate the index of a certain item within the table.(Assuming we have no hashing collision) Therefore the time it takes to search for an item is constant time, O(1).

Finally, the choice between the two. I will choose `ArrayList` if we have a small dataset where the serial order of items matters and we need to constantly loop through all data to generate a report. Otherwise, given a large data set and the main function of repeated seraching an item base on a key, I will choose a `Hashmap`.


