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
