# Design Patterns in JavaScript - DEV Community

Source: Article
Status: Unprocessed
URL: https://dev.to/zeeshanhshaheen/design-patterns-in-javascript-1pgm

![https://dev.to/social_previews/article/804881.png](https://dev.to/social_previews/article/804881.png)

---

20+ Design Patterns explanation in JavaScript

We will discuss implementation of Design Patterns by using JavaScript ES6 classes.

## Reference

[Design Patterns in JavaScript](https://www.udemy.com/course/design-patterns-javascript/) on [Udemy](https://www.udemy.com/) by Dmitri Nesteruk.

## 🚀 What are Design Patterns?

Design Patterns are the solutions to commonly occuring problems in software design. These patterns are easily re-usable and are expressive.

According to Wikipedia

> In software engineering, a software design pattern is a general reusable solution to a commonly occurring problem within a given context in software design. It is not a finished design that can be transformed directly into source or machine code. It is a description or template for how to solve a problem that can be used in many different situations.
> 

## Types of Design Patterns

## Creational Design Patterns

Creational Design Patterns will create objects for you instead of instantiating an object directly.

According to Wikipedia

> In software engineering, creational design patterns are design patterns that deal with object creation mechanisms, trying to create objects in a manner suitable to the situation. The basic form of object creation could result in design problems or added complexity to the design. Creational design patterns solve this problem by somehow controlling this object creation.
> 

## Factory Method
 It defines an interface for creating a single object and let childclasses to decide which class to instantiate.

According to Wikipedia:

> In class-based programming, the factory method pattern is a creational pattern that uses factory methods to deal with the problem of creating objects without having to specify the exact class of the object that will be created. This is done by creating objects by calling a factory method—either specified in an interface and implemented by child classes, or implemented in a base class and optionally overridden by derived classes—rather than by calling a constructor.
> 

### Example

Let's take an example of a point. We have a class of point and we have to create Cartesian point and Polar point. We will define a Point factory that will do this work

```
CoordinateSystem = {
  CARTESIAN: 0,
  POLAR: 1,
};

class Point {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }

  static get factory() {
    return new PointFactory();
  }
}

```

Now we will create Point Factory

```
class PointFactory {

  static newCartesianPoint(x, y) {
    return new Point(x, y);
  }

  static newPolarPoint(rho, theta) {
    return new Point(rho * Math.cos(theta), rho * Math.sin(theta));
  }
}

```

We will use our factory now,

```
let point = PointFactory.newPolarPoint(5, Math.PI/2);
let point2 = PointFactory.newCartesianPoint(5, 6)
console.log(point);
console.log(point2);

```

## Abstract Factory

It creates families or groups of common objects without specifying their concrete classes.

According to Wikipedia

> The abstract factory pattern provides a way to encapsulate a group of individual factories that have a common theme without specifying their concrete classes
> 

### Example

We will be using the example of Drink and Drink making machine.

```
class Drink
{
  consume() {}
}

class Tea extends Drink
{
  consume() {
    console.log('This is Tea');
  }
}

class Coffee extends Drink
{
  consume()
  {
    console.log(`This is Coffee`);
  }
}

```

Making Drink Factory

We will use our factory now

## Builder

It construct complex objects from simple objects.

According to Wikipedia

> The builder pattern is a design pattern designed to provide a flexible solution to various object creation problems in object-oriented programming.
> 

### Example

We will be using ab example of a person class which stores a Person's information.

Now we will create Person Builder

Now creating PersonJobBuilder that will takes Person's Job's information

PersonAddressBuilder will keep Person's Address' Information

Now we will use our builder,

## Prototype

It creates new objects from the existing objects.

According to Wikipedia

> The prototype pattern is a creational design pattern in software development. It is used when the type of objects to create is determined by a prototypical instance, which is cloned to produce new objects.
> 

### Example

We will be using example of car

Thst's how we will use this,

## Singleton

It ensure that there's only for object created for a particular class.

According to Wikipedia

> In software engineering, the singleton pattern is a software design pattern that restricts the instantiation of a class to one "single" instance. This is useful when exactly one object is needed to coordinate actions across the system.
> 

### Example

Creating a Singleton class

Thst's how we will use this,

## Structural Design Patterns

These patterns concern class and object composition. They use inheritance to compose interfaces.

According to Wikipedia

> In software engineering, structural design patterns are design patterns that ease the design by identifying a simple way to realize relationships among entities.
> 

## Adapter

This pattern allows classes with incompatible interfaces to work together by wrapping its own interface around existing class

According to Wikipedia

> In software engineering, the adapter pattern is a software design pattern that allows the interface of an existing class to be used as another interface. It is often used to make existing classes work with others without modifying their source code.
> 

### Example

We are using an example of calculator. Calculator1 is an old interface and Calculator2 is new interfcae. We will bw building an adapter that will wraps up new interface and will give us results using it's new methods,

Creating Adapter class,

Thst's how we will use this,

## Bridge

It separate the abstraction from the implementation so that the two can vary independently.

According to Wikipedia

> Bridge is a structural design pattern that lets you split a large class or a set of closely related classes into two separate hierarchies—abstraction and implementation—which can be developed independently of each other.
> 

### Example

We will be creating Renderer classes for rendering multiple shapes,

That's how we use this,

## Composite

composes objects so that they can be manipulated as single object.

According to Wikipedia

> The composite pattern describes a group of objects that are treated the same way as a single instance of the same type of object.
> 

### Example

We will be using job example,

Creating GroupEmployer,

Thst's how we will use this,

## Decorator

It dynamically adds or overrides the behaviour of an object.

According to Wikipedia

> The decorator pattern is a design pattern that allows behavior to be added to an individual object, dynamically, without affecting the behavior of other objects from the same class.
> 

### Exampe

We will be taking the example of color and shapes. If we have to draw a circle we will create methods and will draw circle. If we have to draw red circle. Now the beaviour is added to an object and Decorator pattern will helps me in that.

Creating ColoredShape class,

That's how we will use this,

## Facade

It provides a simplified interface to complex code.

According to Wikipedia

> The facade pattern (also spelled façade) is a software-design pattern commonly used in object-oriented programming. Analogous to a facade in architecture, a facade is an object that serves as a front-facing interface masking more complex underlying or structural code.
> 

### Example

Let's take an example of a client intracts with computer.

Creating Facade

That's how we will use this,

## Flyweight

It reduces the memory cost of creating similar objects.

According to Wikipedia

> A flyweight is an object that minimizes memory usage by sharing as much data as possible with other similar objects.
> 

### Example

Let's take an example of user. Let's we have multiple users with the same name. We can save our memory by storing a name and give it's reference to ther users having same names.

That's how we will use this. 
 Now we will make memory compersion without Flyweight and with Flyweight, by making 10k users.

## Proxy

By using Proxy, a class can represent functionality of another class.

According to Wikipedia

> The proxy pattern is a software design pattern. A proxy, in its most general form, is a class functioning as an interface to something else.
> 

### Example

Let's take an example of value proxy

That's how we can use that,

## Behavioral Design Patterns

Behavioral Design Patterns are specifically concerned with communication between objects.

According to Wikipedia

> In software engineering, behavioral design patterns are design patterns that identify common communication patterns among objects. By doing so, these patterns increase flexibility in carrying out communication.
> 

## Chain of Responsibility

It creates chain of objects. Starting from a point, it stops until it finds a certain condition.

According to Wikipedia

> In object-oriented design, the chain-of-responsibility pattern is a design pattern consisting of a source of command objects and a series of processing objects.
> 

### Example

We will be using an example of a game having a creature. The creature will increase it's defense and attack when it reaches to a certain point. It will create a chain and attack and defense will increase and decrease.

Increase attack,

Increase defense

That's how we will use this,

## Command

It creates objects which encapsulate actions in object.

According to Wikipedia

> In object-oriented programming, the command pattern is a behavioral design pattern in which an object is used to encapsulate all information needed to perform an action or trigger an event at a later time. This information includes the method name, the object that owns the method and values for the method parameters.
> 

### Example

We will be taking a simple example of bank account in which we give a command if we have to deposit or withdraw certain amonto of money.

Creating our commands,

That's how we will use this,

## Iterator

Iterator accesses the elements of an object without exposing its underlying representation.

According to Wikipedia

> In object-oriented programming, the iterator pattern is a design pattern in which an iterator is used to traverse a container and access the container's elements.
> 

### Example

We will be taking an example of an array in which we print the values of an array and then by using an iterator we print it's value backwords.

That's how we will use this,

## Mediator

Mediator pattern adds a third party object to control the interaction between two objects. It allows loose coupling between classes by being the only class that has detailed knowledge of their methods.

According to Wikipedia

> The mediator pattern defines an object that encapsulates how a set of objects interact. This pattern is considered to be a behavioral pattern due to the way it can alter the program's running behavior. In object-oriented programming, programs often consist of many classes.
> 

### Example

We will be using an example of a person using a chat room. Here a chatroom act as a mediator between two people communicating.

Creating chat room,

That's how we will use this,

## Memento

Memento restore an object to its previous state.

According to Wikipedia

> The memento pattern is a software design pattern that provides the ability to restore an object to its previous state. The memento pattern is implemented with three objects: the originator, a caretaker and a memento.
> 

### Example

We will be taking an example of a bank account in which we store our previous state and will have the functionality of undo.

Adding bank account,

That's how we will use this,

## Observer

It allows a number of observer objects to see an event.

According to Wikipedia

> The observer pattern is a software design pattern in which an object, named the subject, maintains a list of its dependents, called observers, and notifies them automatically of any state changes, usually by calling one of their methods.
> 

### Example

We will be taking an example of a person in which if a person falls ill, it will display a notification.

That's how we will use this,

## Visitor

It add operations to objects without having to modify them.

According to Wikipedia

> The visitor design pattern is a way of separating an algorithm from an object structure on which it operates. A practical result of this separation is the ability to add new operations to existing object structures without modifying the structures.
> 

### Example

We will be taking an example of NumberExpression in which it gives us the result og given expression.

Creating AdditionExpression,

That's how we will use this,

## Strategy

It allows one of an algorithms to be selected on certain sitution.

According to Wikipedia

> The strategy pattern is a behavioral software design pattern that enables selecting an algorithm at runtime. Instead of implementing a single algorithm directly, code receives run-time instructions as to which in a family of algorithms to use.
> 

### Example

We will take an example in which we have text processor that will display data based on strategy(HTML or Markdown).

Creating TextProcessor class,

That's how we will use this,

## State

It alter its behavior of an object when its internal state changes.

According to Wikipedia

> he state pattern is a behavioral software design pattern that allows an object to alter its behavior when its internal state changes. This pattern is close to the concept of finite-state machines.
> 

### Example

We will be taking an example of a light switch in which if we turned on or off the switch it state changes.

Creating state classes

That's how we use this,

## Template Method

It defines the skeleton of an algorithm as an abstract class, that how should it perforned.

According to Wikipedia

> Template Method is a method in a superclass, usually an abstract superclass, and defines the skeleton of an operation in terms of a number of high-level steps.
> 

### Example

We will be taking an example of a chess game,

Creating our chess class,

That's how we will use this,

## That was all about  **JavaScript Design Patterns**

I'll try to improve it further over time. If you think it needs some changes, write your suggestions in comments.

You would like to follow me on twitter [@zeeshanhshaheen](https://twitter.com/zeeshanhshaheen) for more updates.