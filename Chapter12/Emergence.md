# Chapter 12: Emergence 
## Getting Clean via Emergent Design
Simle design follows few rules by Kent
• Runs all the tests
• Contains no duplication
• Expresses the intent of the programmer
• Minimizes the number of classes and methods
The rules are given in order of importance. These rule will help you significantly in developping well designed software.

## Run all the test

A good tested code is a asset of a good software. That will make the whole project more progressiv.Remarkably, following a simple and obvious rule that says we need to have tests and
run them continuously impacts our system’s adherence to the primary OO goals of low
coupling and high cohesion. Writing tests leads to better designs.

## Refactoring
When we add some codes in our peogramm we have to test it again and redesign the code design . We have have to determine whether we are regreting or not. The fact that we have these tests eliminates the fear
that cleaning up the code will break it!

# No duplication
Redundance or duplication is always suggsted to be avoidded. It is our first enemy. 

public void scaleToOneDimension(
float desiredDimension, float imageDimension) {
if (Math.abs(desiredDimension - imageDimension) < errorThreshold)
return;
float scalingFactor = desiredDimension / imageDimension;
scalingFactor = (float)(Math.floor(scalingFactor * 100) * 0.01f);
RenderedOp newImage = ImageUtilities.getScaledImage(
image, scalingFactor, scalingFactor);
image.dispose();
System.gc();
image = newImage;
}
public synchronized void rotate(int degrees) {
RenderedOp newImage = ImageUtilities.getRotatedImage(
image, degrees);
image.dispose();
System.gc();
image = newImage;

In this code we should eliminate the small amount of duplication between
the scaleToOneDimension and rotate methods:

public void scaleToOneDimension(
float desiredDimension, float imageDimension) {
if (Math.abs(desiredDimension - imageDimension) < errorThreshold)
return;
float scalingFactor = desiredDimension / imageDimension;
scalingFactor = (float)(Math.floor(scalingFactor * 100) * 0.01f);
replaceImage(ImageUtilities.getScaledImage(
image, scalingFactor, scalingFactor));
}
public synchronized void rotate(int degrees) {
replaceImage(ImageUtilities.getRotatedImage(image, degrees));
}
private void replaceImage(RenderedOp newImage) {
image.dispose();
System.gc();
image = newImage;
}

# Expressive

We can keep our code expressive by keeping good name , keeping our function small ,using stadard nomenculture.Well-written unit tests are also expressive. A primary goal of tests is to act as documentation
by example. With minimal classes and methods we can also make our code more expressive.
If keep our overall system so simple the it is more essy to maintain.
