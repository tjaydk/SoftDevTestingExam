### System testing, Exploratory Testing, Automated system testing (Week 7 and 8)

**Define the term System Testing and it purpose, both in terms of the old-fashioned V-model and in an agile context**

System testing is when you do tests of the produced application/product. It is hold up against the use cases and requirements given by the customer. The system test applies to the 2nd, 3rd and 4th quadrants of the testing quadrants. And is done in order to assure that the product lives up to the customers expectation. It is done as one of the last things in the development cycle and is usually done by an independent team of testers or in some cases an external team. It tests both functional  and non-functional requirements. As the tests shall give confidence that the product is useful for the customer it should be done in a controlled environment that is as close to the final product environment as possible.

In the v-model it is 2nd depth and is across of the production of system requirements, so it comes fairly late in the process in old school development.
![V model](http://testingfreak.com/wp-content/uploads/2015/01/vmodel.png)

**Explain the "kind of tests" that often are associated with System Testing and the difference between functional and non-functional testing**

System testing is usually associated with specification-based 'black box'/input-output testing using artifacts like use cases defined by the customers or decision tables which can be used to evaluate business rules. It is done to ensure the development is living up to the requirements and expectation of the customer. It is focused on both functional and non-functional requirements. It gives a confidence in the product living up to the described requirements created by the customer. If these test fail then it will have to do with, not a defect system, but a wrongly developed system. Besides the black box test you can also use structured white box test to e.g. test the navigation of a web application etc.

Here is an example of a decision table:

![Decision table](http://5nb3f3r0gfd3fhztnfeqg9yv.wpengine.netdna-cdn.com/wp-content/uploads/2012/06/1.png)

**Who is (often) carrying out the System Test (would your answer be the same for an organization following the old-fashioned v-model versus a modern agile organization?)**

As said before the system test are usually done be a test group or a external testing company. This has to do with the fact that the black box tests are focused on the behavior of the system and not with the code per se, so it would be best for people who doesn't know the structure of the program to actually test it without being influenced of the code it self, but only concentrating in trying to use the application as it is intended to be used and thereby insure that the requirements are met. In the old V-model you would have the system test just before the UAT (user acceptance test) and it would sometimes be done by the programmers themselves as they have already finished the programming part and is now in the testing face, but usually these programmers are specialized in writing code, and not tests. In an agile organization the system test can also come earlier as a part of a continuous integration work flow. 

**What is often (and why) performing system tests?**

System test can be performed by a CI (continues integration) environment, because a CI environment can be set up to simulate the real time environment that the application will be running in when in production. And as it is possible to create the system integration test early and use mocks and stubs to simulate the missing parts it is possible to, in an early stage, begin testing the system against the requirements. It is also a good idea to automate these tests as it will ensure that you have the requirements stated early, and they are know by the whole development team. Each time they submit new features to the application they will be notified if whether or not the system lives up to expectation. Early tests will help keep people on the right track. System test can also be manual test, like exploratory testing to ensure both functional and non functional requirement. Behavior driven development is a good way to generate test cases, by focusing solely on the behavior of the system and not on the code itself. 

**What is the difference between System and Acceptance testing**

One of the major differences between system testing and acceptance testing is the fact that the system testing is being done by testers who have knowledge of the different tools like CI, Selenium *(front end testing tool) etc. And is done with the intent to ensure that the product is ready for delivery. It would not be a good start of a delivery to a customer, if the customer starts out with spotting missing parts of the application. The acceptance test is done primarily done by the customer or end user. In this stage, hopefully all the errors and missing parts have been found and solved by unit and systems testing, and now we just need the customer to say good for the product. So the user will in this face check against his initial wishes for the product, if said wishes are met. Hopefully the customer will be satisfied, and if all the requirements are met, then the developers can get paid. Acceptance testing is also purely functional testing.

**Discuss Pros and Cons with manual versus automated tests**

One of the good things about automation is that it can be done before you even start to code. If you know the requirements you can already start to write tests for it, and then as you move along with the production you can easily and fast get a response if your code is working as intended. The bad thing about automated test are that they can give you false confidence. If the test are poorly written our maybe even testing things wrong e.g. an equivalence partitioning test that has incorrect assertions - it will then result in some errors not being discovered, whereas a manual test usually tend to vary, and maybe by a manual test not being done in the exact same way as last time will result in undiscovered errors surfacing. But overall you should have a combination of automated test that can ensure a fast working pace, and help keeping an overall goal when coding, plus being possible to use as documentation. But also have you occasional manual test just to try different approaches and discover new parts which you can the write automated test for afterwards.

**Explain about Mike Cohn's Test Pyramid and why it's relevant for test planning**

![Test pyramid](https://martinfowler.com/bliki/images/testPyramid/test-pyramid.png)

The pyramid was an illustration by Mike Cohn in the book 'Succeeding with agile', and describes how you should have many more low level test like unit test rather than heavy end-to-end tests. Both because they are very fast to run and can ensure that each unit performs as it should, so as long as you have understood the requirements right it should be the right thing that you are building, and in the other face is that it is very cheap and fast to write the unit test, whereas UI test can demand you having to use very expensive tools to run the automated tests, they can be very cumbersome to setup and usually shouldn't discover anything not discovered already in the lower level tests. 

**Discuss some of the problems with automated GUI tests and what makes such test "vulnerable"**

You can automate GUI test by using tools like Selenium or record/playback tools where you can browse your application, record it and the play it back to produce the same result and thereby automating the UI tests. But when it comes to test like Selenium it can take alot of time writing the test, and it could easily end up being a simple test which won't really discover anything, or be so complex that if the application is changed it would be a very expensive strategy as you would have to rewrite the whole test case to e.g. use a whole new UI. These kind of end-to-end test are vulnerable, and you should rather do API testing and then do unit test of your UI like Jasmine for a javascript UI. Again we are back to the pyramid, stating the much more beneficial approach in low level unit tests.

**Explain about the Selenium, its purpose, and how it "fits into" the testing world**

Selenium is a GUI automation testing tool for web applications which can simulate the behavior of a user interacting with the system, these kind of tests are called end-to-end tests as they test the final system against the UI which will then include the whole system, like the database etc. These test has to be written as sequential tests that resemble the navigation and interaction with the system. They have the problem that they will stop if something goes wrong, and not be able to discover other failures before the first are fixed as it would have to continue the process with faulty data. It is not the best way of doing test, but can be a good tool in cases where you have to fill out a long form, and instead of filling out the data over and over again you can use this tool. Again for testing the system it would be better to do unit tests, api test etc. 

**Demonstrate, using practical examples, how you have tested Web-UI's using Selenium.**

**Explain the difference between a Headless browser, versus a GUI-based browser, and the pros & cons of each**

Headless browsers are frameworks that imitate a browser but does not display a GUI but are handled through a command line interface or a network communication. They are quicker to execute, and can therefore be used to simulate a lot of different browser types for doing cross platform, and backwards compatibility testing. A GUI-based browser test will force you to have the browser installed on your system, and as there are different features in the different versions you are not able to ensure functionality without testing your system on different browser manufactures and versions. The good thing with the GUI-based browser is that you can see the test perform, even if they run fast. But it will make it easier to discover if you have an error in your test. A good approach would be to write a Selenium test using a GUI based browser to ensure its correctness. When it is working as intended you will then switch to a headless browser test to run multiple test. Sauce Labs is a framework delivered by Travis which easily lets you add your Selenium test to your CI.

**Explain the problems we face when testing modern AJAX/JavaScript applications and demonstrate, using practical examples, how you have solved them**

The problem with applications that depend on AJAX (asynchronous JavaScript and XML) is like when your testing multi threaded systems, as you are not able to predict the order in which tasks are performed. This means that you would either have to develop you system to execute tasks within callback functions to ensure sequentiality or you would have to use stubs instead.  

