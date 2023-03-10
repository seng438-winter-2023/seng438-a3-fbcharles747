**SENG 438 - Software Testing, Reliability, and Quality**

**Lab. Report #3 – Code Coverage, Adequacy Criteria and Test Case Correlation**

| Group \#:       |     |
| --------------- | --- |
| Student Names:  |     |
| Chun-chun Huang |     |
| Amneet Deol     |     |
| Shreosi Debnath |     |
| Hiten Mahal     |     |

(Note that some labs require individual reports while others require one report
for each group. Please see each lab document for details.)

# 1 Introduction

This assignment is about unit testing using JUnit in Eclipse. We learnt how to use testing tools and then enhance the test suite. This assignment introduced white-box coverage criteria as a technique for deciding which test cases to develop which was something new for us to learn. White-box coverage criteria tests the internal structure of the code. It ensures that all parts of the code are executed at least once during testing, which helps uncover defects. There are different levels of white-box coverage criteria, such as statement coverage, branch coverage, and path coverage. We did all three coverages for this assignment. 

# 2 Manual data-flow coverage calculations for X and Y methods

DataUtilities.calculateColumnTotal

- Data Flow Graph
![IMG_E8C7C0F08807-1](https://user-images.githubusercontent.com/101241102/222871637-c9c8464f-14e8-439d-9db8-4b585c0ee582.jpeg)

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

| var      | D-U pair                   |
| -------- | ---------------            |
| total    | (1,3,8), (1,4,8)           |
| rowCount | (1,2), (1,5)               |
| n        | (2,3), (2,4), (5,6), (5,7) |

- DU-pair coverage: From assignment 2, we only had 1 test: calculateColumnTotalForThreeValues for the calculateColumnTotal method and it has 0% branch coverage because the test case  didn't cover any pairs. 

Range.getUpperBound

- Data Flow Graph -- the CFG in this case
![IMG_A7C91BBE260D-1](https://user-images.githubusercontent.com/101241102/222870797-f08d4eb7-f46b-4148-84ee-b687a627e658.jpeg)

- Def-use sets

| Line | use            | def      |
| ---- | -------------- | -------- |
| 1    | lower, upper   |          |
| 2    | msg, lower     | msg      |
| 3    | upper          |          |
| 4    | msg            |          |


- DU-pairs: 
There are actually no DU pairs because it always executes the same path (regardless of the upper, lower values). 

- DU-pair coverage: 
There are no decisions that need to be made in this method (or conditions) so there are actually no alternative paths so no coverage considerations (it will always execute/follow the same path). We probably should have chosen a different method for this in hindsight.

# 3 A detailed description of the testing strategy for the new unit test

We ran the coverage tool EclEmma for our unit tests from assignment 2. Looking at the metrics for statement coverage, we implemented tests trying to reach 90% statement coverage. As we approached 90% line coverage, our brach coverage also reached 70%.

# 4 A high level description of five selected test cases you have designed using coverage information, and how they have increased code coverage

## DataUtilitiesTest

Test Case 1: cloneTest()
clone() is a new method in DataUtilities that was not present in assignment 2, and so we had 0% coverage for this function. We created cloneTest() and cloneTestWithNull() to provide coverage over this new method and with these new tests were able to provide 100% instruction, branch, and method coverage on the clone() method.

Test Case 2: calculateRowTotalWithNegativeColCount()
calculateRowTotal() is a method in DataUtilities that we had 83% coverage for from Assignment 2. There was one pathway that we were not testing which was when a Values2D with a negative column count is passed in, 0 should be returned. We created a new test calculateRowTotalWithNegativeColCount() to test this functionality and were able to achieve 100% instruction, branch, and method coverage on the calculateRowTotal() method.

## RangeTest

Test Case 3: testCombine_Range1ParamIsNull(),testCombine_Range2ParamIsNull()

combine(range1: Range,range2 Range) is a method that we had around 50% line coverage and 30% brach coverage in our assignment 2. It will in fact return one of the range if the other range is null, so we increased the line coverage to 100% and branch cover to 100% by setting one of the parameter to null in both test methods.

Test Case 4: testScale_FactorSmallerThanZero_ThrowIllegalArgumentException()

scale(range:Range,factor:double) is the method we did not cover in assignment 2. By entering the expected argument, we can only reach 50% line and branch coverage. In this test cases, we entered a factor which is smaller than 0, so the method will throw an exception. This allowed us to reach 100% line and branch coverage

Test Case 5: testShift_shiftExampleRangeBy5AllowingZeroCrossing()

shift(base:Range,delta:double,allowZeroCrossing:boolean) is the base of the other shift method in the Range class. Other shift method calls this method with allowZeroCrossing set to false, so the branch coverage would be 50% and the line coverage would be about 60%. We used this test method to call shift setting allowZeroCrossing to true, so it has branch and statement completely covered by our test cases.

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

## Pros of EclEmma

- Easy installation through the Eclipse extention market
- Allows code measurement with a variety of coverage metrics (line coverage, branch coverage, etc)
- EclEmma highlights the code that has been covered during the testing which allows for ease-of-use

## Cons of EclEmma

- It only measures coverage during testing but it does not give insight to the quality or performance of the code

# 7 A comparison on the advantages and disadvantages of requirements-based test generation and coverage-based test generation.

Most commonly used software testing methods are requirements-based and coverage-based.

Requirements-based testing makes sure that the software meets all the functional requirements specified by the stakeholders. This is useful for high end systems, but can be time-consuming and may miss defects that aren't explicitly defined in the requirements.

Advantages:

1.Ensures that the software meets all the functional requirements.
2.Helps identify gaps or inconsistencies in the requirements and provides valuable feedback.
3.Useful for highly used and high stakes systems where meeting all requirements is essential.


Disadvantages:

1.May miss defects that are not explicitly defined in the requirements.
2.Does not consider any aspects of the software beyond the requirements.
3.Time-consuming and expensive, especially for complex requirements.

Coverage-based testing aims to test the software thoroughly, looking beyond just specific requirements. This can help find defects that aren't covered by the requirements, but it can be difficult to prioritize which parts of the code to test first and there's a risk of generating test cases that aren't useful.

Advantages:

1.Can identify defects not covered by requirements, such as boundary cases or unexpected inputs.
2.Tests software more thoroughly, increases quality.
3.Useful for testing non-functional requirements.


Disadvantages:

1.May not achieve full code coverage, especially in large or complex systems.
2.Can be difficult to prioritize which code to test first, leading to inefficient use of resources.
3.Risk of generating irrelevant or useless test cases.
4.Wastes time and resources.

# 8 A discussion on how the team work/effort was divided and managed

As this lab assignment fell over reading week, 2 members worked on the manual data-flow coverage calculations and graph during the lab session. The test-writing was then split between members of the group in preparation for the demo. We checked each other's work for the tests and helped to increase the coverage and also collaborated on finishing the report. 

# 9 Any difficulties encountered, challenges overcome, and lessons learned from performing the lab

A couple of members in the group had initial issues setting up the system from assignment 2, especially with the package locations, but once that was figured out, it was not too complicated. We did also have issues reaching the 90% statement coverage due to the unreachable sections of code, but achieved 89.9% in the end. We all learned a lot about the coverage tools as well and realized how impactful unreachable code can be on your coverage. 

# 10 Comments/feedback on the lab itself

We enjoyed working on the lab and building off of the tests written in assignment 2. It was especially interesting to see the initial coverage that we had from assignment 2 and how much we could improve through the added coverage testing. It really helped to better conceptualize how much effort goes into comprehensive testing as a whole. 
