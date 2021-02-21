# Chapter 3: Functions
For writting clean code it is very important to write good and clean function . Because we need our codes well organised thats why we need functions very much.

## Small
Function should be small as small as possible. We can say this we have three rule for making a function "make it small , make it smaller , make smallest". 
Why? Because is more understandable , more easy to modify. 
Now how much small it should be. Every function in this program
was just two, or three, or four lines long. Each was transparently obvious. Each told
a story. And each led you to the next in a compelling order. That’s how short your functions
should be!
We can do this by blocking and intending . Every if, else, while should have one code block in one function. And the indent level of a function should not be greater than one or two. 

## Do one thing
FUNCTIONS SHOULD DO ONE THING. THEY SHOULD DO IT WELL.
THEY SHOULD DO IT ONLY.

Yes man thats right. Every single job should be different function. So devide the function into sections , make the sections into functions. Dont mixed up the abstraction of a function with other function. This will make sure that your function has ***one*** jobe to do.  doJobWell()

## Switch Statements
Unfortunately
we can’t always avoid switch statements, but we can make sure that each switch
statement is buried in a low-level class and is never repeated. We do this, of course, with
polymorphism.

For Example:
```
public Money calculatePay(Employee e)
throws InvalidEmployeeType {
switch (e.type) {
case COMMISSIONED:
return calculateCommissionedPay(e);
case HOURLY:
return calculateHourlyPay(e);
case SALARIED:
return calculateSalariedPay(e);
default:
throw new InvalidEmployeeType(e.type);
}
```
We can turn the code into this
```
public abstract class Employee {
public abstract boolean isPayday();
public abstract Money calculatePay();
public abstract void deliverPay(Money pay);
}
-----------------
public interface EmployeeFactory {
public Employee makeEmployee(EmployeeRecord r) throws InvalidEmployeeType;
}
-----------------
public class EmployeeFactoryImpl implements EmployeeFactory {
public Employee makeEmployee(EmployeeRecord r) throws InvalidEmployeeType {
switch (r.type) {
case COMMISSIONED:
return new CommissionedEmployee(r) ;
case HOURLY:
return new HourlyEmployee(r);
case SALARIED:
return new SalariedEmploye(r);
default:
throw new InvalidEmployeeType(r.type);
}
}
}
```
This will speed up the encasulation of our codes. 

***Reading Code from Top to Bottom: The Stepdown Rule***
If we solve or focus to solve one task per line we have to make sure that the answer ( the next abstraction layer is below )
make that TO do That TO do this end so one
</br>
> “You know you are working on clean code
> when each routine turns out to be pretty much what you expected.”

Oncle Bob gave an awesome quote to this:
> ***To*** include the setups and teardowns, we ***include*** setups, ***then*** we ***include*** the test page content, and then we ***include*** the teardowns.
> ***To include*** the setups, we ***include*** the suite setup if this is a suite, then we include the regular setup.
> ***To*** include the suite setup, we search the parent hierarchy for the “SuiteSetUp” page
> and add an include statement with the path of that page.To search the parent. . .


## Use Descriptive Names

Choosing good and meaningfull names for small functions that do one thing.The smaller and more focused a function is, the easier it is to choose a descriptive
name. Don’t be afraid to make a name long. A long descriptive name is better than a short
enigmatic name.

## Function Arguments
We should less arguments as possible . Zero argument is ideal for function.One input argument is the next best thing to no arguments. Because arguments take a lot of conceptual power. It makes more complex to test the programms. 
How we can reduce our arguments. We can pass those arguments as objrct.Reducing the number of arguments by creating objects out of them may seem like
cheating, but it’s not.
Example:
```
Circle makeCircle(double x, double y, double radius);
Circle makeCircle(Point center, double radius);
```
## Command Query Separation
Functions should either do something or answer something, but not both. For Example

public boolean set(String attribute, String value);

this function is doing something. If we use this function like this
if (set("username", "unclebob"))...

That would be very confusing. 
## Prefer Exceptions to Returning Error Codes
When you return an error code, you create the problem that the caller must deal with
the error immediately.On the other hand, if you use exceptions instead of returned error codes, then the error
processing code can be separated from the happy path code and can be simplified.
For example :
```
if (deletePage(page) == E_OK) {
if (registry.deleteReference(page.name) == E_OK) {
if (configKeys.deleteKey(page.name.makeKey()) == E_OK){
logger.log("page deleted");
} else {
logger.log("configKey not deleted");
}
} else {
logger.log("deleteReference from registry failed");
}
} else {
logger.log("delete failed");
return
```
that can be convert into 
```
try {
deletePage(page);
registry.deleteReference(page.name);
configKeys.deleteKey(page.name.makeKey());
}
catch (Exception e) {
logger.log(e.getMessage());
}
```
<h1>How to clearify:</h1>

few simple method extractions, some renaming, and a little restructuring

Do One thing ... for class and function ofcourse! Add this idea to each line... one line has to do one thing .... this to that -> nextline how...  

Sections should not be devided. sections such as declarations, initializations, and sieve -> Comment this process

Each function should have only one level of abstraction. Imagine that you have a lot of clear functions which are only connecting on level of abstarction. Then it is very easy to cluster them in the smallescommonality and put them in a library again. if you cross more abstractionlevels ... you will have a lot of functions which are not compareable. Maybe the way is the same...but the goal of each is different... and you will not be able to simlify them... split to one-to-one layer and avoid double code
w
