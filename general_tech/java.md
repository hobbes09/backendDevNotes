
===============================================================================
# Topic 1 : Java compilation and Execution process

Ref : https://www.youtube.com/watch?v=F9_m5ch9D_A

Notes :
1) Compile time :
  - Java file is compiled to a byte code
  - This byte code file is the class file

2) Run time
 - ClassLoader function loads the class function into memory, by passing name to JVM. All referenced files are also loaded.
 - ByteCodeVerifier checks the byte code
 - Interpreter(JIT compiler) reads the bytecode strings, converts to machine code, and executes them
 - Runtime environment executes it in hardware


 ===============================================================================

# Topic 2 : Memory Management

- Heap Vs Stack : https://stackify.com/java-heap-vs-stack/
- Concurrent Mark and Sweep Garbage Collection : Refer to Notes
- G1 Garbage collector : https://medium.com/@sauravomar01/g1-garbage-collector-in-java-8535c0a1f91a
https://www.youtube.com/watch?v=X8w3uqN-X98
- Overall : https://www.baeldung.com/jvm-garbage-collectors


===============================================================================

# Topic 3 : G1 Garbage collection

G1 is introduced in Java7. Oracle 9 Hotspot JVM comes with default G1 Garbage collection.

One of the good property of this is you can configure this for maximum pause time using flag:

-XX:MaxGCPauseMillis=n.

Lots of real-world studies say most of the objects (90%) garbage collected in a young generation or in first garbage collection or minor GC (also it depends upon applications). Who survived a couple of GCs(major GC), present in old memory (old objects) they will remain survive more than 95% times.

#### Explaination on G1 Garbage Collector:

1. It does most of the work concurrently.
2. It uses non-continuous which enables G1 to deal with the very large heap efficiently.
3. Instead of dividing heaps into 3 spaces (old) like other Garbage Collectors like CMS (concurrent mark and sweep, Parallel etc), it divides heap memory in small chunks. These regions are fix-sized (about 2Mb by default). like below

    U: Unassigned, O: Old, S: survivor, E: eden

    |U|S|U|S|E|O|U|U|U|E|E|O|S|S|S|U|O|E|O


4. Splitting into small regions helps G1 concurrently run and finish it off very quickly.

5. While running GC on Eden space all the survived objects get copied to unassigned space. The unassigned space becomes survivor space.

6. If all the objects in Eden space are garbage then it can be declared as Unassigned.

7. G1 is not run on whole heap memory at once like others Garbage Collectors, instead of this it always selects the regions which are full or almost full to minimizes the amount of work to free heap space.

8. G1 only stops the application at the beginning of the GC for boot strapping , this phase is called as Initial Mark.

9. While Application is executing it follow all the references and mark live objects, this phase called as Concurrent Mark.

10. When above phase(Concurrent Mark) is done then application again stops. for final cleanup is made, this phase called as Final Mark.

11. To move objects and reclaim heap memory, this phase called as Evacuation phase this phase is fast, called as Evacuation Phase.

12. This is not good for small heaps then it that case might be full GC is performed and might slow down overall executions. In that case increase the heap size or other Garbage collectors can be used.



===============================================================================

# Topic 4 : Maven
- https://stackoverflow.com/questions/13335351/what-does-maven-do-in-theory-and-in-practice-when-is-it-worth-to-use-it



===============================================================================

# Go vs Java

https://rcoh.me/posts/why-you-can-have-a-million-go-routines-but-only-1000-java-threads/


===============================================================================
# Thread-Safety

https://www.baeldung.com/java-thread-safety

==============================================================================

# Flow API

https://www.baeldung.com/java-9-reactive-streams
