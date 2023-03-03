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

## DataUtilitiesTest

Test Case 1: cloneTest()
clone() is a new method in DataUtilities that was not present in assignment 2, and so we had 0% coverage for this function. We created cloneTest() and cloneTestWithNull() to provide coverage over this new method and with these new tests were able to provide 100% instruction, branch, and method coverage on the clone() method.

Test Case 2: calculateRowTotalWithNegativeColCount()
calculateRowTotal() is a method in DataUtilities that we had 83% coverage for from Assignment 2. There was one pathway that we were not testing which was when a Values2D with a negative column count is passed in, 0 should be returned. We created a new test calculateRowTotalWithNegativeColCount() to test this functionality and were able to achieve 100% instruction, branch, and method coverage on the calculateRowTotal() method.

## RangeTest

Test Case 3: testCombine_Range1ParamIsNull(),testCombine_Range2ParamIsNull()

combine(range1: Range,range2 Range) is a method that we had around 50% line coverage and 30% brach coverage in our assignment 2. It will in fact return one of the range if the other range is null, so we increase the line coverage to 100% and branch cover to 100% by setting one of the parameter to null in both test methods.

Test Case 4: testScale_FactorSmallerThanZero_ThrowIllegalArgumentException()

scale(range:Range,factor:double) is the method we did not cover in assignment 2. By entering the expected argument, we can only reach 50% line and brach coverage. In this test cases, we enter a factor which is smaller than 0, so the method will throw an exception. Then we reach 100% line and branch coverage

Test Case 5: testShift_shiftExampleRangeBy5AllowingZeroCrossing()

shift(base:Range,delta:double,allowZeroCrossing:boolean) is the base of other shift method in the Range class. Other shift method will call this method with allowZeroCrossing set to false, so the branch coverage would be 50% and the line coverage would be about 60%. We use this test method to call shift setting allowZeroCrossing to true, so it has branch and statement completely covered by our test cases.

# 5 A detailed report of the coverage achieved of each class and method (a screen shot from the code cover results in green and red color would suffice)

---

**DataUtilities Before New Tests**

Instruction Coverage
![DataUtilitiesInstructionCoverageBefore](https://user-images.githubusercontent.com/72403820/222765254-f4f7a707-37f6-453e-9969-08885eef743c.png)

Branch Coverage
![DataUtilitiesBranchCoverageBefore](https://user-images.githubusercontent.com/72403820/222765222-5a890cb3-4239-4f72-9e9f-9e573f5d19fa.png)

Method Coverage
![DataUtilitiesMethodCoverageBefore](https://user-images.githubusercontent.com/72403820/222765322-4a6c6445-44e6-4bff-a6a4-73b0aded85e4.png)

---

**DataUtilities After New Tests**

Instruction Coverage
![DataUtilitiesInstructionCoverage](https://user-images.githubusercontent.com/72403820/222765188-de3e2b0f-88cd-4f9d-8b08-a0cd97ec59b4.png)

Branch Coverage
![DataUtilitiesBranchCoverage](https://user-images.githubusercontent.com/72403820/222765365-7a55d20a-5ac9-40f3-a644-206940972589.png)

Method Coverage
![DataUtilitiesMethodCoverage](https://user-images.githubusercontent.com/72403820/222765339-cb819f77-a310-4d75-ac10-6bd6dcb0e786.png)

---

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
