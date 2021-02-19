# Chapter 8: Boundries
We always have to use third party code  , packages or open source code. So we need ot integret those codes in clean way. 

## Using Third-Party Code
Suppose we need Sensors data with third party library Map

Map<Sensor> sensors = new HashMap<Sensor>();
...
Sensor s = sensors.get(sensorId );
  
If we have to use again again in different class then we have to write those code in every class. But if we just Declare a another sensor class like this

public class Sensors {
private Map sensors = new HashMap();
public Sensor getById(String id) {
return (Sensor) sensors.get(id);
}
//snip
}

Then we dont have think about Map and its generic problem , which is solved by type casting. We are not suggesting that every use of Map be encapsulated in this form. Rather, we
are advising you not to pass Maps (or any other interface at a boundary) around your
system.
## Learning Tests Are Better Than Free
We can have a test approach for learnig those third party code instead of reading their documentation. we could write some
tests to explore our understanding of the third-party code. Jim Newkirk calls such tests
learning tests.This will save our time and effort for using third part api. Whether you need the learning provided by the learning tests or not, a clean boundary
should be supported by a set of outbound tests that exercise the interface the same way the
production code does.

# Clean Boundaries
Good software
designs accommodate change without huge investments and rework. Code at the boundaries needs clear separation and tests that define expectations. Either way our code speaks to us better,
promotes internally consistent usage across the boundary, and has fewer maintenance
points when the third-party code changes.



