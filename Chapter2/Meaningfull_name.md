# Chapter 2:  Meaningfull name 
We use lots of naming in our code like variable name, class name and names for functions, methods, files, arguments, states, packages, methods etc. Clean code requires clean and meeningfull names to fullfill our own quality guide.

There are some simple rules for good naming in code.
 ## Use Intention-Revealing Names
 Every name in your code have to have a name that describe its use and perpose. You also can leave a comment for description .
 The name should answer the big question about its own self-fulfillment and job. Attention: If you need to add a comment to explain it, the name is wrong
 int t; //temperature of the messurment -> int messurmentTemerature; -> int  actualTemperature 
 
 For example we have piece of code here.
 ```
 public List<int[]> getThem() {
  List<int[]> list1 = new ArrayList<int[]>();
  for (int[] x : theList)
   if (x[0] == 4)
    list1.add(x);
  return list1;
}
 ```
 
 Here   getThem ,List1 , the list ,x[0]  blah blah means nothing. You are the author and your writing is quite meaningless , smile.
 What is list1?
 why there is 4?
 what do you mean by them?
 There is no answer in those codes. So every name must reavile what do you intet to.
 Suppos this is a boardgame code with which we will get the flagged cells.
  ```
  public List<int[]> getFlaggedCells() {
    List<int[]> flaggedCells = new ArrayList<int[]>();
    for (int[] cell : gameBoard)
      if (cell[STATUS_VALUE] == FLAGGED)
        flaggedCells.add(cell);
    return flaggedCells;
}
  
  ```
Notice carefully the code doesnt get more complex or large , it is still the same but more meaningfull.

## Avoid Disinformation
   Dont place any name that far from intended meaning. Like hp, eco, aix those are poor variable name to give , those have special meaning programming. 
   Another thing is group , list or bunch. If you say numberlist it will like list variable . So could be groupOfNumber or bunchOf Number.
   A truly disinformative name is with lower case of l and uppercase of o. Like
     ```
     int a = l;
     if ( O == l )
       a = O1;
     else
       l = 01;
       ```
Too much congusing about 0 or O and 1 or l
   
## Make Meaningful Distinctions
When you want to declare some series variable dont do this like a1[] , a[]2.... Those are not disinformative those noninformative. Not a clue what are going to do with this.
Noise words are another meaningless distinction. Supppose you have Car class , then you have added CarDetails or CarInfo. Those are with same meaning with different class.
Another thing should must avoid that redudndant naming. Like NameString , CarObject , VarCar . Name will be always string for coding sake. And keep giving var in variable name is like giving name human to a human.
## Use Good Names
Good names means pronouciable and searchable names. That is easier to understand . Again you are a author and you have to make others to understand. That people can understand this name and its work . On the otherhand people can search easily your varibles by its use. 
It is good practice to use more short name in local variable that global variable.
 ## Always Avoid Encoding
 We tend to give name as short form. Like phonNum, AddInfo(Address info). It is too much confusing and another burden.  In modern IDE we dont need to do this . If you give complete name  ,it will enforce you write the full name. 
 Another problem in namig is prefix . like m_somethinf , f_something. We dont those. For example 
  ```
 public class Part {
private String m_dsc; // The textual description
void setName(String name) {
m_dsc = name;
}
}
_________________________________________________
public class Part {
String description;
void setDescription(String description) {
this.description = description;
}
}
 ```
 
 ## Some tips for Class and Method Names
 ### Class
 * Class name shoud be Noun or none phrase like employee , Customer. 
 * Avoid data, info ,item in those name.
 ### Function
 * Function name should be verb or verb phrase. Like getCustomers , addEmployee.
 * Always try to add some prefix like get,add , post etc.



Focus the implicity of code and names to create meaningfull code (Avoid Disinformation)
1. What kinds of things are in ....?
2. What is the significance of the zeroth subscript of .... (Or what are we doing with a methode and why we take this )
3. What is the significance of the value?
4. How would I use the output being returned?

<h2>Additionally to a good name we have use a consistent spelling.</h2>
Using inconsistent spellings is disinformation.
***camelCase***: iPhone, eBay  -> All Caps: UserLoginCount
***snakeCase***: hello_world   -> All Caps: USER_LOGIN_COUNT
***BIG(All Caps)***: AGGREGAT
***small( and short )*** :  coding
***_Front***: additionally sign to mention not touching this _dontTouchThis

files: camelCase (All Caps) 
class: camelCase (All Caps)
functions:  camelCase (small)
arguments: BIG
variables: small -> snakeCase 
global Variables: BIG -> snakeCase (All Caps) 

It helps to find the right name by imagination of building a house.
- Class as the result BuildProcessHouseFundament  (What for What? two part )
- function as the needed processes  createFundament , mixConcrete  (What is done with which goal?)
- variables as the needed materials water,sand ....  ( what do i use?)
- arguments to concationate the materials  WATER,SAND
- and the filename HouseFundamentBuilder  (the generalized form of the name)


thanksForReading!
ThanksForReading!
THANKS_FOR_READING_!
