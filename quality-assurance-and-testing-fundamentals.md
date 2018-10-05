# Software Quality Assurance and Testing 
---
I. Background and General Testing Concepts/Terminology

II. Goals of Testing

III. Kinds of Testing

IV. Best Way to Choose Test Cases

V. Black-box Testing

VI. White-box Testing

VII. Quality Assurance 

## I. Background and General Testing Concepts
### Background
- Since software is everywhere, the cost of software is increasing
- Software engineering is the youngest engineering discipline, but similar to the others in some ways:
    - Design is difficult but important
    - Implementation is difficult and important
    - Building complex artifacts must work
    - Use of mathematical principles, scientific understanding
- Unlike other disciplines...
    - Software engineers have many more parts to keep track of, discrete vs. continuous behavior, radically different designs
    - Patching code is easier, computers make our jobs easier, have a greater ability to test!
- Software development consists of a manager that developers and testers report to; manager acts as a supervisor and mediator between the parties
    - Note that developers aren't testers and vice versa
    - Developers write *implementation* and testers write *specification* 
- Key observations in software development:
    - Specifications must be explicit
    - Independent development and testing 
    - Resources are finite -> there's a limit to how many tests you can write
    - Specifications evolve over time -> tests have to be updated over time
    - Automated testing
- A "bug" is an error in software
    - Term was coined by Grace Hopper because her machine was causing errors due to a moth stuck inside of it
- Software properties:
    - External properties that can be verified: timlessness, interoperability
    - Dependability properties: correctness, safety, reliability, robustness
    - Process-oriented properties: maintainability, reusability, modularity
    - External properties that can be validated: usability, elegance

### General Testing Concepts
> "The Royal Road to Software Engineering Capability: You need to build, test, and debug real software." 
- **Testing**- running a program in order to find faults
- Purpose of testing: detect and correct errors in a software product; increase our confidence in a program (high quality, low risk)
- Process: devise test case and expected output, run test case, capture actual output, compare actual output to expected output
    - Will succeed for fail (report failure) 
- Terminology:
    - **Fault or defect**- mistake in code, a static flaw in a program, a bug
        - To expose a fault with a test:
            - *Reachability*: test must reach and execute location of the fault
            - *Infection*: fault corrupts program state -> error
            - *Propogation*: error must persist and cause an incorrect output -> failure
    - **Error**- human mistake, bad program state that results from a fault (not all faults produce an error)
    - **Failure**- external behavior/execution/output incorrect (not every error causes a program failure)
- **Formal verification**- establish correctness of programs using formal methods of mathematics
- **Static analysis**- examine code without executing the program
    - Pure static analysis isn't "software testing" because you aren't actually running the program to see if there are errors
- **Dynamic analysis**- execute the program with test cases ; use test oracles that know exactly what you're looking for
- Testing fundamentals:
    - **Validation** - "Are we building the right machine?", usability testing and user feedback
    - **Verification** - "Are we building the machine right?", testing, inspections, and static analysis
- Specifications
    - Testing checks if the program matches the specifications
    - Specifications outline what the program should do
    - Testing is a form of consistency between implementation and specification
- **Test case**: one execution of the program which may expose a bug
- **Test suite**: set of executions of a program; made of test cases

## II. Goals
  > "Problem testing can be used to show the presence of bugs, but never to show their absence." - Dijkstra
  - Find and fix failures/faults/bugs as possible 
      - Ideally, we want to prove that code is correct using formal mathematical techniques
        - Can be difficult
        - Not always practical
      - Nearly ideally, we can use a symbolic or abstract model to check our system
        - Extracts a mathematical abstraction from a system
        - Proves properties over all possible executions
        - Doesn't work well for more complex properties and data structures
       - As a last resort we can run our program and see if it works
  - Testing improves confidence that the system performs as specified (verification) and as desired (validation)
  - Make sure it's accurate, thorough, repeatable, and systematic 
  - How do we know when we are done testing?
    - Finding bugs = fixes
    - Not finding bugs = gives us nothing, you can never know/confirm that it is 100% bug-free 
    - Can stop testing when the problem find rate stabilizes to near zero 
    - Aim to meet the quality requirements established for the project  
  - You can never be 100% certain that a program is bug-free because there is no possible way to test all possible program exections...
  - The biggest challenge for a tester is to construct effective test samples that reveal faults, performance bottlenecks, and demonstrate reliability, usability, etc...

## III. Kinds of Testing 
  - **Manual testing**: human sits at a program and manually enters inputs to test it
  - **Automated testing**: humans write programs that produce tests or use scripts/other methods to make the computer execute tests
  - When to use manual vs. automated: depends, a good tester will know which one to us
  - **Scripted testing**: a tester follows a fixed script
  - **Exploratory testing**: tester has general guidelines but is free to explore
  - **Unit testing**: testing of a single code unit 
  - Functional/integration testing: testing of interfaces among integrated units
  - System/acceptance testing: testing of complete system for satisfaction and requirements 

