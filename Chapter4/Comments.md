# Chapter 4: Comments

1. Comments
2. Structure
3. Tags:
          -Method-Declaration **[cpp-Documentationtags](https://docs.microsoft.com/de-de/cpp/build/reference/delimiters-for-visual-cpp-documentation-tags?view=msvc-160)**


Comments are really usefull when you want know others about your code. But only that time you need Comments to make understand others about code when you are failed to write understandable code. it is only used for compensation of your failuer. harsh but true.
 So when you find yourself in a position where you need to write a comment, think it
through and see whether there isn’t some way to turn the tables and express yourself in
code. We would rather that energy go toward making the code so clear and expressive that it
does not need the comments in the first place. comment does not make up for bad code. So Try to explin yourself in code.

## Good Comments
Always use informative comments that will explain the unexplained fact. For example :

```
// format matched kk:mm:ss EEE, MMM dd, yyyy
Pattern timeMatcher = Pattern.compile(
"\\d*:\\d*:\\d* \\w*, \\w* \\d*, \\d*");
```

In this case the comment lets us know that the regular expression is intended to match a
time and date that were formatted with the SimpleDateFormat.format function using the
specified format string.

Sometime we can use comments for explaining our intention rather than the implementation. Such as

```
String text = "'''bold text'''";

ParentWidget parent = new BoldWidget(new MockWidgetRoot(), "'''bold text'''");
AtomicBoolean failFlag = new AtomicBoolean();
failFlag.set(false);

//This is our best attempt to get a race condition
//by creating large number of threads.
for (int i = 0; i < 25000; i++) {
   WidgetBuilderThread widgetBuilderThread =
   new WidgetBuilderThread(widgetBuilder, text, parent, failFlag);
   Thread thread = new Thread(widgetBuilderThread);
   thread.start();
}

assertEquals(false, failFlag.get());
```

Sometime we can use comments as warning , we can let reader know about the the consequences of this programm. 

We can also can use comments as todo list. That this has to be done in future or this code needs to be improved. 

```
//TODO-MdM these are not needed
// We expect this to go away when we do the checkout model
protected VersionInfo makeVersion() throws Exception {
  return null;
}
```
Whatever else a TODO might be, it is not an excuse to leave bad code in
the system. Still it might be helpful in some unavoidable case.

A comment may be used to amplify the importance of something that may otherwise seem
inconsequential.
```
String listItemContent = match.group(3).trim();
// the trim is real important. It removes the starting
// spaces that could cause the item to be recognized
// as another list.
new ListItemWidget(this, listItemContent, this.level + 1);
return buildList(text.substring(match.end()));
```

## Bad Comments

Most of the comments fall into the mumbling inappropriate comment. you should spent some time to write a usefull comment . But not useful for you usefull for reader. If it is not even you cannt understand your comment after few days. 

```
public void loadProperties(){
  try {
          String propertiesPath = propertiesLocation + "/" + PROPERTIES_FILE;
          FileInputStream propertiesStream = new FileInputStream(propertiesPath);
          loadedProperties.load(propertiesStream);
      }
  catch(IOException e){
          // No properties files means all defaults are loaded
     }
}
```

Clearly it meant something to the
author, but the meaning does not come through all that well.
We should avoid the redundant comment to keep our code neet and clean. 


## Some More Tips About comments
* Dont use too much big and informative Comment
* Dont use noisy comment. Such as
```
/**
* Default constructor.
*/
protected AnnualDateRule() {
}
No, really? Or how about this:
/** The day of the month. */
```
* Don’t Use a Comment When You Can Use a Function or a Variable
* Few practices are as odious as commenting-out code. Don’t do this.

## Example:
The Adafruit libraries are very well organised and commented:
I love supporting the **[adafruit ccs811](https://github.com/adafruit/Adafruit_CCS811/blob/master/Adafruit_CCS811.cpp)**.
This is the *[adafruit ccs811](https://github.com/adafruit/Adafruit_CCS811/blob/master/Adafruit_CCS811.cpp)*.

```
///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
/*
 *  CS-11 Asn 2: Calculates the total of 6 checks
 *  Mitschrift in der Vorlesung "Programmieren"
 *  programmieren.cpp
 *  Purpose: Calculates the total of 6 checks
 *  
 *  @file checks.cpp
 *  @author Tjark Ziehm
 *  @version 0.9 15.Oktober 2015 
 *
 * Developed for the LSST Data Management System.
 * This product includes software developed by the LSST Project
 * (https://www.lsst.org).
 * See the COPYRIGHT file at the top-level directory of this distribution
 * for details of code ownership.
 *
 * This program is free software: you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation, either version 3 of the License, or
 * (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program.  If not, see <https://www.gnu.org/licenses/>.
 */
///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

// Test-Wert für printf-Test
int zahl = 1;


///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

// Formatspezifizierer %
// %c : char buchstabe = 'a'
// &f : float floatZahl = 1.23 ---> cout>> 1.230000 ( 6 stellig nach dem Komma) ->
// mit %.1f
// bool ?


///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

/**************************************************************************/
/*!    
    @brief  seperation logical blocks
    @param  line of single deviding commenting symbol like /,# or /* and */    
*/
/**************************************************************************/


///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

/**************************************************************************/
/*!    
    @brief  Print out variable w/ print 
    @param  zahl as an integer
    @returns True if device is set up, false on any failure
*/
/**************************************************************************/
printf("Zahl = %d", zahl);


///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

/// <summary>Sorts the list to by the given column</summary>
/// test
/// test
void test()
{
}


///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

/**
 * test 
 * @brief  Print out variable w/ print 
 */
void test2()
{
}


///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////



```




