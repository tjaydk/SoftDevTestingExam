## Test case design (week 3)

### Test Conditions & Designing Test Cases

**Formal and informal testing.** Formal has a lot of documentation, is very specified, informal is usually not documented, not planned extensively. Formality is dependent on the product, since testing is context-dependent. 

**Test basis** is the thing that a specific test is based around, it could be a process, a technical specification, system requirement, the code itself for structural testing, etc. The **test condition** is the specific thing you're testing from that test basis. For example, the **test basis** could be that we want boundaries on a function, and the **test condition** would be the outcomes of testing it, such as does it throw an exception or not. The testing conditions should be a wide net, as we want to make sure we're not causing a **pesticide paradox,** by having a narrow focus that overlooks other defects. 

Test conditions should be **traceable**, meaning that you can trace them back to the test basis, so you know what the condition's relevance is to the test basis. This is relevant in case the test basis changes, such as changes in the requirements, changes in the codebase, etc. Now the test conditions need to be changed, and you can only properly change them if you understand their relation to the basis. It also becomes relevant if tests suddenly start failing, so you can trace back where the defect may lie.

For every test condition, we need a certain amount of **test cases.** The test cases need to be very specific, as they need to be applicable for both the basis and the condition, and also because we're testing against something very specific that needs to behave in a very specific way. It's *greatly* recommended that when designing a test case, that you should figure out the expected result of the test before you run the test. Testing something, seeing what comes out, and then designing your assertions through that is risky, as you can't always be sure if the results of the first test were actually correct or not. You need a **test oracle**, a source of information about the system that details exactly what should be happening. This could be requirement specifications, code documentation or the like. Test cases should also have an explicit reason for existing, so you can perform prioritization of the test cases, especially when handling risk analysis and risk-based testing.

**Test scripts** are documents that detail the **test procedure,** or how and in which order a suite of tests should be run. It could be that there's a set of tests where they need to be run in a specific order for them all to be able to function, such as sequential CRUD operation tests. These differ from **automation scripts,** or **automated test procedures,** which are automated test scripts written in programming languages that a tool can interpret. A collection of test scripts are grouped into a **test execution schedule,** which is basically a superscript of how and in which order to run each test procedure. 



### Test Design Techniques

**Test techniques** are processes that allow the testers to properly choose which tests to create out of a set of all possible tests, since exhaustive testing is unfeasible. There are two main categories of testing techniques; **static and dynamic.**

**Dynamic techniques** consist of **specification-based, structure-based** and **experience-based.** **Specification-based** covers techniques such as **black-box & behavioral techniques,** **structure-based** covers techniques such as **white-box & structural techniques.**

**Static testing** involves not executing the code being examined, and instead reading through it to identify potential flaws. This is usable in code reviews, along with testing any other sort of document, such as design documents, models, functional specifications and requirement specifications. It's a non-execution method for identifying potential defects before taking them into use.

**Black-box testing**, or **input/output testing** is a testing technique that views the product as a blackbox, a product with no viewports or anything that provides insights into its inner workings, and only provides input and output. It's a testing technique wherein the tester has zero knowledge of the inner workings of the product, only what they can input, and the output they are given as a result of their input. It's a behavioral form of testing, that focuses on the product's behavior, instead of its mechanics. **Black-box testing** is used for both **functional** and **non-functional** testing. An example of this would be either something like **UI/End-To-End testing,** for example like our **Protractor E2E** tests on the front-end.

**White-box testing** is the opposite of black-box, in that it focuses on the internals of the product. It's also called **glass-box testing**, referring to the fact that the product's internals are completely visible for the tester. It is less concerned with the functionality of the software, and more with the integrity of the mechanics of the software. White-box is what's thought of when performing **unit/integration tests**, as they specifically target pieces of code in the software to test and measure.

**Experience-based testing** focuses less on the approach to the product, and more on the experience and expertise of the testers themselves. It leverages the fact that testers, developers and businesspeople all have different experiences, and makes use of that expertise to assure that test cases and conditions are properly designed. Having a wide variety of experiences in a development team ensures that several angles are considered, as different experiences and competencies will inevitably lead to different viewpoints and approaches to how to use the product, and how the product could potentially be defective. An example of this approach is **exploratory testing.**

### Specification-based/Black-Box Techniques

Specification-based techniques include **Equivalence Partitioning/Boundary Value Analysis, Decision Tables, and State Transition Testing.**

#### Equivalence Partitioning

