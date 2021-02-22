# Chapter 13:Concurrency
Concurrence is a strstegy of decoupling. It is more popular with the name multythread.
Clean concurrent is more big picture . It connot be cover by a chapter. Cuncurrence code is very helpful and work really fine , but in deep level it is more complex than  we thought.

# Why Concurrency?
In modern software need more power of process  , because of lots calculation with multy loop. It improves the structure and throughput of a software. Without multythreading we caanot imagine a single software in this era. Specially in we application we need to handle lots of request in single time. With the help of concurrence code it is possible.
Consider, for example, the standard “Servlet” model of Web applications. These systems
run under the umbrella of a Web or EJB container that partially manages concurrency
for you. The servlets are executed asynchronously whenever Web requests come in.
The servlet programmer does not have to manage all the incoming requests. In principle,
each servlet execution lives in its own little world and is decoupled from all the other servlet
executions.

## Myths and Misconceptions
There are lots of misconception and myth about concurrence code. we are goinf to discuss about it.
• Concurrency always improves performance.
Concurrency can sometimes improve performance, but only when there is a lot of wait
time that can be shared between multiple threads or multiple processors. Neither situation
is trivial.
• Design does not change when writing concurrent programs.
In fact, the design of a concurrent algorithm can be remarkably different from the
design of a single-threaded system. The decoupling of what from when usually has a
huge effect on the structure of the system.
• Understanding concurrency issues is not important when working with a container
such as a Web or EJB container.
In fact, you’d better know just what your container is doing and how to guard against
the issues of concurrent update and deadlock described later in this chapter.
Here are a few more balanced sound bites regarding writing concurrent software:
• Concurrency incurs some overhead, both in performance as well as writing additional
code.
• Correct concurrency is complex, even for simple problems.

• Concurrency bugs aren’t usually repeatable, so they are often ignored as one-offs2
instead of the true defects they are.
• Concurrency often requires a fundamental change in design strategy.

# Challenges

The main challenge in concurrence code is the threads runs randomly. Because there are lots paths to run the thrads. There are 12870 execution paths of execution of threads . When which thread will execute , determinig that is very hard. 

public class X {
private int lastIdUsed;
public int getNextId() {
return ++lastIdUsed;
}
}
Let’s say we create an instance of X, set the lastIdUsed field to 42, and then share the
instance between two threads. Now suppose that both of those threads call the method
getNextId(); there are three possible outcomes:
• Thread one gets the value 43, thread two gets the value 44, lastIdUsed is 44.
• Thread one gets the value 44, thread two gets the value 43, lastIdUsed is 44.
• Thread one gets the value 43, thread two gets the value 43, lastIdUsed is 43.
Of course most of those paths generate valid results. The
problem is that some of them don’t.

## Concurrency Defense Principles
We will talk about how to defense the concurrence code problem.
### Single Responsibility Principle
• Concurrency-related code has its own life cycle of development, change, and tuning.
• Concurrency-related code has its own challenges, which are different from and often
more difficult than nonconcurrency-related code.
• The number of ways in which miswritten concurrency-based code can fail makes it
challenging enough without the added burden of surrounding application code.
Recommendation: Keep your concurrency-related code separate from other code.6

### Corollary: Limit the Scope of Data
• You will forget to protect one or more of those places—effectively breaking all code
that modifies that shared data.
• There will be duplication of effort required to make sure everything is effectively
guarded (violation of DRY7).
• It will be difficult to determine the source of failures, which are already hard enough
to find.
Recommendation: Take data encapsulation to heart; severely limit the access of any
data that may be shared.

### Corollary: Use Copies of Data
If there is an easy way to avoid sharing objects, the resulting code will be far less likely
to cause problems. You might be concerned about the cost of all the extra object creation. It is
worth experimenting to find out if this is in fact a problem. However, if using copies of
objects allows the code to avoid synchronizing, the savings in avoiding the intrinsic lock will
likely make up for the additional creation and garbage collection overhead.
### Corollary: Threads Should Be as Independent as Possible
For example, classes that subclass from HttpServlet receive all of their information
as parameters passed in to the doGet and doPost methods. This makes each Servlet act
as if it has its own machine. So long as the code in the Servlet uses only local variables,
there is no chance that the Servlet will cause synchronization problems. Of course,
most applications using Servlets eventually run into shared resources such as database
connections.
Recommendation: Attempt to partition data into independent subsets than can be
operated on by independent threads, possibly in different processors.

Some other technique

* Know Your Execution Models
* Know Your Library
* Thread-Safe Collections
* Keep Synchronized Sections Small
* Beware Dependencies Between Synchronized Methods
* You have to write correct shutdown code of thread.

## Testing Threaded code
That is a whole lot to take into consideration. Here are a few more fine-grained
recommendations:
• Treat spurious failures as candidate threading issues.
• Get your nonthreaded code working first.
• Make your threaded code pluggable.
• Make your threaded code tunable.
• Run with more threads than processors.
• Run on different platforms.
• Instrument your code to try and force failures.



