## Test case design (week 3)

### ● Point out the main differences between white box and black box tests

White-box and black-box testing are both **dynamic techniques,** meaning they're techniques that actually execute the code and observe the results of certain inputs. White-box testing is a **structure-based** technique, and black-box testing is a **behavioral technique.**

**Black-box testing**, or **input/output testing** is a testing technique that views the product as a blackbox, a product with no viewports or anything that provides insights into its inner workings, and only provides input and output. It's a testing technique wherein the tester has zero knowledge of the inner workings of the product, only what they can input, and the output they are given as a result of their input. It's a behavioral form of testing, that focuses on the product's behavior, instead of its mechanics. **Black-box testing** is used for both **functional** and **non-functional** testing. An example of this would be either something like **UI/End-To-End testing,** for example like our **Protractor E2E** tests on the front-end.

**White-box testing** is the opposite of black-box, in that it focuses on the internals of the product. It's also called **glass-box testing**, referring to the fact that the product's internals are completely visible for the tester. It is less concerned with the functionality of the software, and more with the integrity of the mechanics of the software. White-box is what's thought of when performing **unit/integration tests**, as they specifically target pieces of code in the software to test and measure.

Basically, the difference is the amount of knowledge the tester has about the system as a whole. Black-box gives the tester the front-facing client to interact with, allowing them to measure input/output, but nothing more, whereas white-box techniques have full access to the internals and code of the system, allowing the tester to very specifically test parts of the system, perform component testing, and measure test coverage.



### ● List a few of the elements that a high quality test case in your opinion is comprised of

To start with, a test case needs to have its purpose explicitly stated, and should be directly traceable to its test basis. You need to be able to see why it's there, what it does and how it does it, in case specifications change or the functionality changes, such that you can make changes to the test case and have it remain valid.

Figure out assumptions before executing the test. If you run the test, analyze the result, and design your assertions from that, you're usually not certain if what you're asserting against is actually correct. If you're not certain of what the result of a test case *should* be, then refer to a test oracle for information on the intended behavior of the functionality you're testing. Especially relevant when performing test-driven design, as you need to be clear on what the functionality should be doing before you start coding it.

Attempt to make test cases that can cover several test conditions. Along with using dynamic test design techniques like boundary analysis and equivalence partitioning, you generally want to write test cases that can cover several conditions at a time, such that you generate code coverage more effectively and reduce the amount of test cases you need to create.



### ● Elaborate on the role of oracles and their usage with regards to test cases

A test oracle is a resource that can inform you of the intended output of a function or method, such that you're clear on what assertions you should be making. When writing test cases, if you're unsure of what your assertions should be, or you're just unclear on what the function you're testing is actually supposed to do, you need to refer to a test oracle to confirm what the intended behavior is, such that you write your test case correctly.

A test oracle can be anything from documentation about the system such as a requirement specification or code documentation, it could be a domain expert who you could ask about the intended behavior, or really anything else that can clearly explain to you what a function is supposed to do, so you can check whether it does it correctly or not.



### ● Explain the overall focus and important considerations in relation to the test analysis process

The overall focus of the test analysis process is fairly simple; examine the system, identify components that could be potential vectors for defects, gather information about those components, and then create a test basis from that information, from which you specify test conditions and test cases.

Important considerations depend on which part of the analysis process you're in. When analyzing the system and trying to decide on specific test bases to focus on, you should use qualifiers such as risk analysis, requirement specifications, expert knowledge and other forms of documentation for establishing what the system is supposed to be capable of, and then taking these intended functionalities of the system and using those as your basis.

When creating test conditions for every test basis, we analyze the basis, and identify everything that the basis should be capable of. For example if we have an age gate as our test basis, we'll have conditions detailing that the age gate should not be able to accept non-numerical input, the numerical input has to not be negative or overly large, it should generate different output depending on the age you put in, stuff like that. Exploratory testing is a good way to make sure that you're considering every angle of a functionality, even ones that haven't really been considered when the specifications were written, such that you're sure that you have considered every condition possible.

When writing test cases, you want to attempt to make test cases that can cover several test conditions. You generally want to write test cases that can cover several conditions at a time, such that you generate code coverage more effectively and reduce the amount of test cases you need to create.



### ● Explain what has to be done during the test design process and what the result of it is

