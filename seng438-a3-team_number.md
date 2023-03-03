**SENG 438 - Software Testing, Reliability, and Quality**

**Lab. Report #3 – Code Coverage, Adequacy Criteria and Test Case Correlation**

| Group \#:       |     |
| --------------- | --- |
| Student Names:  |     |
| Chun-chun Huang |     |
| Amneet Deol     |     |
| Shreosi Debnath |     |

(Note that some labs require individual reports while others require one report
for each group. Please see each lab document for details.)

# 1 Introduction

Text…

# 2 Manual data-flow coverage calculations for X and Y methods

DataUtilities.calculateColumnTotal

- Data Flow Graph

## Def-use sets

| Line | use            | def      |
| ---- | -------------- | -------- |
| 1    | data           |          |
| 2    |                | total    |
| 3    | data           | rowCount |
| 4    | r, rowCount    | r        |
| 5    | r,column,data  | n        |
| 6    | n              |          |
| 7    | total,n        |          |
| 10   | r2,rowCount    | r2       |
| 11   | r2,column,data | n        |
| 12   | n              |          |
| 13   | total,n        |          |
| 16   | total          |          |

## DU-pairs

| var      | D-U pair        |
| -------- | --------------- |
| total    | (2,7)           |
| rowCount | (3,4)           |
| r        | (4,4),(4,5)     |
| n        | (5,6),(11,12)   |
| r2       | (10,10),(10,11) |

- DU-pair coverage

Range.getUpperBound

- Data Flow Graph
- Def-use sets
- DU-pairs
- DU-pair coverage

# 3 A detailed description of the testing strategy for the new unit test

We run the coverage tool Elemma for our unit test in assignment 2. Looking at metric for statement coverage, we implement for tests trying to reach 90% statement coverage. As we approach 90% line coverage, our brach coverage reach 70%.

# 4 A high level description of five selected test cases you have designed using coverage information, and how they have increased code coverage

Text…

# 5 A detailed report of the coverage achieved of each class and method (a screen shot from the code cover results in green and red color would suffice)

---------------------------------------
**DataUtilities Before New Tests**

Instruction Coverage
![DataUtilitiesInstructionCoverageBefore](https://user-images.githubusercontent.com/72403820/222765254-f4f7a707-37f6-453e-9969-08885eef743c.png)

Branch Coverage
![DataUtilitiesBranchCoverageBefore](https://user-images.githubusercontent.com/72403820/222765222-5a890cb3-4239-4f72-9e9f-9e573f5d19fa.png)

Method Coverage
![DataUtilitiesMethodCoverageBefore](https://user-images.githubusercontent.com/72403820/222765322-4a6c6445-44e6-4bff-a6a4-73b0aded85e4.png)

---------------------------------------
**DataUtilities After New Tests**

Instruction Coverage
![DataUtilitiesInstructionCoverage](https://user-images.githubusercontent.com/72403820/222765188-de3e2b0f-88cd-4f9d-8b08-a0cd97ec59b4.png)

Branch Coverage
![DataUtilitiesBranchCoverage](https://user-images.githubusercontent.com/72403820/222765365-7a55d20a-5ac9-40f3-a644-206940972589.png)

Method Coverage
![DataUtilitiesMethodCoverage](https://user-images.githubusercontent.com/72403820/222765339-cb819f77-a310-4d75-ac10-6bd6dcb0e786.png)

---------------------------------------

## Range.java

### Range statement coverage

<img src="./media/Range_LineCoverage.PNG" />

### Range brach coverage

<img src="./media/Range_BranchCoverage.PNG" />

# 6 Pros and Cons of coverage tools used and Metrics you report

## Pros of Eclemma

- easy installation through Eclipse extention market
- provide code measurement by using variety of coverage metrics, such as line coverage, branch coverage
- Elemma highlight the codes that have been covered during the testing

## Cons of Elemma

- only measures coverage during testing but it does not provide insight to quality or performance of the codes

# 7 A comparison on the advantages and disadvantages of requirements-based test generation and coverage-based test generation.

Text…

# 8 A discussion on how the team work/effort was divided and managed

- Chun-chun
  : work on increasing range test coverage

# 9 Any difficulties encountered, challenges overcome, and lessons learned from performing the lab

Text…

# 10 Comments/feedback on the lab itself

Text…
