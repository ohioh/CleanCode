# CleanCode - The art of refactoring

Refactoring: https://de.wikipedia.org/wiki/Refactoring

A Summary of Clean Code Book from Robert C. Martin (Autor) *big thanks for the coding lessons*

Robert C. “Uncle Bob” Martin has been a software professional since 1970 and an international software consultant since 1990. He is founder and president of Object Mentor, Inc., a team of experienced consultants who mentor their clients worldwide in the fields of C++, Java, C#, Ruby, OO, Design Patterns, UML, Agile Methodologies, and eXtreme programming.

C Based Ideas for a good Code: https://opensource.com/article/19/5/how-write-good-c-main-function</br>
Addtional Clean Coder knowledge: https://cleancoders.com/

### Design-Principles && Paradigms:
1.  Separation of Concerns 				-> Each class has exactly one responsibility
2.  DRY: Don‘t Repeat Yourself  "Once and only once"    -> Same or similar code should be present in the system only once
3.  Speaking Code Principle				-> The code should "speak" for itself like a book.
4.  Open Closed Principle				-> A component should be open for extensions.  Existing clients should not become invalid in the event of adaptations.
5.  Liskov Substitution Principle			-> An instance of a class must be usable anywhere in place of its superclass.
6.  Dependency Inversion				->  High-level concepts should not depend on low-level principle concepts or implementations
7.  Interface Segregation Principle   			-> Interfaces should be small. The methods of individual interfaces should have a high coupling.
8.  Common Reuse Principle 				-> The classes of a component are reused as a whole.
9.   Common Closure Principle				-> The classes of a component should be closed against the same type of changes.  If a change is made, only one component should be affected.
10.  Acyclic Dependency Principle			-> Die Abhängigkeitsstruktur zwischen Komponenten  soll azyklisch sein.
11.  Stable Dependency Principle			-> A component should only depend on components that are at least as stable as itself.
12.  Stable Abstractions Principle			-> The more stable a component is, the more abstract it should be. Unstable components should be concrete
13.  Tell, Don‘t Ask					-> Don't ask an object for an object, tell it what to do.
14.  Inversion of Control				-> An object is passive; it is supplied with all the information it needs from above.
15.  Law of Demeter					-> Each object should only talk to objects that it holds as attributes or is passed as parameters. 
16.   Differentiable programming                        -> is the very basis of deep learning, implemented in software libraries such as  TensorFlow and PyTorch. Differentiable programming is more than deep learning: it is a programming paradigm where the algorithms are not hand-coded, but learned






## Index
```
	Index:
	├── Chapter 1:  Clean Code
	├── Chapter 2:  Meaningfull name
	├── Chapter 3:  Functions
	├── Chapter 4:  Comments
	├── Chapter 5:  Formating
	├── Chapter 6:  Objects And Data Structures
	├── Chapter 7:  Error Handling
	├── Chapter 8:  Boundries
	├── Chapter 9:  Unit tests
	├── Chapter 10: Classes
	├── Chapter 11: System
	├── Chapter 12: Emergence 
	├── Chapter 13: Concurrency
	├── Chapter 14: Successive Refinement
	├── Chapter 15: JUnit Internals
	├── Chapter 16: Refactoring serial Data
	├── Chapter 17: Smells And Huristics
	├── Chapter 18: ISO 25000
	├── Chapter 19: Style Guides & UML
	└── Chapter 20: Coding Cycle 
```
Even bad code can function. But if code isn't clean, it can bring a development organization to its knees. Every year, countless hours and significant resources are lost because of poorly written code. But it doesn't have to be that way. Noted software expert Robert C. Martin presents a revolutionary paradigm with Clean Code: A Handbook of Agile Software Craftsmanship. Martin has teamed up with his colleagues from Object Mentor to distill their best agile practice of cleaning code "on the fly" into a book that will instill within you the values of a software craftsman and make you a better programmer--but only if you work at it. What kind of work will you be doing? You'll be reading code--lots of code. And you will be challenged to think about what's right about that code, and what's wrong with it. More importantly, you will be challenged to reassess your professional values and your commitment to your craft. Clean Code is divided into three parts. The first describes the principles, patterns, and practices of writing clean code. The second part consists of several case studies of increasing complexity.Each case study is an exercise in cleaning up code--of transforming a code base that has some problems into one that is sound and efficient. The third part is the payoff: a single chapter containing a list of heuristics and "smells" gathered while creating the case studies. The result is a knowledge base that describes the way we think when we write, read, and clean code. Readers will come away from this book understanding *How to tell the difference between good and bad code *How to write good code and how to transform bad code into good code *How to create good names, good functions, good objects, and good classes *How to format code for maximum readability *How to implement complete error handling without obscuring code logic *How to unit test and practice test-driven developmentThis book is a must for any developer, software engineer, project manager, team lead, or systems analyst with an interest in producing better code.</br>

## Chapter 1: Clean Code
Every movement of change needs energy. Aspecially to get a clean coder needs the motivation to go to this process. Oncle Bob did right to show us first the benefit of a clean code.Additional we try to answers the question about differenct views to identify clean code and the problem with bad code. 
The summary contains the understanding for different perspectives of aggregations to the code and 

### Bad Code
We try to develop our product with rush and just working code. we keep cleanning up the codes for later. But day by day the working bad codes create lots of bugs in future. It could breakdown a company for handling those unclean codes. We all know the law later equal never.

The Total Cost of Owning a Mess
If you continue the development with unclean code, later modification and adding of that code will be hard. The scaleability will be almost zero. So the aggregated bunch of unclean code could cost you whole fortune.

The Grand Redesign in the Sky
When you will realise that the we cannt make any changes on that messy code , you have to redesign the same functionality code with deiffernt experts. And if that experts dont code cleanely then you have to redesign it again and again.

### Goals to learn:
Software -> Programme -> ("Program"-)Code -> Task -> Segment -> Section -> Unit -> Line -> Comments

Topic Goals defined in the ISO 25000:Functionality, Reliability, Useability, Efficience, Modifiability, Portability

## Chapter 2:  Meaningfull name
## Chapter 3:  Functions
## Chapter 4:  Comments
## Chapter 5:  Formating
## Chapter 6:  Objects And Data Structures
## Chapter 7:  Error Handling
## Chapter 8:  Boundries
## Chapter 9:  Unit tests
## Chapter 10: Classes
## Chapter 11: System
## Chapter 12: Emergence 
## Chapter 13: Concurrency
## Chapter 14: Successive Refinement
## Chapter 15: JUnit Internals
## Chapter 16: Refactoring serial Data
## Chapter 17: Smells And Huristics
## Chapter 18: ISO 25000
## Chapter 19: Style Guides & UML
## Chapter 20: Coding Cycle

### Helpfull to write good markdown-Readme's: 
I love this on: **[Markdown Tutorial:](https://docs.github.com/en/github/writing-on-github/working-with-advanced-formatting)**.
One more *[Markdown Guide](https://www.markdownguide.org/basic-syntax/)*.