During the test design process, before you start to actually design tests, you need to decide on which test techniques to use. Each individual technique is aimed at uncovering specific types of defects, so picking some and leaving out others can potentially cause some defects to remain unnoticed. The choice of techniques to use usually depends on a lot of things, such as risk analysis, time and budget, the experience and technical knowledge of testers and developers, regulatory standards and the like. You can also just paint broadly and then focus on some techniques more than others, in case you find that some techniques will be more applicable to the development you're performing.

During the test design process, you then take the techniques you've chosen, and put them into use with formal application. You decide on rules of how to apply the techniques, allot development time to preparing and using them, and make sure that the tests designed during the process are properly documented, such that they have proper traceability.



### ● Explain which tasks to carry out and decisions to take in the test implementation process

Not entirely sure what this is supposed to mean exactly, but I figure it's about actually taking the tests you've made during the design process and applying them.

When writing and preparing the tests themselves, making sure to properly document them and annotating them such that their purpose is clear is important, as it provides traceability. The tests should be as concise as possible, while still fulfilling their purpose of asserting that a functionality functions as it should. Make sure to make proper use of test oracles so that assertions are correct. Create test scripts and procedures, such that the tests can be executed in an efficient, quick manner, so as to save as much time as possible when testing the software. 

### ● Account for some general aspects concerned with test (design / case / procedure) documentation

The test **procedure**, or test plan/script, is the documentation that outlines the overall testing strategy. It includes the test cases intended for the application, along with explanations for which features the test cases are testing and the intended purpose of those features, the fixtures and resources required to perform these tests, which tools to use, along with the scheduling of the testing activities outlined in the document.

The **design** of the test cases should be thoroughly documented in order to provide proper traceability. If a test basis is to be changed at some point, the decision processes for designing the test conditions and cases should be easily understandable, such that they can be changed to reflect the changes in the test basis without having to do too much time-wasting research. Clear documentation such as with decision tables, state transition models and boundary value tables create a very clear understanding of the intended functionality of the application, and care should be taken that they're created and maintained.

Test **case** documentation follows much of the same documentation guidelines as the design processes, but with more granularity. Test cases should be individually labeled, should explicitly state their purpose, the version history of the test case and the version history of the application when the case was created, and then clear statement of its assumptions, pre/post-conditions, the steps taken in the test case to perform it, and then both the expected outcome and the actual outcome.

The entire purpose of proper documentation is traceability. There's a term called the **Requirement Traceability Matrix - RTM,** whose purpose is to facilitate forward tracing, which is tracing how requirements should be translated into design and code, and backwards tracing, which is tracing back the design and code to the requirements. The goals are: 

- Make sure the software is developed as per the mentioned requirements.
- Make sure the software helps in finding the root cause of any bug.
- Make sure the software helps in tracing the developed documents during different phases of the development lifecycle.



### ● Describe how the techniques equivalence partitioning and boundary value analysis are applied in test case design and outline the reasons for using each technique

Read notes on Equivalence Partitioning and Boundary Value Analysis in the "Test case design (week 3) Notes" document.

Equivalence Partitioning and Boundary Value Analysis (EP/BVA) are used in test case design in order to make both the design and implementation process more efficient. EP is a technique used to cut down on the amount of test cases needed, built on the assumption that you can group certain sets of inputs into partitions that, if one of the inputs from a partition passes, then the others should logically follow suit, cutting down on the amount of tests required. It saves a ton of time in the implementation phase, as it cuts down dramatically on the amount of individual tests that need to be performed. 

BVA is used in conjunction with EP, both in order to more accurately define the individual partitions by defining specific boundaries, and to further ensure that the partitions can be assumed to be truly equivalent, such that if we test one condition from a partition, we can assume all conditions in the partition would behave the same way. It does increase the amount of test cases made somewhat, but it's a good way to ensure that specifications are followed, and gives a much more significant feeling of stability when presenting it to stakeholders.

### ● Describe the benefits of decision tables and state transition models in the context of test case design

Decision tables and State Transition Models are great tools to use in order to not only gain a much clearer understanding of how the software works, but also as a great guideline for designing test cases. In the case of decision tables, they're a very clear, concise form of figure that can be basically directly translated into test cases, as they outline exactly which pairings of conditions to test, and what the outcome of them should be. It's a pretty great kind of document to use as a test oracle, as it details both the intended input and output of a transaction.

Much of the same goes for state transition models, which are also a very clear, graphical representation of the input and output of a program with regards to its state changes. In its graph form, it's quite easy to sketch up on a whiteboard, and can then be translated into a state table to give something reminiscent of a decision table, which as mentioned before, is very useful in defining test cases and the assertions that should be made in each case.



