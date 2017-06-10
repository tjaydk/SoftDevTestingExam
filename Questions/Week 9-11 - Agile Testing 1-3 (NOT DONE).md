# Agile Testing 1-3 (Week 9-11)

This cover answers for following questions: 

● Explain about Test Driven Development and how to use it with Continuous integration
● Explain Continuous Integration and principles/tools involved
● Explain why Maven (or similar tools) is a "great" match for CI via a Build Server, and elaborate on
the properties we can take advantage of.
● Explain how to use separate test phases for Unit Tests and Integration Tests with Maven.
● Demonstrate CI, using Travis (or a similar build server), on a system involving, as a minimum:
​	○ Building the project
​	○ Running all Unit Tests
​	○ Running all Integrations test, involving a real database
​	○ Creating Project Reports (Code Coverage, Test Results etc.)
● Explain about Test-Driven Development and its role as a design tool
● Explain how agile development and testing differ from traditional approaches
● Explain the test activities in agile projects, including when which test activities are initiated
● Explain how risk is coped with in agile project as compared to traditional approaches
● Explain the roles and skills of a tester in agile projects
● Explain agile development and testing in the context of the Agile Manifesto’s 4 statements of
values
​	○ Individuals and interactions over 	- processes and tools
​	○ Working software over 			- comprehensive documentation
​	○ Customer collaboration over 		- contract negotiation
​	○ Responding to change over 		- following a plan



### Explain about Test Driven Development and how to use it with Continuous integration

Recommend you look at this article uploaded by Tine: [TDD agile approach](http://agiledata.org/essays/tdd.html)

##### Test Driven Development

Test-driven development (TDD) is an advanced technique of using unit tests to drive the design of software and force decoupling of dependencies. The result of using this practice is a comprehensive suite of unit tests that can be run at any time to provide feedback that the software is still working. This technique is heavily emphasized by those using Agile development methodologies. /wiki

**The TDD Technique described**

The first step is to quickly add a test, basically just enough code to fail. Next you run your tests, often the complete test suite although for sake of speed you may decide to run only a subset, to ensure that the new test does in fact fail. You then update your functional code to make it pass the new tests. The fourth step is to run your tests again. If they fail you need to update your functional code and retest. Once the tests pass the next step is to start over (you may first need to refactor any duplication out of your design as needed, turning TFD into TDD).(TFD, test first development)

**The goal of TDD**

One view is the goal of TDD is specification and not validation.  In other words, it’s one way to think through your requirements or design before your write your functional code. Others views it as a programming technique.

**TDD flow diagram**

<img src="http://imgur.com/hT86gHD.png" width="300" height="500">

**Simple TDD flow**

<img src="http://imgur.com/m5rNS97.png" width="300">



##### Continuous Integration

continuous integration(**CI**) is the practice of merging all developer working copies to a shared mainline several times a day.

With CI we try to tackle the following things: 

- It works on "my" machine but not on B's

- Where should we run the tests?

- When should we run the tests
  ​

Initially CI was conceived of as running all unit tests in the developer's local environment and verifying they all passed before committing to the mainline. Later elaborations of the concept introduced build servers, which automatically ran the unit tests periodically, or even after every commit and reported the results of tests to the developer, like we did with the Gutenberg Project.

CI benefits:

- No integration bugs (/hell)
- Easy to deploy and release
- Frequent integration = fast development
- Constant available working version

**TDD and CI**

Since CI relies on tests, TDD is an good way to create test used as the base build test you run with CI. 

**TDD workflow**

<img src="http://imgur.com/X5KQv79.png" >

### Explain Continuous Integration and principles/tools involved

For CI look in previous question.

**Continuous Integration relies on the following principles**

- Maintain a Code Repository

The convention is that the system should be buildable from a fresh checkout and not require additional dependencies.

- Automate the build

A single command should have the capability of building the system.

- Make the build self-testing

Once the code is built, all tests should run to confirm that it behaves as the developers expect it to behave.

- Everyone commits to the baseline every day

By committing regularly, every committer can reduce the number of conflicting changes (No integration Hell).

- Every commit (to baseline) should be built

The system should build commits to the current working version to verify that they integrate correctly.

- Keep the build fast

The build needs to complete rapidly, so that if there is a problem with integration, it is quickly identified.

**Tools involved when working Continuous integration **

Here is a list of many thinks you need to setup and work with CI:

- distributed version control system, like Git.

- Build server, there are many, check out many [CI builds server options](https://en.wikipedia.org/wiki/Comparison_of_continuous_integration_software). we used Travis-CI.

- Some kind of dependency management, Like maven.


**Maven**
Maven is used with java as a dependency management tool, each machine can fetch required dependencies.  Maven also help with IDE independency and Build Automation (build, test, deploy, etc.). With Maven we can do CI locally (on our own developer machine) and a Build Server can do the same.

**Build server - Travis-CI**
We have used a free tool, Travis-CI, it is easy to set up as our build server environment. Travis CI helps us run test-driven development in your own projects and with your peers. 
In our prject we wrote:
*For our continuous integration process we have used Travis-CI - an on-the-fly CI tool integrated with our GitHub repositories, so that each commit or pull-request will be tested automatically.*

### Explain why Maven (or similar tools) is a "great" match for CI via a Build Server, and elaborate on the properties we can take advantage of. 

Maven is a great tool cause it lets us run same environment and setup locally and on server. Maven make it a lot easier to import libraries steam line the development process. for properties look in earlier question.

### Explain how to use separate test phases for Unit Tests and Integration Tests with Maven.

A great way to use maven is when you run test on your build server. sakfjlads



### Explain how risk is coped with in agile project as compared to traditional approaches

TDD is primarily a specification technique with a side effect of ensuring that your source code is thoroughly tested at a confirmatory level. However, there is more to testing than this. Particularly at scale you'll still need to consider other agile testing techniques such as pre-production integration testing and investigative testing. Much of this testing can also be done early in your project if you choose to do so (and you should). 


With traditional testing a successful test finds one or more defects. It is the same with TDD; when a test fails you have made progress because you now know that you need to resolve the problem. More importantly, you have a clear measure of success when the test no longer fails. TDD increases your confidence that your system actually meets the requirements defined for it, that your system actually works and therefore you can proceed with confidence. 

As with traditional testing, the greater the risk profile of the system the more thorough your tests need to be. With both traditional testing and TDD you aren't striving for perfection, instead you are testing to the importance of the system. To paraphrase [AgileModeling (AM)](http://www.agilemodeling.com), you should "test with a purpose" and know why you are testing something and to what level it needs to be tested. An interesting side effect of TDD is that you achieve 100% coverage test – every single line of code is tested – something that traditional testing
doesn’t guarantee (although it does recommend it).  In general I think it’s fairly safe to say that although TDD is a specification technique, a valuable side effect is that it results in significantly better code testing than do traditional techniques.

To sum up, agile have a lower risk of failing since, it should have a higher code coverage than traditional coding, and therefore a lower risk profile than traditional code project.