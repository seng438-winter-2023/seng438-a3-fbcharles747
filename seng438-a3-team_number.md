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

Text…

# 4 A high level description of five selected test cases you have designed using coverage information, and how they have increased code coverage

Text…

# 5 A detailed report of the coverage achieved of each class and method (a screen shot from the code cover results in green and red color would suffice)

Text…

# 6 Pros and Cons of coverage tools used and Metrics you report

Text…

## Pros of Eclemma

- easy installation through Eclipse extention market

# 7 A comparison on the advantages and disadvantages of requirements-based test generation and coverage-based test generation.

Text…

# 8 A discussion on how the team work/effort was divided and managed

- Chun-chun
  : work on increasing range test coverage

# 9 Any difficulties encountered, challenges overcome, and lessons learned from performing the lab

Text…

# 10 Comments/feedback on the lab itself

Text…
