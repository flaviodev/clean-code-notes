# Clean Code Notes

Some notes about the book Clean Code - Bob Martin

## Functions 

* Main rule: A function must do only one thing 

* Preference to use no-args functions or funcitons with one or two arguments (three only if really necessary)

* Write the name of the arguments in the function in the same declaration order

´´´
public void sendMessageToTopic(String message, String topic) { ... }
```
