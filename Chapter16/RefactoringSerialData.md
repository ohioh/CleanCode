# Chapter 16:Refactoring serial Data
Ther is a class called SerialDate. Which belongs in org.jfree.date package in JCommon Library. We are going to refactor this class in chapter. We will run some unitest in tbis code and will see how is the performance and will change the inner code to make it more clean. Actually we are going to make some proffesional judgement on this code. That will be honest review with technical explaination.
The name of the author of this class is David Gilbert. He is a very good experinced programmer . 

## What is SerialDate actually
SerialDate is a class which represent the date functionality in java. Though there are more other libraries about date times like java.util.Date and
java.util.Calendar, and othrs. But in this class the author reduce some pain of programmer. Which makes it more helpfull. 

## First, Make It Work
To refactor and recover this class first we have to test it . With testing this class we cannot understand it actual behaviour.
For testing it has its own test class SerianDateTest. After testing some staemnets fortunately we found some bug. We are going to fix those . 
On this code There was statemnet , which was executable with test function because the if condition was always false. Other code was not passed with unitest. 
So what should we do first for start refactoring a code , start with testing , test every statment with power ful unitest tools.

## Then Make It Right
After all the testing then we are goimg to clean the programm. Cleaning the progrmm meanes we have to make every class , function , variable in order through our cleaning rules. In this class there was a class called Daydate. That class inherits from Comparable,
Serializable , MonthConstants. But Month constant should not be inherited  . Inherit a constant is backdated coding system. insted of that we make a enum
```
public static enum Month {
JANUARY(1),
FEBRUARY(2),
MARCH(3),
APRIL(4),
MAY(5),
JUNE(6),
JULY(7),
AUGUST(8),
SEPTEMBER(9),
OCTOBER(10),
NOVEMBER(11),
DECEMBER(12);
```
This is more cleaner than that. ther was Static final variable called EARLIEST_DATE_ORDINAL. The naming is good but the final value was unexplained clealy. We fixed this with more comment. 

On other abstract class called daydate ther was unusual implementation of that . Making it more cleaner we Declared a factory class about that . Factory class is more way modern and helpful. 

Ther are lots of function who has perameters as flag. That is very idea .when that flag simply selects the format of the output. We have renamed that functions and moved theme into month enum.
The next function, leapYearCount  doesn’t really belong in DayDate.
Nobody calls it except for two methods in SpreadsheetDate. So I pushed it down . So I pushed it down.
 
 
Test coverage was
increased, some bugs were fixed, the code was clarified and shrunk. The next person to
look at this code will hopefully find it easier to deal with than we did. That person will also
probably be able to clean it up a bit more than we did.So like this with our clean concept we can refactor a code . This process is more efficient for cleaning up any draft code. We dont create anynew sytem for being draft.

## Few Last Word

Refactoring a code is very important thing of a project . Unclean code could happen in any sytem. We need to refactore them often. So For refactoring we need take few steps

### Make it work
Test the whole code and fix the testing errors

### Make it Right

Clean the whole code we cleaning methods.


