# Chapter 15: JUnit Internals
Kent Beck and Eric Gamma started to develop a testing program called jUnit. It is a great testing tool. Lots of developer and company uses this tool to test their java code.
We could explain it further, but the test cases do a better job. So take a look at the code
and you will understand the requirements of this module in depth. While you are at it,
critique the structure of the tests. Could they be simpler or more obvious?
package junit.tests.framework;
import junit.framework.ComparisonCompactor;
import junit.framework.TestCase;
public class ComparisonCompactorTest extends TestCase {
public void testMessage() {
String failure= new ComparisonCompactor(0, "b", "c").compact("a");
assertTrue("a expected:<[b]> but was:<[c]>".equals(failure));
}
public void testStartSame() {
String failure= new ComparisonCompactor(1, "ba", "bc").compact(null);
assertEquals("expected:<b[a]> but was:<b[c]>", failure);
}
public void testEndSame() {
String failure= new ComparisonCompactor(1, "ab", "cb").compact(null);
assertEquals("expected:<[a]b> but was:<[c]b>", failure);
}
public void testSame() {
String failure= new ComparisonCompactor(1, "ab", "ab").compact(null);
assertEquals("expected:<ab> but was:<ab>", failure);
}
public void testNoContextStartAndEndSame() {
String failure= new ComparisonCompactor(0, "abc", "adc").compact(null);
assertEquals("expected:<...[b]...> but was:<...[d]...>", failure);
}
  public void testStartAndEndContext() {
String failure= new ComparisonCompactor(1, "abc", "adc").compact(null);
assertEquals("expected:<a[b]c> but was:<a[d]c>", failure);
}
public void testStartAndEndContextWithEllipses() {
String failure=
new ComparisonCompactor(1, "abcde", "abfde").compact(null);
assertEquals("expected:<...b[c]d...> but was:<...b[f]d...>", failure);
}
public void testComparisonErrorStartSameComplete() {
String failure= new ComparisonCompactor(2, "ab", "abc").compact(null);
assertEquals("expected:<ab[]> but was:<ab[c]>", failure);
}
public void testComparisonErrorEndSameComplete() {
String failure= new ComparisonCompactor(0, "bc", "abc").compact(null);
assertEquals("expected:<[]...> but was:<[a]...>", failure);
}
public void testComparisonErrorEndSameCompleteContext() {
String failure= new ComparisonCompactor(2, "bc", "abc").compact(null);
assertEquals("expected:<[]bc> but was:<[a]bc>", failure);
}
public void testComparisonErrorOverlapingMatches() {
String failure= new ComparisonCompactor(0, "abc", "abbc").compact(null);
assertEquals("expected:<...[]...> but was:<...[b]...>", failure);
}
public void testComparisonErrorOverlapingMatchesContext() {
String failure= new ComparisonCompactor(2, "abc", "abbc").compact(null);
assertEquals("expected:<ab[]c> but was:<ab[b]c>", failure);
}
public void testComparisonErrorOverlapingMatches2() {
String failure= new ComparisonCompactor(0, "abcdde",
"abcde").compact(null);
assertEquals("expected:<...[d]...> but was:<...[]...>", failure);
}
public void testComparisonErrorOverlapingMatches2Context() {
String failure=
new ComparisonCompactor(2, "abcdde", "abcde").compact(null);
assertEquals("expected:<...cd[d]e> but was:<...cd[]e>", failure);
}
public void testComparisonErrorWithActualNull() {
String failure= new ComparisonCompactor(0, "a", null).compact(null);
assertEquals("expected:<a> but was:<null>", failure);
}
public void testComparisonErrorWithActualNullContext() {
String failure= new ComparisonCompactor(2, "a", null).compact(null);
  ssertEquals("expected:<a> but was:<null>", failure);
}
public void testComparisonErrorWithExpectedNull() {
String failure= new ComparisonCompactor(0, null, "a").compact(null);
assertEquals("expected:<null> but was:<a>", failure);
}
public void testComparisonErrorWithExpectedNullContext() {
String failure= new ComparisonCompactor(2, null, "a").compact(null);
assertEquals("expected:<null> but was:<a>", failure);
}
public void testBug609972() {
String failure= new ComparisonCompactor(10, "S&P500", "0").compact(null);
assertEquals("expected:<[S&P50]0> but was:<[]0>", failure);
  
  We ran a code coverage analysis on the ComparisonCompactor using these tests. The code
is 100 percent covered. Every line of code, every if statement and for loop, is executed by
the tests. This gives me a high degree of confidence that the code works and a high degree
of respect for the craftsmanship of the authors.
If we look other example code the we can understand how to structure our testing code.

package junit.framework;
public class ComparisonCompactor {
private static final String ELLIPSIS = "...";
private static final String DELTA_END = "]";
private static final String DELTA_START = "[";
private int fContextLength;
private String fExpected;
private String fActual;
private int fPrefix;
private int fSuffix;
public ComparisonCompactor(int contextLength,
String expected,
String actual) {
fContextLength = contextLength;
fExpected = expected;
fActual = actual;
}
public String compact(String message) {
if (fExpected == null || fActual == null || areStringsEqual())
return Assert.format(message, fExpected, fActual);
findCommonPrefix();
findCommonSuffix();
String expected = compactString(fExpected);
String actual = compactString(fActual);
return Assert.format(message, expected, actual);
}
private String compactString(String source) {
String result = DELTA_START +
source.substring(fPrefix, source.length() -
fSuffix + 1) + DELTA_END;
if (fPrefix > 0)
result = computeCommonPrefix() + result;
if (fSuffix > 0)
result = result + computeCommonSuffix();
return result;
}
private void findCommonPrefix() {
fPrefix = 0;
int end = Math.min(fExpected.length(), fActual.length());
for (; fPrefix < end; fPrefix++) {
if (fExpected.charAt(fPrefix) != fActual.charAt(fPrefix))
break;
}
}
private void findCommonSuffix() {
int expectedSuffix = fExpected.length() - 1;
int actualSuffix = fActual.length() - 1;
for (;
actualSuffix >= fPrefix && expectedSuffix >= fPrefix;
actualSuffix--, expectedSuffix--) {
if (fExpected.charAt(expectedSuffix) != fActual.charAt(actualSuffix))
break;
}
fSuffix = fExpected.length() - expectedSuffix;
}
private String computeCommonPrefix() {
return (fPrefix > fContextLength ? ELLIPSIS : "") +
fExpected.substring(Math.max(0, fPrefix - fContextLength),
fPrefix);
}
private String computeCommonSuffix() {
int end = Math.min(fExpected.length() - fSuffix + 1 + fContextLength,
fExpected.length());
return fExpected.substring(fExpected.length() - fSuffix + 1, end) +
(fExpected.length() - fSuffix + 1 < fExpected.length() -
fContextLength ? ELLIPSIS : "");
}

We have satisfied the Boy Scout Rule. We have left this module a bit cleaner than
we found it. Not that it wasn’t clean already. The authors had done an excellent job with it.
But no module is immune from improvement, and each of us has the responsibility to
leave the code a little better than we found it.
  
  
  
