## Fundamentals of testing (Week 1)

### Explain why testing is necessary by giving examples

Testing is necessary due to the single reason that everybody makes mistakes, and no software is made without any bugs. The problem with those bugs is that they will make programs run in a way in which it were not meant to run. Sometimes those bugs can be insignificant but at other times they can be really dangerous. An example of one of those times is with the launch of the rocket Ariane 5 back in 1996. Here the rocket was launched and had to self-destruct after only 37 seconds of flight. This was due to software that was reused from the rocket Ariane 4 and it was assumed that it would work for the Ariane 5 rocket as well. That assumption cost 500 million dollars. The reason for the failure of the flight was due to a 64-bit floating point number being converted to a 16 bit signed integer and therefor causing an integer overflow. 

Here are 7 important reasons to do software testing:

- Software testing is really required to point out the defects and errors that were made during the development phases.
- It’s essential since it makes sure of the Customer’s reliability and their satisfaction in the application.
- It is very important to ensure the Quality of the product.  Quality product delivered to the customers helps in gaining their confidence.
- Testing is necessary in order to provide the facilities to the customers like the delivery of high quality product or software application which requires lower maintenance cost and hence results into more accurate, consistent and reliable results.
- Testing is required for an effective performance of software application or product.
- It’s important to ensure that the application should not result into any failures because it can be very expensive in the future or in the later stages of the development.
- It’s required to stay in the business.

### Explain the difference in meaning between the root cause of a defect and its effects

Lets assume that we ran into the problem that a printer kept failing to print out the jobs that was queued up for it. There could be a lot of reasons for this including: 

- Printer driver software fails.
- Printer runs out of supplies.

If we assume that the problem is that the printer runs out of supplies then the root cause of the problem could be that no one is responsible for checking the paper/ink levels of the printer. It could also be that some of the staff didn't know how to change the ink cartridges. So there is two possibilities for a root cause, and the effect of that would then be that the printer can't print.

### Explain the common objectives of testing

The most common objectives of testing are:

- Finding defects which may get created by the programmer while developing the software.
- Gaining confidence in and providing information about the level of quality.
- To prevent defects.
- To make sure that the end result meets the business and user requirements.
- To ensure that it satisfies the BRS that is Business Requirement Specification and SRS that is System Requirement Specifications.
- To gain the confidence of the customers by providing them a quality product.

### Provide examples for the objective of testing in different phases of the software life cycle

