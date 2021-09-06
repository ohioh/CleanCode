# Chapter 10: Classes
Class is very important part of whole programming part along with functions and statement. So clean class is also important to make our code clean and shine.

## Class Organization
For organising class we need to follow some standard . We should start classes with public , private , static variables.
The function shold be the follow.  Private utilities should be placed after public function . We’ll first look for a way to maintain privacy.
Loosening encapsulation is always a last resort. Because Encapsulation is very important for a clean code.
Specially getter and setter of varibles will play vital roles.

## Classes Should Be Small
As with functions, smaller is the primary rule when it comes to designing classes. As with functions, our immediate question is always “How small?”
We can look on this code:
```
public class SuperDashboard extends JFrame implements MetaDataUser
public String getCustomizerLanguagePath()
public void setSystemConfigPath(String systemConfigPath)
public String getSystemConfigDocument()
public void setSystemConfigDocument(String systemConfigDocument)
public boolean getGuruState()
public boolean getNoviceState()
public boolean getOpenSourceState()
public void showObject(MetaObject object)
public void showProgress(String s)
public boolean isMetadataDirty()
public void setIsMetadataDirty(boolean isMetadataDirty)
public Component getLastFocusedComponent()
public void setLastFocused(Component lastFocused)
public void setMouseSelectState(boolean isMouseSelected)
public boolean isMouseSelected()
public LanguageManager getLanguageManager()
public Project getProject()
public Project getFirstProject()
public Project getLastProject()
public String getNewProjectName()
public void setComponentSizes(Dimension dim)
public String getCurrentDir()
public void setCurrentDir(String newDir)
public void updateStatus(int dotPos, int markPos)
public Class[] getDataBaseClasses()
public MetadataFeeder getMetadataFeeder()
public void addProject(Project project)
public boolean setCurrentProject(Project project)
public boolean removeProject(Project project)
public MetaProjectHeader getProgramMetadata()
public void resetDashboard()
public Project loadProject(String fileName, String projectName)
public void setCanSaveMetadata(boolean canSave)
public MetaObject getSelectedObject()
public void deselectObjects()
public void setProject(Project project)
public void editorAction(String actionName, ActionEvent event)
public void setMode(int mode)
public FileManager getFileManager()
public void setFileManager(FileManager fileManager)
public ConfigManager getConfigManager()
public void setConfigManager(ConfigManager configManager)
public ClassLoader getClassLoader()
public void setClassLoader(ClassLoader classLoader)
public Properties getProps()
public String getUserHome()
public String getBaseDir()
public int getMajorVersionNumber()
public int getMinorVersionNumber()
public int getBuildNumber()
public MetaObject pasting(
MetaObject target, MetaObject pasted, MetaProject project)
public void processMenuItems(MetaObject metaObject)
public void processMenuSeparators(MetaObject metaObject)
public void processTabPages(MetaObject metaObject)
public void processPlacement(MetaObject object)
public void processCreateLayout(MetaObject object)
public void updateDisplayLayer(MetaObject object, int layerIndex)
public void propertyEditedRepaint(MetaObject object)
public void processDeleteObject(MetaObject object)
public boolean getAttachedToDesigner()
public void processProjectChangedState(boolean hasProjectChanged)
public void processObjectNameChanged(MetaObject object)
public void runProject()
public void setAçowDragging(boolean allowDragging)
public boolean allowDragging()
public boolean isCustomizing()
public void setTitle(String title)
public IdeMenuBar getIdeMenuBar()
public void showHelper(MetaObject metaObject, String propertyName)
// ... many non-public methods follow ...
}
```
Most developers would agree that it’s a bit too super in size. Some developers might refer
to SuperDashboard as a “God class.”
But if this class only have these functions
```
public class SuperDashboard extends JFrame implements MetaDataUser
public Component getLastFocusedComponent()
public void setLastFocused(Component lastFocused)
public int getMajorVersionNumber()
public int getMinorVersionNumber()
public int getBuildNumber()
}
```
This class is small but its responsibility is big. That how clean code starts.
The name of a class should describe what responsibilities it fulfills
We should also be able to write a brief description of the class in about 25 words,
without using the words “if,” “and,” “or,” or “but.”

## The Single Responsibility Principle
The Single Responsibility Principle (SRP)2 states that a class or module should have one,
and only one, reason to change.Classes should have one responsibility—one reason to
change. Trying to identify responsibilities (reasons to change) often helps us recognize and
create better abstractions in our code. For example 

public class Version {
public int getMajorVersionNumber()
public int getMinorVersionNumber()
public int getBuildNumber()
}

The Version class is a construct that has a high potential for reuse in other
applications!

Getting software to work and making software clean are two very different activities.
Most of us have limited room in our heads, so we focus on getting our code to work more than organization and cleanliness.
We fail to switch to the other concern of organization and cleanliness. Do you want your tools organized into toolboxes with many
small drawers each containing well-defined and well-labeled components? Or do you want
a few drawers that you just toss everything into?

# Cohesion
In general the more variables a method manipulates the more cohesive that method is to its class.
A class in which each variable is used by each method is maximally cohesive.
Consider the following code , the implemetation of stack:
```
public class Stack {
  private int topOfStack = 0;
  List<Integer> elements = new LinkedList<Integer>();
  public int size() {
  return topOfStack;
  }

  public void push(int element) {
  topOfStack++;
  elements.add(element);
  }

  public int pop() throws PoppedWhenEmpty {
  if (topOfStack == 0)
    throw new PoppedWhenEmpty();
    int element = elements.get(--topOfStack);
    elements.remove(topOfStack);
    return element;
  }
}
```
Here we were trying to seperate the classes into functions.  You should try to separate the variables and methods into two or
more classes such that the new classes are more cohesive.
  
##  How to change our Classes?
Changes of classes are continuaous process. 
 We have to structure our systems so that we muck with as little as possible when we
update them with new or changed features. In an ideal system, we incorporate new features
by extending the system, not by making modifications to existing code.


