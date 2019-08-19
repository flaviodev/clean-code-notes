# Clean Code Notes

Some notes about the book Clean Code - Bob Martin

## Meaningful Names

* Apply meaningful distinctions
* Use pronounceable/researchable names and avoid encodings
* Use solution/problem domain names

## Functions 

* Main rule: Functions should do one thing. They should do it well. They should do it only.
* Use descriptive names
* Choose the verb/noum pair to name of functions
* Preference to use no-args functions or funcitons with one or two arguments (three only if really necessary)
* Write the name of the arguments in the function in the same declaration order
```java
public void sendMessageToTopic(String message, String topic) { ... }
```
* Prefer exceptions to returning error codes

## Comments 

* Comments are always failures 
* Avoid bad comments, TODO comments and redundant comments
```java
 // TODO: Remove this comment
```
* Few practices are as odious as commenting-out code

## Formatting 

* First of all, let's be clear
* Code formatting is about communication
* Vertical formatting, the newspaper mataphor
* The "thoughts" are separated from each other with blank lines
* Vertical Density: Implies close association. If one function calls another, they should be vertically close

## Objects and Data Structures

* Procedural code makes it hard to add new data structures because all the functions must change. OO code makes it hard to add new functions because all the classes must change.
* Mature programmers know that the idea that everything is an object is a myth. Sometimes you really do want simple data structures with procedures operating  on them.
* Data transfer Objects
* Objects expose behavior and hid data
* Data structures expose data and have no significant behavior 

## Error Handling

* Error handling is important, but if it obscures logic, it's wrong.
* Use Exceptions rather than return codes
* Use unchecked exceptions
* Provide context with exceptions
* In java, you can get a stack trace from any exception; however, a stack trace cant't tell you the intent of the operation that falied
* Create informative error messages and pass them along with your exceptions. Mention the operation the failed and the type of failure
* Define exceptions classes in terms of caller's needs
* when we define exception classes in an application, our most important concern should be how they are caught 
* In fact, wrapping third-party APIs is a best practice
* Define the normal flow
* Don't return null
* when we return null, we are essentially creating work for ourselves and foisting problems upon our callers
* Returning null from methods is bad, but passing null into methods is worse
* Clean code is readable, but it must also be robust.

## Boundaries

* Learning the third-party code is hard. Integrating the third-party code is hard too. Doing both at the same time is doubly hard.
* We could write some tests to explore our understanding of the third-party code (learning tests)
* Learning Tests Are Better Than Free
* Not only are learning tests free, they have a positive return on investment.
* We run the learning tests to see whether there are behavioral differences.
* Clean Boundaries      

## Unit Tests

* The Three Laws of TDD
 - First Law You may not write production code until you have written a failing unit test.
 - Second Law You may not write more of a unit test than is sufficient to fail, and not compiling is failing.
 - Third Law You may not write more production code than is sufficient to pass the currently failing test.
* Keeping Tests Clean
 - So long as the test code worked, and so long as it covered the pro-
duction code, it was good enough.
 - Test code is just as important as production code.
* Tests Enable the -ilities
 - If you don’t keep your tests clean, you will lose them. Tests enable all the -ilities, because tests enable change.
* Clean test:
 - What makes a clean test? Three things. Readability, readability, and readability. The same thing that makes all code readable: clarity, simplicity,
and density of expression
 - Domain-Specific Testing Language
 - F.I.R.S.T: Clean tests follow five other rules that form the above acronym:
Fast, Independent, Repeatable, Self-Validating, Timely
 - Tests preserve and enhance the flexibility, maintainability, and reusability of the production code
 - Invent testing APIs that act as domain-specific language that helps you write the tests. 
* One Assert per Test

## Classes

### Class Organization

