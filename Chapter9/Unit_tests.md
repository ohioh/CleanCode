# Chapter 9: Unit tests
We code a lots of programms , run it and have adicision that it is working. But most of thr programmer miss the testing of that programm . Here we are going to talk about TDD( Test Driven Development) . Sometiem we test our code for good performance , But in the mad rush to add testing to our discipline, many
programmers have missed some of the more subtle, and important, points of writing
good tests.

## The Three Laws of TDD
By now everyone knows that TDD asks us to write unit tests first, before we write production
code. But that rule is just the tip of the iceberg. Consider the following three laws:

First Law You may not write production code until you have written a failing unit test.
Second Law You may not write more of a unit test than is sufficient to fail, and not compiling
is failing.
Third Law You may not write more production code than is sufficient to pass the currently
failing test.
This is a cycle of test coding and production coding . If we write lots of test code , the production could suffer. We need to clean those up.

## Keeping Tests Clean
Test code is just as important as production code. It
is not a second-class citizen. It requires thought, design, and care. It must be kept as clean
as production code. So like production code we need to follow all the rules of cleaning code in test code.

## Clean Test
Readibility is the most important thing in clean test. The same thing that makes all code readable: clarity, simplicity,
and density of expression. If we consider the code

public void testGetPageHieratchyAsXml() throws Exception
{
crawler.addPage(root, PathParser.parse("PageOne"));
crawler.addPage(root, PathParser.parse("PageOne.ChildOne"));
crawler.addPage(root, PathParser.parse("PageTwo"));
request.setResource("root");
request.addInput("type", "pages");
Responder responder = new SerializedPageResponder();
SimpleResponse response =
(SimpleResponse) responder.makeResponse(
new FitNesseContext(root), request);
String xml = response.getContent();
assertEquals("text/xml", response.getContentType());
assertSubString("<name>PageOne</name>", xml);
assertSubString("<name>PageTwo</name>", xml);
assertSubString("<name>ChildOne</name>", xml);
}
public void testGetPageHieratchyAsXmlDoesntContainSymbolicLinks()
throws Exception
{
WikiPage pageOne = crawler.addPage(root, PathParser.parse("PageOne"));
crawler.addPage(root, PathParser.parse("PageOne.ChildOne"));
crawler.addPage(root, PathParser.parse("PageTwo"));
PageData data = pageOne.getData();
WikiPageProperties properties = data.getProperties();
WikiPageProperty symLinks = properties.set(SymbolicPage.PROPERTY_NAME);
symLinks.set("SymPage", "PageTwo");
pageOne.commit(data);
request.setResource("root");
request.addInput("type", "pages");
Responder responder = new SerializedPageResponder();
SimpleResponse response =
(SimpleResponse) responder.makeResponse(
new FitNesseContext(root), request);
String xml = response.getContent();
assertEquals("text/xml", response.getContentType());
assertSubString("<name>PageOne</name>", xml);
assertSubString("<name>PageTwo</name>", xml);
assertSubString("<name>ChildOne</name>", xml);
assertNotSubString("SymPage", xml);
}
public void testGetDataAsHtml() throws Exception
{
crawler.addPage(root, PathParser.parse("TestPageOne"), "test page");
request.setResource("TestPageOne");
request.addInput("type", "data");
Responder responder = new SerializedPageResponder();
SimpleResponse response =
(SimpleResponse) responder.makeResponse(
new FitNesseContext(root), request);
String xml = response.getContent();
assertEquals("text/xml", response.getContentType());
assertSubString("test page", xml);
assertSubString("<Test", xml);
}

This code has lots of redundant stuff like addpage() .More importantly, this
code is just loaded with details that interfere with the expressiveness of the test. this code was not designed to be read. The poor reader is inundated with a
swarm of details that must be understood before the tests make any real sense.
Now lets clean the test code
public void testGetPageHierarchyAsXml() throws Exception {
makePages("PageOne", "PageOne.ChildOne", "PageTwo");
submitRequest("root", "type:pages");
assertResponseIsXML();
assertResponseContains(
"<name>PageOne</name>", "<name>PageTwo</name>", "<name>ChildOne</name>"
);
}
public void testSymbolicLinksAreNotInXmlPageHierarchy() throws Exception {
WikiPage page = makePage("PageOne");
makePages("PageOne.ChildOne", "PageTwo");
addLinkTo(page, "PageTwo", "SymPage");
submitRequest("root", "type:pages");
assertResponseIsXML();
assertResponseContains(
"<name>PageOne</name>", "<name>PageTwo</name>", "<name>ChildOne</name>"
);
assertResponseDoesNotContain("SymPage");
}
public void testGetDataAsXml() throws Exception {
makePageWithContent("TestPageOne", "test page");
submitRequest("TestPageOne", "type:data");
assertResponseIsXML();
assertResponseContains("test page", "<Test");
}

We have seperated the whole code into three parts. The first part builds up the test data, the
second part operates on that test data, and the third part checks that the operation yielded
the expected results. It makes our test code more clean.

Some other tips of clean testing code:
* There are things that you might never do in a
production environment that are perfectly fine in a test environment. Usually they involve
issues of memory or CPU efficiency. But they never involve issues of cleanliness.
* Do one assert per test.
* Always keep single concept in a test code.
* Clean code need to be Fast , Independent , Repeatable, Self-Validating and Timely;

