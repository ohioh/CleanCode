# Chapter 6: Objects And Data Structures
After OOP concept , coding environmet changed dramatically . You dont have to depend and understand to use others code. Developer uses getter setter to their Class thus others can use their code easily.

# Data Abstraction
Data abstraction is great way to make yur code more understandable. Lets take a look on this code.
Code:1
public class Point {
public double x;
public double y;
}

Code:2
public interface Point {
double getX();
double getY();
void setCartesian(double x, double y);
double getR();
double getTheta();
void setPolar(double r, double theta);
}

In code 2 you cannot tell whether the
implementation is in rectangular or polar coordinates. But the interface is represenring data structure in style.But it represents more than just a data structure. The methods enforce an access
policy. You can read the individual coordinates independently, but you must set the coordinates
together as an atomic operation. Hiding implementation is about abstractions! Rather it exposes abstract interfaces
that allow its users to manipulate the essence of the data, without having to know its
implementation.

The difference between object and data is Objects hide
their data behind abstractions and expose functions that operate on that data. Data structure
expose their data and have no meaningful functions. Object can manipulate the data with its features. It is really important that we need to ensure the best use polymorphism and encapsulation.

## The Law of Demeter
There is a well-known heuristic called the Law of Demeter2 that says a module should not
know about the innards of the objects it manipulates. More precisely, the Law of Demeter says that a method f of a class C should only call
the methods of these:
• C
• An object created by f

### Train Wrecks

Take a look at this code
Options opts = ctxt.getOptions();
File scratchDir = opts.getScratchDir();
final String outputDir = scratchDir.getAbsolutePath();

This code lokes like a train wreck , because it look like a bunch of coupled train. We dont this chain actually. The calling
function knows how to navigate through
a lot of different objects.
cars. The use of accessor functions confuses the issue. If the code had been written as follows,
then we probably wouldn’t be asking about Demeter violations.

final String outputDir = ctxt.options.scratchDir.absolutePath;

## Hiding Structure

Choose the code below which is better

ctxt.getAbsolutePathOfScratchDirectoryOption();
or
ctx.getScratchDirectoryOption().getAbsolutePath()
The first option could lead to an explosion of methods in the ctxt object. The second presumes
that getScratchDirectoryOption() returns a data structure, not an object. 

## Conclusion
Object represtnt behavior and hide data. OOP is giving us the power of hiding our data with making objects. In big project it is very essential.
