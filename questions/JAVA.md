# Interview Questions for Java

### Java

1. (OT) We have a stream and we call the following methods for it: `myStream.map(object -> object.toOtherType()).filter(object -> object.isEnabled()).collect(...)`. If we want to add a new mapping operation, does it matter if we place it before or after the filter operation?<br>
   A: No, it doesn't. `filter()` and `map()` are non-terminal operations and their order does not matter.
2. (OT) When do the intermediate (= non-terminal) operations in the previous stream example execute?<br>
   A: When we call a terminal operation, like `count()` or `collect()`. Intermediate operations are lazy.
3. (OT) What's the difference between final, finally and finalize keywords in Java?<br>
   A: `final` keyword is used for declaring constant variables or non-extendable classes.<br>
      `finally` keyword is part of the `try...catch...finally` statement. It executes a code block after either `try` or `catch` blocks.<br>
      `finalize` keyword represents a method from the Object class that can be overridden. It will be called when the object is being removed from memory by the garbage collector.<br>
4. (L) What types of exceptions do you know? Could you explain and give an example of each type?<br>
   A: Checked (must be caught), unchecked (it's recommended to catch it) and error (should not try to catch). Checked - IOException, Unchecked - NullPointerException, Error - StackOverflowError.
5. (L) What can an interface contain in Java 17?<br>
   A: Method declarations, constants, nested interfaces, static methods (Java 8), default methods (Java 8), private methods (Java 9), and private static methods (Java 9).
7. (L) Describe the collections hierarchy in Java. Could you give examples of concrete classes?<br>
   A: Iterable -> Collection -> List, Set, Queue; Map -> Map, SortedMap.
8. (L) Explain the difference between LinkedList and ArrayList. What are the complexities of get, add and remove methods? When would we use a LinkedList instead of ArrayList?<br>
   A: ArrayList uses a dynamically resizing array to store elements. When the array reaches its capacity, it is resized to accommodate more elements, usually doubling its size. `get(index)` - O(1), `add(element)` - O(1), if no resizing is required, and O(n) in the other case, `remove(index)` - O(n) because we need to fill the gap. We should use it when we usually add and remove elements from the end of the list, we need fast random access to the list or we know from the beginning the size of the list.<br>
      In LinkedList, each element represents a node that has a reference to the previous and next nodes. `get(index)` - O(n), `add(element)` - O(1), `remove(index)` - O(n). We should use it when we add elements at the beginning or the middle of the list and when we work with smaller lists for which we don't need fast random access.<br>
9. (L) Explain memory management in Java. When is the garbage collector run? Can we run it?<br>
   A: Memory allocations and deallocations happen automatically in Java. The garbage collector is managing deallocations. The garbage collector runs regularly. We can only tell the JVM to prioritize the garbage collector using `System.gc()`, but the garbage collector won't run instantly. It depends on how busy the JVM is.
10. (L) What are immutable objects? How do we implement an immutable class?<br>
   A: Immutable objects are those whose content cannot be changed. We implement an immutable class by not implementing setters, returning copies of the objects for getters and declaring the class final to ensure that the class won't be extended and made mutable.
11. (L) How can we override a method from a superclass?<br>
   A: We should keep the method name, the number of parameters and the types of the parameters and we should have the same return type or a subtype of the superclass' return type. Also, we should throw the same exceptions from the message.
12. (L) How do we run async code in Java? How do we start a thread and wait for it to run? What's the difference between calling the `start()` method for the thread and the `run()` method for the Runnable class?<br>
   A: We can use threads or ExecutorService, for example (or Future/CompletableFuture from Java 8). We can start a thread by creating a thread object `Thread thread = new Thread(new RunnableClass(), "threadName");` and then calling `thread.start();`. If we call start() from the thread, the code will execute asynchronously, but when we call run() from the runnable class, the code will be run by the same thread.
13. (L) How do we implement a thread-safe block of code?<br>
   A: We can use the `synchronized` keyword before a method name or a code block. Otherwise, we can use other mechanisms, like Lock, Semaphore or Barrier.
14. (L) What is a deadlock?<br>
   A: A deadlock happens when two or more threads try to use at least 2 resources and all of them wait for a lock to be fred.
15. (L) Could you give examples of synchronized collections in Java? How do we instantiate them?<br>
   A: BlockingQueue - we create a new Blocking queue object. We also have synchronized lists, sets, maps, and queues which can be created by calling a method from `Collections` class: `Collections.synchronizedList(new ArrayList<>());`.
16. (L) Is a `finally` block executed even if we have a `return` statement in try/catch, or an unexpected exception is being thrown?<br>
   A: Yes, the only case it won't execute would be when the program exits before the `finally` block.
17. (L) How can we make sure our resources will be closed after a `try...catch` block, without using `finally`?<br>
   A: We can use `try-with-resources`.

### Spring Core

1. (OT) What's the main difference between `@Bean` and `@Component`? When would we prefer to use one or another?<br>
   A: @Bean can be used for both classes and methods, but @Component can only be used for classes. We prefer to use @Bean when we use external classes and we cannot add the @Component annotation to them.
