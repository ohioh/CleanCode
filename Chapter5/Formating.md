# Chapter 5: Formating
We should always code in nicely formated. Foemating increases code it's beauty and more readability. The unformated code seems like this code is written by drunk sailor , who is going to turn down your project(ship).
So Formatting is very import part of clean code.

The perpose of formating is building a great communication between code and coder. And it will increase readability and style that will set precedent that will continue in next changes and modification.

## Verticle Formating
First thing we should consider that our file shoud not be very larg. Ideal code file should have less than hundrade line code.  Small files are usually easier to understand than large files are.

### Newspaper Metaphore
When we read newspaper we can see there lots story by para in a single page. There is no story that cover whole newspaper . And a story has different para of different kind of introduction and information. Our code should be like that. Like news paper first codes should be more important the other by algorithm and importancy . 

### Vertical Openness Between Concepts
In our code expression and clausses are represented by each line of code. And group of code represents a total story and thought.
 For example :
 package fitnesse.wikitext.widgets;
import java.util.regex.*;
public class BoldWidget extends ParentWidget {
public static final String REGEXP = "'''.+?'''";
private static final Pattern pattern = Pattern.compile("'''(.+?)'''",
Pattern.MULTILINE + Pattern.DOTALL
);
public BoldWidget(ParentWidget parent, String text) throws Exception {
super(parent);
Matcher match = pattern.matcher(text);
match.find();
addChildWidgets(match.group(1));
}
public String render() throws Exception {
StringBuffer html = new StringBuffer("<b>");
html.append(childHtml()).append("</b>");
return html.toString();
}
}

There are blank lines that separate the package
declaration, the import(s), and each of the functions. This extremely simple rule has a profound
effect on the visual layout of the code.
Verticle Density is very important between close associated codes. ith implise that how much associated the codes are.
Here are some example:
public class ReporterConfig {
/**
* The class name of the reporter listener
*/
private String m_className;
/**
* The properties of the reporter listener
*/
private List<Property> m_properties = new ArrayList<Property>();
public void addProperty(Property property) {
m_properties.add(property);
}
  
  In this code these useless comments break the close association between codes.
  Concepts that are closely related should be kept vertically close to each other.Variables should be declared as close to their usage as possible.
Initialization code should be closed.

## Horizontal Formatting

We should prefere as shortline as possible. We should not make scroll hoeizontally seeing our code. This is very Annoying.
Horaizontal openness and density is very important. We shold use whitw spaces between character very carefully. A nice example about that.

private void measureLine(String line) {
lineCount++;
int lineSize = line.length();
totalChars += lineSize;
lineWidthHistogram.addLine(lineSize, lineCount);
recordWidestLine(lineSize);
}
For formatting horizontal alignment is one of the most important thing. It is really inportant to make better readibility . 
To make good hirarchy we should focus on indent.It even helpes coder to code syntax  errorles
code.Programmers rely heavily on this indentation scheme. 
