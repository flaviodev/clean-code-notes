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

###Class Organization

#### A class should begin with a list of variables.
* Public static constants, if any, should come first. 
* Then private static variables, followed by private instance variables. 
* There is seldom a good reason to have a public variable.
* Public functions should follow the list of variables. 
* We like to put the private utilities called by a public function right after the public function itself. 
* This follows the stepdown rule and helps the program read like a newspaper article.