#### A class should begin with a list of variables.
* Public static constants, if any, should come first. 
* Then private static variables, followed by private instance variables. 
* There is seldom a good reason to have a public variable.
* Public functions should follow the list of variables. 
* We like to put the private utilities called by a public function right after the public function itself. 
#### Encapsulation
* If a test in the same package needs to call a function or access a variable, we’ll make it protected or package scope. However, we’ll first look for a way to maintain privacy. Loosening encapsulation is always a last resort.
#### Classes should be small
* With functions we measured size by counting physical lines. With classes we use a different measure. We count responsibilities. 
* The more ambiguous the class name, the more likely it has too many responsibilities. For example, class names including weasel words like Processor or Manager or Super often hint at unfortunate aggregation of responsibilities.
* We should also be able to write a brief description of the class in about 25 words, without using the words “if,” “and,” “or,” or “but.”
* Single Responsibility Principle: Classes should have one responsibility — one reason to change.
* Yet oddly, Single Resposability Pinciple is often the most abused class design principle.
* Cohesion: When cohesion is high, it means that the methods and variables of the class are co-dependent and hang together as a logical whole.
* Breaking large functions and breanking large classes: So breaking a large function into many smaller functions often gives us the opportunity to split several smaller classes out as well. This gives our program a much better organization and a more transparent structure.
* Open-Closed Principle: Classes should be open for extension but closed for modification.
* Isolating from change: By minimizing coupling in this way, our classes adhere to another class design principle known as the Dependency Inversion Principle (DIP)

## Systems

### Separation of Concerns
* Clean code helps us achieve this (separation of concerns) at the lower levels of abstractions;
* Software systems should separate the startup process, when the application objects are constructed and the dependencies are "wired" together, from  the runtime logic that takes over after startup;
* The separation of concerns is one of the oldest and most important design techniques in our craft;
* Lazy initialization/evaluation has a hard-coded dependency, and testing it can be a problem;
* Hence, the global setup strategy (if there is one) is scattered across the application, with little modularity and often significant duplication;

### Separation of Main
* One way to separate construction from use is simply to move all aspects of construction to main;
* The main function builds the objects necessary for the system, then passes them to the application, which simply uses them;
* Use of Factories
* Dependency Injection and Inversion of Control
* Inversion of Control moves secondary responsibilities from an object to other objects that are dedicated to the purpose;
* Instead, it should pass this responsibility to another "authoritative" mechanism, thereby inverting control;

### Scaling Up
* Software systems are unique compared to physical systems. Their architectures can grow incrementally, IF we maintain the proper separation of concerns;
* Cross-Cutting Concerns
* Proxies 
* Pure Java AOP Frameworks 

### Cross-cutting concerns
* Cross-cutting concerns: persistence, transactions, security, caching, failover
* An Optimal system architecture consists of modularized domains of concern, each fo which is implemented with Plain Old Java (or other) Objects. The different domains are integrated, together with minimally invasive Aspects or Aspect-like tools. This architecture can be test-driven, just like the code.
* The agility provided by a POJO system with modularized concerns allows ws to make optimal, just-in-time decisions, based on the most recent knowledge. The complexity of these decisions is also reduced.
* Standards make it easier to reuse ideas and components, recruit people with relevant experience, encapsulate good ideas, and wire components together. However, the process of creating standards can sometimes take too long for industry to wait, and some standards lose touch with the real needs of the adopters they are intended to serve.
* A good DSL minimizes the "communication gap" between a domain concept and the code that implements it, just as agile practices optimize the communications within a team and with the project's stakeholders. 
* Domain-Specific Languages allow levels of abstraction and all domains in the application to be expressed as POJOs, from high-level policy to low-level details.

## AspectJ
* The pure Java approaches provided by Spring AOP and JBoss AOP are sufficient for 80–90 percent of the cases where aspects are most useful.

## Emergence

* Many of us feel that Kent Beck's four rules of Simple Design are of significant help in creating well-designed software:
- Runs all the tests
- Contains no duplication
- Express the intent of the programmer
- Minimizes the number of classes and methods

### Run All the Tests
* First and foremost, a design must produce a system that acts as intended.
* A system that is comprehensively tested and passes all of its tests all of the time is a testable system.
* Arguably, a system that cannot be verified should never be deployed.
* For each few lines of code we add, we pause and reflect on the new design.
* The fact that we have these tests eliminates the fear that cleaning up the code will break it!



