# Functional programming vs OOP: comparing paradigms

Source: Article
Status: Unprocessed
URL: https://www-imaginarycloud-com.cdn.ampproject.org/c/s/www.imaginarycloud.com/blog/functional-programming-vs-oop/amp/

![https://images.unsplash.com/photo-1587620962725-abab7fe55159?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxMTc3M3wwfDF8c2VhcmNofDJ8fHByb2dyYW1taW5nfGVufDB8fHx8MTYyNjc5NzQ2OA&ixlib=rb-1.2.1&q=80&w=2000](https://images.unsplash.com/photo-1587620962725-abab7fe55159?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxMTc3M3wwfDF8c2VhcmNofDJ8fHByb2dyYW1taW5nfGVufDB8fHx8MTYyNjc5NzQ2OA&ixlib=rb-1.2.1&q=80&w=2000)

---

[Functional%20programming%20vs%20OOP%20comparing%20paradigms%20625fc26a685b435ab972cdab522655e6/photo-1587620962725-abab7fe55159](Functional%20programming%20vs%20OOP%20comparing%20paradigms%20625fc26a685b435ab972cdab522655e6/photo-1587620962725-abab7fe55159)

Functional programming and object-oriented programming (OOP) have very distinct approaches to programming. This article explains in detail what each of the programming paradigms consists of and further sums up their key takeaway differences.

## Table of Contents

[Programming ParadigmsFunctional ProgrammingObject-Oriented ProgrammingPure functionsObjects and classes](https://www-imaginarycloud-com.cdn.ampproject.org/c/s/www.imaginarycloud.com/blog/functional-programming-vs-oop/amp/)
 ➤ [Mutable vs Immutable](https://www-imaginarycloud-com.cdn.ampproject.org/c/s/www.imaginarycloud.com/blog/functional-programming-vs-oop/amp/)
 ➤ [Imperative vs DeclarativeFunctional programming vs OOP: key takeaway differencesConclusion](https://www-imaginarycloud-com.cdn.ampproject.org/c/s/www.imaginarycloud.com/blog/functional-programming-vs-oop/amp/)

A programming paradigm is an approach (or method) to solve a certain programming task. Paradigms represent the different **strategies**, **principles**, and **rules** a developer can implement to develop software. Every existing programming language (and there are many) must follow at least one **programming paradigm**. Despite their differences, all paradigms have their pros and cons, which is why a growing number of popular programming languages prefer offering **multi-paradigm programming** instead of following strictly just one. However, it usually comes down to the developers' preferences and the applications' goals.

Also, it is rare to be a "pure" language that only supports 100% one paradigm. For instance, [Java](https://www.imaginarycloud.com/blog/kotlin-vs-java/) is known to be an object-oriented programming (OOP) language, but is it 100% OOP? Well, maybe not 100%, but close, which is enough to sustain its reputation as "one of the purest" OOP languages.

Nowadays, there is an incredible number of programming paradigms that we can follow. In short, there are two main paradigms - **imperative and declarative** - which influence multiple programming paradigms. Among some of the most popular ones, we have logic programming paradigm, procedural programming paradigm, and, of course, functional and object-oriented programming.

Functional programming is a declarative programming paradigm that writes in **pure functions**, meaning that these functions do not modify variables but instead generate new ones as an output. In other words, the output of a pure function only depends on the input parameters; thus, there is no external impact, which avoids side effects. Moreover, writing pure functions also helps developers avert mutable data and shared state.

Therefore, functional programming has many benefits and is used in a lot of programming languages and frameworks. It is a popular programming paradigm due to its ability to **create maintainable and clean software** by using functions, which are vital to code organization.

Object-oriented programming is a programming paradigm that organizes data and the software structure based on the concept of **classes and objects**.

**Classes** are a set of instructions (or blueprints) that establish a data structure for a specific object, determining what the object will contain (the types of variables that can exist in an object) and how it will behave (the methods or member functions that define how to operate on the variables). Thus, **objects** are instances of classes since classes work as "templates" to create objects. Plus, objects can contain data in the form of fields (also known as attributes) and code in the form of procedures (also named methods).

As mentioned, functional programming relies on functions, whereas object-oriented programming is based on classes and respective objects. A **function** is a process that retrieves a data input, processes it, and then returns an output. Therefore, functions are modules of code written to achieve a certain task. Pure functions are "pure" because they always return the same output for the same argument values.

Further, the pure function application **does not have side effects** since there is no variation with local static variables, mutable reference arguments, input streams, or other external aspects. They are entirely independent of any state; they just need the inputs. This characteristic has four main advantages:

- Good **readability and comprehension** since they are atomic.
- Pure functions are a good solution for **parallel processing** across distributed computing clusters and CPUs.
- Since pure functions are independent, it is **easier to refactor and reorganize** them within the code. Plus, being independent from the outside also makes them more **portable and easier to reuse** in other applications.
- Pure functions can be **easily tested**, considering that all it takes is to test the inputs and confirm the (expected) result.

Hence, pure functions are very simple and reusable blocks of code that can be extremely practical when implementing a program. Therefore, it makes perfect sense that **functions are the primary unit of functional programming**. Even though it is possible to create pure functions in OOP, it is not this paradigm’s main focus since its main unit is objects, which in turn are designed to interact with the object's state.

The downside of pure functions is that it prioritizes operations over data. If a pure function only produces outputs with identical inputs, then it cannot return other different (and perhaps meaningful) values. For this reason, functional programming is extremely **operational**, practical, and, as the name indicates, functional.

Object-oriented programming relies greatly on the concept of classes and objects, which in turn contain functions and data. As explained, a class is an established blueprint (or prototype) from which objects are built. Thus, classes represent a set of methods (or properties) that are common to a certain object's type. In turn, an **object is the basic unit of OOP** and represents real-life entities. An object must have:

- **An identity:** a unique name; having a unique ID allows objects to interact with other objects.
- **A state:** an object's state reflects the properties or attributes of an object.
- **Behavior:** the methods of an object and how objects will respond and interact with other objects.

For instance, let's imagine we have "Athlete 1" as an object, and within that object, we have all the data about the object through the properties. Thus, the state could be sport, height, weight, trophies, country, etc. These properties store data, and an **object's data** can be manipulated through functions attributed to an object. In this case, this object's methods could be attack, defense, jump, run, sprint, etc. Further, the developer can create properties by declaring variables in the object's code module.

In sum, in OOP languages, the data is stored in the properties, and the logic behind lies in the **functions and respective methods**. Regarding object-oriented programming, methods are functions that belong to a class or object; **methods are "owned" by a specific class** or even object. In comparison, **functions are "free"**, meaning they can be on any other scope of the code, not belonging to classes or objects. Therefore, a method is always a function, but a function is not always a method. When objects contain properties and methods that work closely together, those objects belong to the same class.

In an OOP language, code is written to define the classes and, consequently, the respective objects. Pure object-oriented languages follow the **four core principles**: encapsulation, abstraction, inheritance, and polymorphism.

[data:image/svg+xml;charset=utf-8,%3Csvg xmlns='http%3A//www.w3.org/2000/svg' xmlns%3Axlink='http%3A//www.w3.org/1999/xlink' viewBox='0 0 10 5'%3E%3Cfilter id='b' color-interpolation-filters='sRGB'%3E%3CfeGaussianBlur stdDeviation='.5'%3E%3C/feGaussianBlur%3E%3CfeComponentTransfer%3E%3CfeFuncA type='discrete' tableValues='1 1'%3E%3C/feFuncA%3E%3C/feComponentTransfer%3E%3C/filter%3E%3Cimage filter='url(%23b)' x='0' y='0' height='100%25' width='100%25' xlink%3Ahref='data%3Aimage/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAoAAAAFCAIAAADzBuo/AAAAf0lEQVQI1z3BWw7CIBAF0MuEAH1YjH64DnWnjbtyJzYmJh0qYDvjX89BznnbRFUn1vuot1En1h1574kMAK6YK5YKrtiZx5MNEAN9sryTsYTY6MERV1HAXvsl0O9LQxfmEl3XtlJ4dWfKr4rGDl0IgHN9JC3qU0reiEAvp2Na7R+LdUcCimwNowAAAABJRU5ErkJggg=='%3E%3C/image%3E%3C/svg%3E](data:image/svg+xml;charset=utf-8,%3Csvg xmlns='http%3A//www.w3.org/2000/svg' xmlns%3Axlink='http%3A//www.w3.org/1999/xlink' viewBox='0 0 10 5'%3E%3Cfilter id='b' color-interpolation-filters='sRGB'%3E%3CfeGaussianBlur stdDeviation='.5'%3E%3C/feGaussianBlur%3E%3CfeComponentTransfer%3E%3CfeFuncA type='discrete' tableValues='1 1'%3E%3C/feFuncA%3E%3C/feComponentTransfer%3E%3C/filter%3E%3Cimage filter='url(%23b)' x='0' y='0' height='100%25' width='100%25' xlink%3Ahref='data%3Aimage/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAoAAAAFCAIAAADzBuo/AAAAf0lEQVQI1z3BWw7CIBAF0MuEAH1YjH64DnWnjbtyJzYmJh0qYDvjX89BznnbRFUn1vuot1En1h1574kMAK6YK5YKrtiZx5MNEAN9sryTsYTY6MERV1HAXvsl0O9LQxfmEl3XtlJ4dWfKr4rGDl0IgHN9JC3qU0reiEAvp2Na7R+LdUcCimwNowAAAABJRU5ErkJggg=='%3E%3C/image%3E%3C/svg%3E)

Let's start by focusing on encapsulation. **Encapsulation** is highly important in OOP since it consists of the ability to encapsulate variables within a class from outside access. Properties and methods can be private or public. OOP languages allow developers to establish multiple degrees of visibility. On the one hand, private features can only be visible for the class itself. On the other hand, public features can be visible to everyone.

**Inheritance** is also extremely vital since it provides a mechanism to organized and structure the software. It allows classes to inherit states and behaviors from their superclasses, which also means that this principle supports reusability.

Object-oriented programming can support mutable data. Contrarily, functional programming uses immutable data instead. In both programming paradigms, an **immutable object** refers to an object whose state cannot be modified once created. A **mutable object** consists of exactly the opposite; an object's state can be modified even after being created.

In pure functional programming languages (e.g., Haskell), it is **impossible to create mutable objects**. Thus, objects are typically immutable. In OOP languages, the answer is not that straightforward since it depends more on **the specifications of each OOP language**. String and concrete objects can be expressed as immutable objects in order to improve runtime efficiency as well as readability. Plus, immutable objects can be very helpful when handling multi-threaded applications because it avoids the risk of the data being changed by other threads.

Mutable objects also have their advantages. They allow developers to make changes directly in the object without allocating it, saving time and speeding up the project. However, it is up to the developer and the development team to decide whether it actually pays off according to the project's objectives. For instance, mutation can also open more doors for bugs, but sometimes its speed is very suitable and even necessary.

Therefore, OOP can support mutability, but its languages may also allow for immutability. Java, C++, C#, Python, [Ruby](https://www.imaginarycloud.com/blog/ruby-vs-python-for-web-development/), and Perl can be considered object-oriented programming languages, but they **do not support mutability or immutability exclusively**. For example, in Java, the strings are immutable objects. Nonetheless, Java also has mutable versions of strings. Similarly, in C++, developers can declare new class instances as immutable or as mutable. Another good example is Python, which has built-in types that are immutable (e.g., numbers, booleans, frozensets, strings, and tuples); however, the custom classes are usually mutable.

It is also important to keep in mind that many of the mentioned languages are not 100% functional programming or object-oriented. For instance, [Python](https://www.imaginarycloud.com/blog/python-vs-javascript/) is one of the most popular languages, and it truly is a **multi-paradigm language**. Thus, it can entail a more functional or OOP approach according to the developers' preference.

**Declarative programming** is a programming paradigm that declares what the program has to accomplish. It does not declare how the program should accomplish a certain computation throughout the control flow; it just declares **what it wants** without explaining how to get it. In contrast, **imperative programming** relies on a sequence of statements to modify a program's state, providing a detailed description for each step on **how to accomplish** a certain goal.

The majority of **OOP languages** were designed to follow imperative programming primarily. In comparison, **functional programming** tends to follow a more declarative programming approach since its logic does not explicitly describe the flow control to achieve a certain output. Instead, it expresses a computation as a pure function.

[Untitled](Functional%20programming%20vs%20OOP%20comparing%20paradigms%20625fc26a685b435ab972cdab522655e6/Untitled%20Database%2048f91014f687448e826be84db195d575.csv)

## Conclusion

Functional programming and OOP are two of the most popular and followed (even if just partly) programming paradigms. Despite having different approaches, both were designed to help developers create efficient and top-quality applications. These paradigms simply have different ways - and by "ways," we mean strategies, principles, and rules - to get there.

On the one hand, in OOP, **data is stored in objects** since the data and respective behaviors (meaning, what a program can do to or with data) should belong to a single location.

On the other hand, in functional programming, **data is passed and collected by functions**. However, it does not store data in objects because that could compromise clarity, considering that, for functional programming, data and behavior are different.

Both programming paradigms have their pros and cons, which is why many developers actually prefer to implement **hybrid solutions** according to each project's requirements and goals.

[Found this article useful? You might like these ones too!](https://web.imaginarycloud.com/services/ux-audit?utm_source=designblogposts&utm_medium=banner&utm_campaign=uxaudit&utm_content=uxauditpage)

[data:image/svg+xml;charset=utf-8,%3Csvg xmlns='http%3A//www.w3.org/2000/svg' xmlns%3Axlink='http%3A//www.w3.org/1999/xlink' viewBox='0 0 14 4'%3E%3Cfilter id='b' color-interpolation-filters='sRGB'%3E%3CfeGaussianBlur stdDeviation='.5'%3E%3C/feGaussianBlur%3E%3CfeComponentTransfer%3E%3CfeFuncA type='discrete' tableValues='1 1'%3E%3C/feFuncA%3E%3C/feComponentTransfer%3E%3C/filter%3E%3Cimage filter='url(%23b)' x='0' y='0' height='100%25' width='100%25' xlink%3Ahref='data%3Aimage/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA4AAAAECAIAAAAxsZngAAAApklEQVQImWWNPQ6CMABGeyzi6j2c3TRew8nRS2iMcWNwMIaYqBEBNYhRg7bSUrBCoPy0Nq6+vOF70wcIyyGOEImfrxAGFOHIh+SBSEAZr+QtSFyfqpFwCTBlln3YmpaxWtvOce+h3fW98WhI6WzhaL1pozvqDI2sFAAyMT/X+qlIef1DVLVUKlToS1Nr9ZvtgXvH4BLKiS3HlowzqY7+TfMyK8SHyy+LN5RQxLT1NwAAAABJRU5ErkJggg=='%3E%3C/image%3E%3C/svg%3E](data:image/svg+xml;charset=utf-8,%3Csvg xmlns='http%3A//www.w3.org/2000/svg' xmlns%3Axlink='http%3A//www.w3.org/1999/xlink' viewBox='0 0 14 4'%3E%3Cfilter id='b' color-interpolation-filters='sRGB'%3E%3CfeGaussianBlur stdDeviation='.5'%3E%3C/feGaussianBlur%3E%3CfeComponentTransfer%3E%3CfeFuncA type='discrete' tableValues='1 1'%3E%3C/feFuncA%3E%3C/feComponentTransfer%3E%3C/filter%3E%3Cimage filter='url(%23b)' x='0' y='0' height='100%25' width='100%25' xlink%3Ahref='data%3Aimage/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA4AAAAECAIAAAAxsZngAAAApklEQVQImWWNPQ6CMABGeyzi6j2c3TRew8nRS2iMcWNwMIaYqBEBNYhRg7bSUrBCoPy0Nq6+vOF70wcIyyGOEImfrxAGFOHIh+SBSEAZr+QtSFyfqpFwCTBlln3YmpaxWtvOce+h3fW98WhI6WzhaL1pozvqDI2sFAAyMT/X+qlIef1DVLVUKlToS1Nr9ZvtgXvH4BLKiS3HlowzqY7+TfMyK8SHyy+LN5RQxLT1NwAAAABJRU5ErkJggg=='%3E%3C/image%3E%3C/svg%3E)