Read [this](http://istqbexamcertification.com/what-is-software-testing-life-cycle-stlc/) for more information.

There are six phases in the Software Testing Life Cycle

- Requirement analysis
- Test Planning
- Test cause development
- Environment Setup
- Test Execution
- Test Cycle Closure 

Each step has an entry criteria, a set of conditions that should be met before starting the software testing, as well as an exit criteria, a set of conditions that should be completed in order to stop the software testing, where we can determine if we can move on to the next phase of the life cycle or not.

##### Requirement analysis

In this phase the testing team goes through both functional and non functional requirements in order to identify the testable requirements. Activities that should be done in this phase are:

- Analyzing the System Requirement specifications from the testing point of view
- Preparation of RTM that is Requirement Traceability Matrix
- Identifying the testing techniques and testing types
- Prioritizing the feature which need focused testing
- Analyzing the Automation feasibility
- Identifying the details about the testing environment where actual testing will be done

The outcomes of this phase are:

- Requirement Traceability Matrix (RTM)
- Automation feasibility report

##### Test Planning

This phase starts after the completion of the requirement analysis. In this phase a test plan, and test strategy documents will be prepared, and from those documents a test effort estimation will also be made. Activities in this phase are:

- Estimation of testing effort
- Selection of Testing Approach
- Preparation of Test Plan, Test strategy documents
- Resource planning and assigning roles and responsibility to them
- Selection of Testing tool

The outcomes of this phase are:

- Test Plan document
- Test Strategy document
- Best suited Testing Approach
- Number of Resources, skill required and their roles and responsibilities
- Testing tool to be used

##### Test Case Development

In this phase test cases are written. If automation is required, scripts are also written to do that. Verification of the test cases and the scripts are done by other people. Activities in this phase are:

- Creation of test cases
- Creation of test scripts if required
- Verification of test cases and automation scripts
- Creation of Test Data in testing environment

The outcomes of this phase are:

- Test cases
- Test scripts (for automation if required)
- Test Data

##### Test Environment Setup

In this phase the setup of software and hardware required for the application is setup. Activities in this phase are:

- As per the Requirement and Architecture document the list of required software and hardware is prepared
- Setting up of test environment
- Creation of test data
- Installation of build and execution of Smoke testing on it

The outcomes of this phase are:

- Test Environment setup is ready
- Test Data is created
- Results of Smoke testing

##### Test Execution

In this phase the test cases are executed in the testing environment. Activities in this phase are:

- Execution of Test Cases
- Reporting test results
- Logging defects for the failed test cases
- Verification and retesting of the defect
- Closure of defects

The outcomes of this phase are:

- Test execution Report
- Updated test cases with results
- Bug Report

##### Test Cycle Closure

In this phase the members of the testing team will meet and discuss about the testing artifacts. The intention of this meeting is to learn lessons from bad practices that can then be avoided in future projects. Activities in the phase are:

- To evaluate the test completion on the basis of Test Coverage and Software Quality
- Documentation of the learning from the project
- Analyzing the test results to find out the distribution of severe defects
- Test Closure Report preparation

The outcome of this phase is:

- Report of Test Closure

### Explain the difference between testing and debugging

Testing is done to find defects in software code, whereas debugging is done to fix those defects.

So a tester may run a test suite and find that some method is not returning what is expected. That means a defect is found in the software. This may lead to a developer debugging said method to figure out why the defect happens, and then fix it.

### Explain some of the seven principles of testing

Read [this](http://istqbexamcertification.com/what-are-the-principles-of-testing/) to learn more

The seven principles of testing are:

- Testing shows presence of defects.
- Exhaustive testing is impossible
- Early testing
- Defect clustering
- Pesticide paradox
- Testing is context dependent
- Absence of errors fallacy 

##### Testing shows presence of defects

Testing can show that defects are present but they can't prove that there are no defects. Testing will always reduce the number of undiscovered defects in the software, but even if no defect is found, it's not a proof that there are no defects present in the software.

#####  Exhaustive testing is impossible

It's not possible to test everything. So instead of trying to test everything, risk and priorities should be used to focus testing efforts. As everything can't be testing accessing and managing risk is one of the most important activities for testing in any product.

#####  Early testing

Testing should start as early as possible and should be focused on defined objectives.

#####  Defect clustering

A small number of modules will contain most of the defects, and will show most operational failures. 

#####  Pesticide paradox

If the same kind of test is repeated the same set of test cases will not be able to find new bugs. To overcome this “Pesticide Paradox”, it is really very important to review the test cases regularly and new and different tests need to be written to exercise different parts of the software or system to potentially find more defects.

#####  Testing is context dependent

Testing is basically context dependent. Different kinds of sites are tested differently. For example, safety – critical software is tested differently from an e-commerce site.

#####  Absence of errors fallacy 

If the system built is unusable and does not fulfil the user’s needs and expectations then finding and fixing defects does not help.



###  Explain the characteristics of good testing that applies to all stages of the testing life-cycle

There are different types of development life cycles like the waterfall model, the V model, the iterative model and of course the agile model. Each of these different life cycles has different testing life cycles that goes hand in hand with the development cycle. e.g. The V model has a face where you plan the different testing faces and testing cases together with the planning of the system, this is called the verification stage where you verify the requirements through describing the tests for set face. The when you come to the development cycle you then start by doing unit tests, integration test and so forth. Its actually a bit like with the agile model even though it is not possible to go back through the faces of the development to change things that a further up the life cycle stream, like the problem with the waterfall model. Then you have the agile model where you do TDD which means that you actually build your system upon tests which then can be specified during the planning and development. The important thing is to know which development life cycle is used in order to do the correct corresponding testing life cycle. But common for each life cycle is that there are some good characteristics of testing which applies to all cycles which are stated below

- for every development activity there is a corresponding testing activity;
- each test level has test objectives specific to that level;
- the analysis and design of tests for a given test level should begin during the
  corresponding development activity;
- testers should be involved in reviewing documents as soon as drafts are avail
  able in the development cycle



###  Explain the major objectives of the different test levels:

- **Unit testing/component** testing: This is where each unit is tested independently down to a method receiving an input and the returning the correct output. This is in agile development done through TDD. The test cases can implement equivalence partitioning and boundary value analysis.

- **Integration testing:**  This is testing interfaces interacting with each so when a component has been created we test whether it works properly with the other components. It can also be system integration test which can be carried out after system testing and includes testing communication with other systems. There are two approaches to integration testing, continues integration where small 'chunks' are added and tested against the each other, the problem with this approach is that it will demand stubs and mocks to be created in order to simulate system behavior.

  • Top-down: testing takes place from top to bottom, following the control flow
  or architectural structure (e.g. starting from the GUI or main menu).
  Components or systems are substituted by stubs.
  • Bottom-up: testing takes place from the bottom of the control flow upwards.
  Components or systems are substituted by drivers/mocks.
  • Functional incremental: integration and testing takes place on the basis of
  the functions or functionality, as documented in the functional specification.

   The other is 'Big Bang' where every component/interface is assembled simultaneously and then tested as a whole. This is very risky as it will be very difficult afterwards to narrow down and find the error. The reason to choose this approach is that it will not require you to create simulated stubs and mocks in order to do tests. 

- **System testing:** This has to do with testing the system as a whole. When all the components are done and integration test have passed then its time to test the whole system against the initial requirements specified by the customer. Theses tests has to do with both functional requirements which are the basis of the afterwards acceptance testing and non-functional requirements, where we check if the system is fast enough, whether the GUI is intuitive enough etc. If all the requirements have been met we are able continue to the last step.

- **Acceptance testing:** This is the final stage, where the customers gets the product and test it to verify that it meets the requirements that he gave. In an agile environment this should not be as thorough a test as with a waterfall model, as the customer has been close in contact with the development team to test the small parts as they have been produced, and is already well aware if it meets the requirements or not, but of course a test of the final product is in order. 

### Explain the four test types:

- **Functional testing:** This has to do with functionality specified in the requirements. Does the application fulfill the functionality the customer asked? If not then it has to be changed.
- **Non-functional testing:** This has to do with test that are not focused on the functionality, but on things like the ease of use of the application, the visuals, the performance and the security. These things can also be part of the requirements from the customer but does not have to do with the program have the right functionality.
- **Structural testing:** Has to do with looking at the code and verifying the structure of it and the coverage of the code being tested which is also referred to as code coverage. This can be done with various tools to check how much of the code has actually been tested.
- **Change related testing:** This is confirmation tests, where we confirm that a fault in the system has indeed been corrected and fixed. Or regression test when we add new components and functionality to the system we want to insure that it did not break any of the other functionalities of the system. So the difference is that the confirmation tests has to do with failing tests being run again to see they will pass, and regression tests has to do with former passed test being rerun to verify that they still pass.

### Identify and describe relevant non-functional tests from one of your exercises during the course

See the project as we had non functional testing of the database using JMeter to see which of them performed fastest.

### Describe the purpose of regression testing

As explained before. Regression tests has to do with functionality that has passed already, and when you introduce new functionality you would like to rerun the same tests to verify that the tests still pass and that the new components did not break any of the old.

### Compare maintenance testing (testing an existing system) to testing a new application with respect to test types, triggers for testing and amount of testing

If an applications has been developed with a correct testing life cycle you should hopefully have a lot of test cases and automated test scripts created already. So when checking with maintenance it could be regression test to ensure that addition to the existing system did not break other functionalities. Or it could be that a user/customer has reported an error. In the latter case you would have to try to identify which parts of the system could have caused the error and then write new test cases to address the problem. Then you would go through a debugging face where you would narrow it down either with a button up- or a top down approach.

### Describe tools which can support test activities at the various test levels in the V-model. You may demonstrate one or more tools. 

- User requirements can be added as issues in a development version control application like GitHub - see our issues in the project.
- Requirements evaluation test / system test can be done with Selenium which does end-to-end testing of the application or you can do exploratory testing. But API testing with something like Rest Assured is better as end-to-end test can be cumbersome.

### Describe test roles and test organization in a V-model system development project.

As with agile development, the V-model want's to tie the tester to the development as soon as possible, so they can both contribute with their knowledge and start of with defining and analyzing their testing life cycle. So the testers role is already in effect before any development is done. Here there will be done an evaluation of the BRS (Business Requirement Specification) and the SRS (System Requirement Specification). And along the different faces of the software development life cycle the testing life cycle creates analysis, documentations and creates test cases alongside. When the development is undertaking we then afterwards test the components, integration, system and finally the requirements using the artifacts created during along with the planning and execution face of the software development life cycle.

### Describe strengths and weaknesses of the V-model. What are the alternatives?

The good thing with the V-model as a continuation of the waterfall model is that you now use the expertise of the testers and include them in the development process, it also makes it possible to address possible issues that may arise during before starting to develop. The problem is that it still executes the steps sequential, so things that was not discovered during the initial analysis and planning face will be of concern when having to execute the tests, and the possibility of going back and correcting these mistakes are just as expensive as with the waterfall model. As we can see in the traditional cost of change curve it is still expensive to change the program later

![Cost of change](http://agilemodeling.com/images/costOfChangeTraditional.gif)

So this approach relies on the humans involved with the analysis to predict the future, which is impossible. So a better approach would be an agile- or iterative model where you have the different phases overlapping. So you would do testing along side the development and then be able to discover errors before continuing to develop new components. Thereby lowering the cost substantially.

Kent Becks agile cost of change curve:

![Agile cost of change curve](http://agilemodeling.com/images/costOfChangeBeck.gif)

