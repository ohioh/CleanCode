### Chapter 1: Clean Code


### What is bad Code?
If code is not understandable ***like a good book***, the ***complexity needs long time*** to understand and documentation is unclear or not avaible, "To do" list is long,
and no clear structur and reusability is not given...
the "red line" in the code is maybe visible but different ways/ possbilities are not clear. 

### What is the cost of bad code?
(productivity vs time)
To go forward adding code to such structures will distroy productivity and creativity and need exponential more time.
Redesign is not possible because it is nearly unpossible to build the structure to reqonstruct the ways without copieng the mess in it.
In each way it is a waste of time. Ofcourse it is important that clean code will use more time too, but at the end it will need maybe the same time.
The difference is at the same investment of time the base in clean code for going forward and build more creativity instead of stagnation. The goal it to write instead of repairing. For this the right way of refactoring is a key element,

### Attitude: 
Why does this happen to code? Why does good code rot so quickly into bad code?
<p>But the fault is not in our stars, but in ourselves.We are unprofessional.</p>
A ***philosphy in the managment and in the company strategy*** is needed.
The need is to see the awesome creativty in the clean code. This can have issuess too but they have to be at the todo list and it needs the discilpine to work first with the todo and then adding new code.
An internal review to the code with our self on a ***true refelction is*** important.
So too it is unprofessional for programmers to bend to the will of managers who don’t
understand the risks of making messes.

### The Primal Conundrum
True professionals know that the second part of the conundrum is wrong. You will not
make the deadline by making the mess.
Indeed, the mess will slow you down instantly, and
will force you to miss the deadline. The only way to make the deadline—the only way to
go fast—is to keep the code as clean as possible at all times.

### The Art of Clean Code?
“How do I write clean code?”
Writing clean code requires the disciplined use of a myriad little techniques applied
through a painstakingly acquired sense of “cleanliness.” This “code-sense” is the key.

### What Is Clean Code?
<h2>Bjarne Stroustrup:</h2>
I like my code to be elegant and efficient. The
logic should be straightforward to make it hard
for bugs to hide, the dependencies minimal to
ease maintenance, error handling complete
according to an articulated strategy, and per-
formance close to optimal so as not to tempt
people to make the code messy with unprinci-
pled optimizations. Clean code does one thing
well.
-> Bad code tempts the mess to grow!
-> One broken window starts the process toward decay.
-> clean code does one thing well
-> Clean code is focused. Each
function, each class, each module exposes a single-minded attitude that remains entirely
undistracted, and unpolluted, by the surrounding details.

<h2>Grady Booch:</h2>C
Clean code is ***simple and direct***. Clean code
reads like well-written prose. Clean code never
obscures the designer’s intent but rather is full
of crisp abstractions and straightforward lines
of control.
-> ***readability perspective***. clean code should
read like well-written prose.
-> “crisp abstraction” to be a fascinating oxymoron!

<h2>“Big” Dave Thomas:</h2>
<p>Clean code can be read, and enhanced by a
developer other than its original author. It has
unit and acceptance tests. It has meaningful
names. It provides one way rather than many
ways for doing one thing. It has minimal depen-
dencies, which are explicitly defined, and pro-
vides a clear and minimal API. Code should be
literate since depending on the language, not all
necessary information can be expressed clearly
in code alone </p>
<p>
-> Dave asserts that
clean code makes it easy for other people to enhance it
-> the discipline of Test Driven Development
-> Code,without tests, is not clean.
-> code should be literate.</p>


<h2>Michael Feathers:</h2>
<p>Clean code always
looks like it was written by someone who cares.
One word: care. That’s really the topic of
this book. Perhaps an appropriate subtitle
would be How to Care for Code.</p>

<h2>Ron Jeffries:</h2>
<p>In recent years I begin, and nearly end, with Beck’s
rules of simple code. In priority order, simple code:</br>
- Runs all the tests;</br>
- Contains no duplication;</br>
- Expresses all the design ideas that are in the
system;</br>
- Minimizes the number of entities such as classes,
methods, functions, and the like.</br></p>

<p>When the same thing is done over and over,
it’s a sign that there is an idea in our mind that is not well represented in the code. I try to
figure out what it is. Then I try to express that idea more clearly.</p>

<p>Ron has summarized the contents of this book. No
duplication, one thing, expressiveness, tiny abstractions. Everything is there.</p>

<h2>Ward Cunningham</h2>
<p>You know you are working on clean code when each
routine you read turns out to be pretty much what
you expected. You can call it beautiful code when
the code also makes it look like the language was
made for the problem.</p>


<h2>Summary: Strategy and possible Derivations</h2> 
***true refelection*** 
***simple and direct***
***elegant and efficient Logic ***

1.  Define & Point the Needs of the work and Goal
2.  explain process ("Expresses all the design ideas that are in the system")
3.  give input
4.  calculate the output
5.  Name the process and subprocess ( "meaningful names")
6.  Visulaize the logic and compare to code idea
7.  divide and conquere Problems
8.  Create command guide to the goal
9.  Splitt in small closed and well created parts ("No duplication, one thing, expressiveness, tiny abstractions")
10.  Make functions, classes and Moduls autarc and connectable ("Minimizes the number of entities such as classes,methods, functions ")
11.  Start to focus your code ( this unit has to be well ) before starting the next part. go to next segment/section/unit if the code is awesome
12.  Start to create "Lord of the rings" first chapter ( remember: "clean code should read like well-written prose" )
13. Optimize the concept ( " minimal dependencies, which are explicitly defined, and provides a clear and minimal API" )

cares your code and read it as a non author without coding language and refelct the need to concentrate to understand you code


Task -> Segment -> Section -> Unit -> Line -> Comments

