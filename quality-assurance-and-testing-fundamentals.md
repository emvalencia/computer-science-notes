# Software Quality Assurance and Testing 
---
I.   General Testing Concepts/Terminology

II.  Goals of Testing

III. Levels of Testing

IV.  Best Way to Choose Test Cases

V.   Black-box Testing

VI.  White-box Testing

VII. Quality Assurance 

## I. General Testing Concepts 
> "The Royal Road to Software Engineering Capability: You need to build, test, and debug real software." 
- Since software is everywhere, the cost of software is increasing
- Purpose of testing: detect and correct errors in a software product
- Process: devise test case and expected output, run test case, capture actual output, compare actual output to expected output
    - Will succeed for fail (report failure) 
- Terminology:
    - **Error**- human mistake
    - **Fault or defect**- mistake in code 
    - **Failure**- external behavior/execution/output incorrect 
- **Formal verification**- establish correctness of programs using formal methods of mathematics
- **Static analysis**- examine code without executing the program
- **Dynamic analysis**- execute the program with test cases ; use test oracles that know exactly what you're looking for
- Software properties:
    - External properties that can be verified: timlessness, interoperability
    - Dependability properties: correctness, safety, reliability, robustness
    - Process-oriented properties: maintainability, reusability, modularity
    - External properties that can be validated: usability, elegance
- Testing fundamentals:
    - Validation
    - Verification

## II. Goals
  > "Problem testing can be used to show the presence of bugs, but never to show their absence." - Dijkstra
  - Find and fix failures/faults 
  - Find as many bugs as possible
  - Improve confidence that the system performs as specified (verification) and as desired (validation)
  - Make sure it's accurate, thorough, repeatable, and systematic 
  - How do we know when we are done testing?
    - Finding bugs = fixes
    - Not finding bugs = gives us nothing, you can never know/confirm that it is 100% bug-free 
    - Can stop testing when the problem find rate stabilizes to near zero 
    - Aim to meet the quality requirements established for the project  

## III. Levels of Testing 
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
  
  
  
@copy: Note are from courses from Professor Ziv, Professor Navarro, and I. Ahmed
