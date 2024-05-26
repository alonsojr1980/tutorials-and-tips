The GoF (Gang of Four) design patterns are 23 patterns that were first described in the book "Design Patterns: Elements of Reusable Software" by Erich Gamma, Richard Helm, Ralph Johnson, and John Vlissides. Here's the list of all 23 GOF design patterns, along with a brief explanation of each:

**Creational Patterns (5)**

1. **Abstract Factory**: Provides an interface for creating families of related or dependent objects without specifying their concrete classes.
2. **Builder**: Separates the construction and representation of an object, allowing you to construct complex objects step-by-step.
3. **Factory Method**: Provides a way to create objects without specifying the exact class of object that will be created.
4. **Prototype**: Creates a new object by copying an existing object.
5. **Singleton**: Ensures a class has only one instance and provides a global point of access to it.

**Structural Patterns (7)**

1. **Adapter**: Converts the interface of a class into another interface that clients expect.
2. **Bridge**: Separates an object's abstraction from its implementation, allowing them to vary independently.
3. **Composite**: Composes objects in terms of smaller independent objects, allowing you to treat individual and composite objects uniformly.
4. **Decorator**: Allows an object to add additional responsibilities to another object without affecting the existing object's external interface.
5. **Facade**: Provides a simplified interface to a complex system of classes or interfaces.
6. **Flyweight**: Reduces memory usage by sharing instances of large objects, like graphics or text.
7. **Proxy**: Acts as an intermediary between a client and an object, controlling access to the object.

**Behavioral Patterns (11)**

1. **Chain of Responsibility**: Allows multiple objects to handle a request without having them know about each other's existence.
2. **Command**: Encapsulates a command or action in an object, allowing you to execute it later.
3. **Interpreter**: Interprets or executes a set of rules or grammar defined by an abstract syntax tree (AST).
4. **Iterator**: Provides a way to access the elements of an aggregate object without exposing its underlying representation.
5. **Mediator**: Reduces coupling between classes that communicate with each other, promoting loose coupling and better scalability.
6. **Memento**: Allows you to capture and externalize an object's internal state, allowing it to be restored later.
7. **Observer**: Notifies objects about changes to another object without having a direct reference to the changed object.
8. **State**: Allows an object to change its behavior when its internal state changes.
9. **Strategy**: Defines a family of algorithms and encapsulates each one in a separate class, allowing you to choose between them at runtime.
10. **Template Method**: Provides a way to define a method that can be customized by subclasses.