**Equivalence Partitioning** is a black-box testing technique based around partitioning sets of test conditions together in groupings wherein the conditions are considered 'equivalent', or in where the test conditions should be handled by the system similarly. These are called either **equivalence partitions** or **equivalence classes.** The idea is that the different test conditions should be handled equivalently, such that you can run a single test from each partition, and safely assume that the rest of the conditions in that partition would behave similarly. If one partition passes, then all conditions in that partition can, generally, be assumed to also pass.

An example of this would be creating test conditions for an age gate. Say we have an input field where we ask for the age of the client, and only allow access to the product if the client is above 18 years of age. We then have several test conditions we wish to fulfill; we want to make sure that if you're under 18, you don't get access, and if you're over 18, you get access. You could potentially also create conditions that disallow age inputs below 0. 

![](https://i.imgur.com/dkHGy4B.png)

What you would then do is look at these ranges as **partitions.** Instead of creating test cases for every possible age, we create test cases that cover every partition. In particular, we'll create test cases for input below 0, between 0 and 17, and 18 and above. If the test case passes for one of the partitions, we can be reasonably certain that any other test case within the specified range would pass as well.

It's important to cover not just the specified conditions, but the invalid conditions that are not specified as well. For example, we're told that there must be an age gate of 18 years old. We should also create a partition for ages under 0, as it is impossible to be negative age. Similarly, we could also create an upper boundary for age. For example, we can be reasonably certain that no-one over the age of 120 will ever use the system, or at least in the immediate future.

Partitioning like this is a way to cut down on the amount of time spent writing tests. Sure, we could create tests for every possible age, or even just a parameterized test to make it much more efficient, but in reality, we can partition these test conditions and create singular tests for each partition, and be pretty much entirely certain that they cover the entire partition.

#### Boundary value analysis

**Boundary value analysis** is an extension of the boundary checking mentioned in the notes for **equivalence partitioning.** It's a type of range checking, and is usually done unconsciously, but as with EP, BVA is also much more effective if taken into conscious usage. 

![](https://i.imgur.com/o8QUtik.png)

BVA is taken into use when working with functionalities that take input inside of a specific range. It's an extension of EP, in that it accurately specifies wherein the boundaries for a given partition are. The boundaries are the lower and upper bound for where an input lies within a given partition, and it is **up to and including.** So for example, if a new partition begins at input 1000, then the upper bound for the partition prior to it would be 999.99.

BVA is a way of making EP a little more precise, but without going overboard. Whereas we test an arbitrary test case in every partition in EP, BVA requires us to test at least two cases; the upper and lower bounds. If both bounds pass, we can be reasonably sure that every value in between them will pass as well.

**Open boundaries** are the boundaries at the maximum and minimum ends of a boundary analysis table. Usually, you'll want to define some boundaries for these as well. For example for the age range checker; we could simple say that a valid boundary would be 18 and up, but a safer thing to do would be setting an upper boundary such as, for example 120, as we can be quite certain no human being using our product is going to be over that age.

EP and BVA can be used for more than just range checking, and it's up to simply considering how different types of input can be partitioned. For example, if you have a functionality wherein someone can choose different classes of seats in a plane - economy, economy plus, first class - you can lump those into a valid partition, and then create invalid partitions that check for misshapen or otherwise invalid input, for example in case someone finds a defect that allows for customized input, or if data is sent from the GUI incorrectly, such that you can set up effective error handling.

##### Designing test cases

When designing test cases for test conditions, it's smart to attempt to design the test cases such that they cover more than one test condition at a time, reducing the amount of test cases needed to be created. However, when testing invalid partitions, it's usually wise to only cover one condition at once, in case the software throws an exception or otherwise halts operations once a single invalid input has been made.

It is recommended to do tests on both the boundary values and the partition values. For example, if we have a partition with the boundaries 1 and 99, we would test those two boundaries, and a value in between, meaning a value in the partition. This way we can be sure that it is not just the boundaries that work, but the partition itself is functional. 

#### Decision table testing

Whereas EP/BVA testing is focused on specific singular inputs and the boundaries for those singular inputs, **decision tables** are focused on combinations of singular inputs, and the behavior that arises from that. Decision tables are usually quite easy to understand for non-technical employees as well, and could benefit greatly from being worked on jointly with the business side of the project, as they could find it helpful as well.

Depending on the functionality the decision table concerns, the amount of different sets of inputs can be quite large. Depending on the type of testing being done, you would either need to analyze which decision sets to prioritize testing, or setting up automated procedure scripts for them, such as by parameterized tests.

![](https://i.imgur.com/QqMdaCT.png)

For every combination of conditions, true or false for each condition in a given rule, there must be a specified action or outcome for them. It could be a valid response, or it could be an error message, but what is important is that there is a specified outcome for every combination of conditions. The outcomes are **mutually exclusive;** only one outcome can come as a result of a set of conditions.

#### State transition testing

Any system that involves a **finite state machine** can be tested through **state transition testing.** A **finite state machine** means a system wherein, given an input, the output can differ as a result of actions taken prior to the input, meaning the **state** of the system determines the output given.

A fairly simple example is that of a browser. Given a state wherein you have a tab open, you can press a hotkey to close that tab. If you then press that hotkey again, nothing happens, as there are no tabs open anymore. The state of the browser has changed, so the result has changed as well. 

![](https://i.imgur.com/sfB8hku.png)

A **state transition model** has four stages; the states that the software occupies, the legal transitions between two states, the events that cause transitions between states, and the actions resulting from a transition. Creating this model then gives you an oversight of the different states, the transitions between them, and the test conditions that can be designed to cover the state transitions. You can test the singular states and transitions themselves, or make larger test cases between several states and transitions, called 1-switch coverage or 2-switch coverage, depending on how many state switches you perform.

This model does not cover invalid transitions, however. For this, we often want to make a **state table** which outlines the valid transitions, and then empty cells where a transition would be erroneous, from which we can design invalid test cases.

![](https://i.imgur.com/3H5Wbvg.png)



#### Use Case Testing

Use cases are the more non-technical side of defining a test case. It's described from the point of view of the **actor,** the person doing something in the system, and the expected result of those actions. This can be used to uncover integration defects, wherein specific actions should produce specific results. Use cases are also used in agile Product Backlogs, to describe how specific functionalities should result in specific results.

When designing use case tests, you can set up a table for them as well, describing the **main success scenario,** and then rows of **extensions,** meaning actions deviating from the main scenario that should result in specific things.

![](https://i.imgur.com/gkXYjfz.png)



### Structure-Based/White-Box Techniques

Structure-based testing techniques are used primarily for test coverage measurement and structural test case design. This means that structural-based and white-box techniques are used primarily to ensure that there's proper coverage of the software code, and after assessing the amount of coverage the code has, you use the existing test cases to devise new test cases that differ from the existing ones to further improve coverage.

**Structure-based test design**  is the process of analyzing the coverage you have of test cases for your system, and if the coverage is insufficient, you design new test cases designed to cover those parts that have not been covered yet.

#### Test Coverage

An important thing about test coverage is that it is a complimentary technique that focuses on the structures that are already present, but does not cover any defects that come from omissions on specification documents, missing functionality code or the like. Likewise, test coverage doesn't ensure that the system is fully tested. Just because you have a test for a specific piece of code doesn't mean the code is fully tested, because there could be several different types of inputs or the like that haven't been considered. As such, test coverage is taken into use along with experience-based techniques, such that you're sure that you're creating the tests that are necessary, and then using coverage to give a clear overview of your testing plans versus how much testing has actually been performed.

**Statement coverage,** or what we might know as **line coverage** is the measurement of coverage for how many of the statements present in the code are actually tested. If for example we have a function that operates on an *if* statement, we do not have proper statement coverage if we do not activate that *if* statement. It's basically coverage of how many of the lines of code in the system are executed by the tests.

**Decision coverage** is a slightly further version of statement coverage, in that it also concerns making sure you're thorough with making sure that all code is executed and tested. In particular, decision coverage focuses on conditional statements such as *if, while, switch* and the like. Say we have a function with a switch statement; if we don't make test cases such that we activate every case in the switch statement, we have not properly covered that statement. 



### Experience-based Techniques

Experience-based techniques are devised as a more creative approach to testing. We already have plenty of systematic approaches to testing, but being fairly rigid, there are often defects that those approaches will not catch. Experience-based techniques aim to use human creativity, experience and intuition to devise new test cases and uncover defects.

#### Error Guessing

Error Guessing is fairly straightforward, as it revolves around the tester using their experience, technical knowledge and intuition to think of ways to cause errors in the software, and testing towards that. It's a technique that's mostly focused on figuring out the many ways in which a user could interact with the system, the many types of value inputs one could make, or ways in which individual components could interact with each other, that could lead to potential defects.

#### Exploratory Testing

Exploratory Testing is a technique even further based on the tester's own ingenuity, as it's concerned entirely with learning things about the system, and simply taking an allotted amount of time to operate the system in every way the tester can think of. It's basically a type of test where the tester is given an hour or two, and then told to more or less just try to find every single crack, seam and hole in the software that they can, and logging their activities so we can learn of all the defects they uncover in the process.





















