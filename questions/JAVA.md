# Interview Questions for Java

### Java

1. We have a stream and we call the following methods for it: `myStream.map(object -> object.toOtherType()).filter(object -> object.isEnabled()).collect(...)`. If we want to add a new mapping operation, does it matter if we place it before or after the filter operation?
   A: No, it doesn't. `filter()` and `map()` are non-terminal operations and their order does not matter.
2. When do the intermediate (= non-terminal) operations of the previous stream executes?
   A: When we call a terminal operation, like `count()` or `collect()`. Intermediate operations are lazy.
3. What's the difference between final, finally and finalize keywords in Java?
   A: `final` keyword is used for declaring constant variables or non-extendable classes.
      `finally` keyword is part of the `try...catch...finally` statement. It executes a block of code after the end of either `try` or `catch` blocks.
      `finalize` keyword represents a method from the Object class that can be overridden. It will be called when the object is being removed from memory by the garbage collector.

### Spring Core

1. What's the main difference between @Bean and @Component. When would we prefer to use one or another?
   A: @Bean can be used for both classes and methods, but @Component can only be used for classes. We would prefer to use @Bean when we use external classes and we cannot add the @Component annotation to them.
