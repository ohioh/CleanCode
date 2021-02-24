# Chapter 17:Smells And Huristics
In this chapter we have narrowed down some important term that we used in prevois chapter. It is really important to read top to bottom , that will amke you understand that how we noted the changes with different word. There is a cross-reference for each heuristic that shows you where it is referenced in the
rest of the text.

## Comments
* We should avoid lack of informative comments.
* Delet all the obsolete comments
* Redundant comment is more dangerous. Could make our code more unclean . So alwas avoid that.
* we should avoid comment out our code code.

## Functions

* Give informative and meaning full name.
* Avoid giving multiple arguments.
* The methods are never called shouldbe cleanned up.
* We should pass flags as arguments.
## Some Genaral Tips
### Duplication
We should always avoid duplicate code and comments in our programm. Duplicate stuff is more confusing.
This is one of the most important rules in this book, and you should take it very seriously.

### Multiple Languages in One Source File
The ideal is for a source file to contain one, and only one, language. Realistically, we
will probably have to use more than one. But we should take pains to minimize both the
number and extent of extra languages in our source files.

### Too Much Information

A well-defined interface does not offer very many functions
to depend upon, so coupling is low. A poorly defined interface provides lots of functions
that you must call, so coupling is high.

### Clutter

Variables that aren’t used, functions that are never
called, comments that add no information, and so forth. All these things are clutter and
should be removed. Keep your source files clean, well organized, and free of clutter.

### Function Names Should Say What They Do
Look at this code:
Date newDate = date.add(5);
Would you expect this to add five days to the date? Or is it weeks, or hours? Is the date
instance changed or does the function just return a new Date without changing the old one?
You can’t tell from the call what the function does.
If the function adds five days to the date and changes the date, then it should be called
addDaysTo or increaseByDays. If, on the other hand, the function returns a new date that is
five days later but does not change the date instance, it should be called daysLater or
daysSince.

### Prefer Polymorphism to If/Else or Switch/Case
We should use polymorphism when we want to call multiple functions by conditions. 
This might seem a strange suggestion given the topic of Chapter 6. After all, in that chapter I
make the point that switch statements are probably appropriate in the parts of the system
where adding new functions is more likely than adding new types.
### Structure over Convention
Enforce design decisions with structure over convention. Naming conventions are good,
but they are inferior to structures that force compliance.
### Don’t Inherit Constants
This is a hideous practice! The constants are hidden at the top of the inheritance hierarchy.
Ick! Don’t use inheritance as a way to cheat the scoping rules of the language. Use a static
import instead.
### Choose Descriptive Names
Don’t be too quick to choose a name. Make sure the name is descriptive. Remember that
meanings tend to drift as software evolves, so frequently reevaluate the appropriateness of
the names you choose.