## IV. Best Way To Choose Test Cases 
  - Intuition 
  - Specification (black-box testing)- equivalence class partitioning, boundary-value analysis 
  - Code (white-box testing)- path analysis 
  - Existing test cases
  - Faults
  - **Test oracles**: mechanism for deciding if a test mechanism succeeds or fails, difficult to automate

## V. Black-box Testing 
  - Aka specification-based testing- use specifications to derive test cases
  - Do not have access to the code, Only know what it's supposed to do
  - Choose test cases that guarantee a wide range of coverages (typical values, boundary values, special cases, invalid input values)
  - **Equivalence class partitioning**:
    - Divide input into several classes that are considered "equivalent" for the purpose of finding errors
      o If fails/passes for one member of the class, it is likely to fail/pass for all members
    - Classes are determined by: looking at requirements specification, tester's intuition 
    - Classes should cover the complete input domain, should never overlap 
  - **Bounary value analysis**:
    - Exp has shown that many errors are made at the "boundaries" rather than under normal conditions
      ex. Confusion between < and <=
    - Uses same classes as equivalence partitioning but tests at the boundaries rather just any element
  - **Systematic approach to equivalence class partitioning and boundary value analysis**:
    1. Identify the set of all possible inputs, aka domain
    2. Identify a basis for subdividing the set of inputs
      ex. Size/magnitude, structure, correctness, your creative thinking 
    3. Use this basis to divide the set of all possible inputs into classes/subdomains
    4. From each subdomain select [a] representatives to be [a] test case input/s (one test case may be okay!)
    5. Test for each subdomain: normal values, boundary or edge input values 
       Example: quizAverage (following systematic approach)
        1. Identify all set of integers (scores that students may get)
        2. Subdivide it into length of the list, position of min score, number of minima, magnitude of numbers
            - Looking at how to divide the LIST as opposed to the actual values of the quizzes
            - Length of the list: how many quizzes were received 
            - Position of min score: can subdivide the list by the lower scores, no need to look at the lower scores
            - Number of minima:
            - Magnitude of numbers
        3. Divide into subdomains:
            - Len of list: 0 elements, 1, 2-10, 11+
            - Position of min score: first, middle, last
            - Number of minima: 1, a few, all 
            - Magnitude of numbers: 0-33, 34-66, 67-100, mixed 
         4. Select representatives from each subdomain to be used as test case input/s
            - Len of list: [], [87.3], [80,81,83.4]....
               o Check: empty list, one element, small (2-10 elements), large (11+ elements)
               o Does changing the length of the list affect the code's output?
            - Position of min score: [80, 87, 88, 89], [87, 88, 89, 80], [87, 88, 80, 89],... 
               o Does changing the position of the min score affect the code's output?
            - Number of minima: [80, 87, 88, 89], [97, 80, 80], [88, 88, 88, 88], ... 
               o Check: one minima in the list, a few minima, all are minima 
               o Does changing the number of each value affect the code's output?
            - Magnitude of numbers: [0, 4, 15, 5, 33], [100, 67], [47, 43, 24, 58, 60], ...
               o 
               o Does the magnitude of numbers (how much they vary) affect the code's output?   
         o Remember! Trying to find bugs, trap the software
    - When doing systematic testing, can visualize it using a simple graph
        o Title: the basis you are testing
        o Split into sections: test cases (input), subdomains, expected output, actual output
                              Length of List (for quizAverage example)
                              
         | Test Case     |       Subdomains       |  Expected Output |   Actual Output              |
         |---------------|:----------------------:|:----------------:|-----------------------------:|
         |     ()        |  empty                    |       0.0        |        9.9999!       #ERROR  |
         |     (87)      |         one              |       87.0       |        crashes       #ERROR  |
         |     (90,95,85)|             small          |       92.5       |        92.5          #Passes |
         |     (80,81,82, 83,84,85,86,87,99) |   large    |     86.0         |      86.0          #Passes   |
            
  
## VI. White-box Testing 
  - Aka structural testing 
  - Have access to the code 
  
  
  
## VII. Quality Assurance
- Quality assurance: all activities designed to measure and improve quality in a product
- **QA goals**:
  - Verification - implement the idea properly
  - Validation - implement the proper idea 
- Ideal scenario: complete formal specification of problem to be solved, design in formal notation, code in verifiable language,
  executable machine code, execution on verified hardware
- Real world scenario: mixture of formal and informal specifications, design in mixed notation, code in C++/Java/Ada, (Intel
  Pentium-based) machine code, execution on commercial hardware
- Why is QA difficult?
  - Complex data communications
  - Distributed processing
  - Stringent performance objectives
  - Complex processing 
  - QA lays out the rules, uncovers the faults, and is viewed as cumbersome/heavy (people just want to code/be left alone)
- QA techniques:
  - Formal methods
  - Static analysis of program properties
  - Reviews and inspections
  - Testing 
  
  
  
@copyright. Notes are from UCI lectures and slides from courses taught by Professor Ziv, Professor Navarro, and Professor Ahmed.
