# Unit testing and Mocking (week 4 - 6)

### ● Explain what makes a test a unit test.

Unit tests, also called component tests, are separatable tests that seek to test the system in isolation, focusing on specific, isolated components and ensuring that the singular component itself functions as intended. It's a test that ensures that when not enacted upon by external factors, a component or function behaves as it's intended to behave. Usually a unit test makes use of **stubs** to fill in and specify the state of the component such that it is usable, and to further control the environment it's tested within.

Unit tests are also used for non-functional testing, such as resource-behavior (e.g. memory leaks), performance testing of specific functions, or robustness testing to ensure that something doesn't break when used in different ways.



### ● Explain properties that make a unit test a good unit test

First off, proper test design techniques should be taken into use to ensure that the test case is clearly written, has a clear test basis, is traceable, readable and has its assertions correctly defined. Usually you want to either write the test cases for unit tests with a programmer or with the usage of a test oracle, to ensure that your pre/post-conditions and assertions are correct.

When implementing the test, the approach depends on if you're working as an independent tester, or if the testing is part of a test-first approach such as in XP. If testing as an independent, you often want to work with either the programmer who coded the function being tested, or with a different programmer who's independent from the coding of the function, which could possibly uncover unnoticed defects.

Of course, most importantly, a good unit test needs to be properly isolated, lest it inadvertently ends up becoming more of an integration test. Usage of stubs and mocks should be carefully considered when testing a function, to avoid unnecessary processing time and possible influencing of the function's operations by external factors.



### ● Provide examples (in words, not code) of JUnit tests which are not Unit tests

At its core, JUnit is not necessarily exclusively a unit-testing framework - it's a framework intended for unit testing that also functions perfectly well as an independent test runner. While it's clearly defined as a framework for unit testing, you can just as easily use JUnit to run such things as integration tests, API tests through frameworks like REST Assured, or even UI tests through Selenium.

Examples in our own project are all of our integration and REST tests. The tests for our DAO methods are not unit tests, but integration; they connect to a live database and perform real queries for every test. Still, they're run using JUnit.



### ● What is meant by a test fixture?

A test fixture is a resource or collection of resources used to set up the system's state before performing a test. Having a fixture means you will be capable of easily setting up the system's pre-conditions, such as by establishing connection to a database, loading in test data, or running and instantiating any parts of the system you need operational with specific values and settings such that you create a stable test bed that's consistent between every time you run the test. When creating a fixture, you want to ensure that you cover all variables inherent to the functionalities that you're testing, even if it's things that it shouldn't directly influence, as it's possible that the settings of specific variables or such can have an unintended, unnoticed impact on the functionality. An example of a test fixture is something like using DBUnit, wherein we instantiate a test database and load it with test data, which is data we have pre-defined and know the contents of every time we run the test, such that we can always be assured of what we can assert against.



### ● Explain, using a short example, the rationale behind the Arrange - Act - Assert strategy for testing

Arrange - Act - Assert is a way of structuring a unit test with regards to its pre-conditions, its execution and its assertions. You first set up all required resources; instantiate variables and instances, load stubs, create mocks etc, then you call the functions you're aiming to test, and then you assert against the output of the functional calls.

Let's say we're unit testing a facade function which, among other things, makes a call to a DAO method that connects to a database. We want to make a unit test, so we wish to mock out that functional call. We would start off by first instantiating and configuring the mock object we need, then add whitespace between that and the functional calls. We perform the functional calls, and then add whitespace between them and the assertions. Basically it's a way of separating the three different parts of a test; we start by creating all the variables we need, then we call the functions, then we assert, with none of these activities mixed between each other.

```
[TestMethod]  
public void Withdraw_ValidAmount_ChangesBalance()  
{  
    // arrange  
    double currentBalance = 10.0;  
    double withdrawal = 1.0;  
    double expected = 9.0;  
    var account = new CheckingAccount("JohnDoe", currentBalance);  
    // act  
    account.Withdraw(withdrawal);  
    double actual = account.Balance;  
    // assert  
    Assert.AreEqual(expected, actual);  
}  
```

A fairly simple illustrated example here. We **arrange** by instantiating all required variables, then **act** by making the function calls, then **assert** by calling our assertion matchers. The purpose of this is traceability; we clearly separate what's being tested from the setup.

A thing you could mention is Martin Fowler's description of the xUnit test sequence; **setup, exercise, verify, teardown.** It's basically the same as AAA, but with post-conditions factored in as well.

### ● Explain the topics: State Verification vs Behavior Verification and strategies for testing each

This question is probably a kinda sneaky way of trying to get us to explain the difference between **mocks** and **stubs**. Mention the Martin Fowler article "[Mocks Aren't Stubs](https://martinfowler.com/articles/mocksArentStubs.html)", Tine will love that.

When performing unit tests you often require **collaborator objects** in order to perform certain function calls on the object you're focusing on testing, also called the **system under test**, or the **primary object**. You might need an instance of a User object to send into a function in order to run it, or you need some certain variables set in an instance in order for a function to run correctly. We do this through **test doubles**, which are objects closely mimicking the real objects that would normally be used by those functions.

**State verification** means we're determining whether an executed method worked correctly by examining the state of the **primary object** and its **collaborator objects** after execution. State verification makes use of **stubs,** wherein we instantiate the collaborator objects and change their state, either through dependency injection or get/set methods, and then use its native functions as normal.

**Behavior verification** means we're working with **mocks** instead, as we're not interested in stubbing out the state of a collaborator object, we're just making a dummy object that does exactly what we tell it to do. In the setup phase, or the **act** phase of AAA, it's not just instantiating objects, it's instantiating objects and then specifying expectations, telling the Mock object to do a certain thing when asked for something specific, or when a specific function call is made.

The difference between the two types of verification come down to what we're focusing on asserting against. In the example by Martin Fowler, he tests against a Warehouse object that can contain certain items and a quantity of each of those items, and then functions can ask for a specific quantity of those items. In his example, **state verification** is basically testing that the state of the Warehouse object is correct; if it contains the correct items and the correct quantity of them, it should behave as intended. **Behavior verification** however focuses on the **primary object,** the Order, ensuring that it calls the correct functions and performs the correct actions with the output of those functions. 

**Stubs** are canned answers to function calls made in the test. They're basically test fixtures that are set up to provide a certain state to test against; an example of this would be if we used DBUnit and created a test database through an SQL fixture. In this case, the DBUnit database would be a stub.

**Mocks** are objects pre-programmed with expectations that they enact upon whenever those expectations are met. They're set up to mimic the structure of another class, and then when a specific method is called, they have a pre-defined output to send back. 

The strategies for testing each of them comes down to which frameworks to use. Behavior verification makes usage of Mocks, through frameworks such as Mockito or xMock, and State verification makes usage of test fixtures and frameworks such as DBUnit if stubbing out things in system integration.



### ● Explain about the JUnit Framework, how to include it in a project, and how to write tests

The JUnit framework is a unit-testing framework first and foremost, but also functions as an effective test runner when performing non-isolated automatized tests, such as integration or UI tests. It functions through usage of **Reflection**, wherein test classes and methods are marked by Java **annotations**, adding metadata that the Reflection API can then identify and include in its test procedure. 

JUnit is included as a default library in most, if not all larger Java IDE's, and can be added to a project either through creating a JUnit test class, or by adding the library manually as a dependency to the project module. If the project uses Maven, then JUnit can also be added to the dependency list through the pom.xml file.

Writing tests can be done either by creating a new JUnit class in most IDE's, at least definitely in NetBeans, IntelliJ and Eclipse, or by creating a standard Java class and annotating it with the JUnit annotation `@TestClass`. You can then optionally set up pre/post-conditions through the `@BeforeClass` and `@AfterClass` annotations.

Writing unit tests is quite simple, as it requires only creating a method annotated with the `@Test` annotation, which will cause the JUnit test runner to flag it as a test method to be run. The test method then is written by calling the desired functions, potentially mocking functions or stubbing out dependencies, and then **asserting** against a desired output. This can be done through either the included JUnit matcher library, or through a third-party matcher library such as **Hamcrest.**



### ● Explain a few rules of what makes a good Unit test, and rules for what makes code testable (or untestable).

First off, proper test design techniques should be taken into use to ensure that the test case is **clearly written**, has a **clear test basis**, is **traceable**, **readable** and has its **assertions correctly defined**. Usually you want to either write the test cases for unit tests with a programmer or with the usage of a **test oracle**, to ensure that your pre/post-conditions and assertions are correct.

When implementing the test, the approach depends on if you're working as an independent tester, or if the testing is part of a test-first approach such as in XP. If testing as an independent, you often want to work with either the programmer who coded the function being tested, or with a different programmer who's independent from the coding of the function, which could possibly uncover unnoticed defects.

Of course, most importantly, a good unit test needs to be **properly isolated**, lest it inadvertently ends up becoming more of an integration test. Usage of **stubs** and **mocks** should be carefully considered when testing a function, to avoid unnecessary processing time and possible influencing of the function's operations by external factors.

In order for code to be testable, the code should be open for alterations such that the test can alter the **state** of the **system under test**, basically meaning that we should be capable of **stubbing** it and all the necessary collaborator objects. One of the big sinners when it comes to untestable code is **static** methods, **final** fields and **private** methods. 



### ● Explain about the SOLID rules plus a number of the additional rules given in Effective Unit Testing focusing on WHY following these rules makes code more testable

The SOLID principles mesh very well with testable design, as they're highly geared towards making code modular and upholding the coupling-coherence pattern.

#### Single Responsibility Principle

SRP is basically the distilled version of the **cohesion/binding** part of coupling-coherence. Simply, it's "*There should never be more than one reason for a class to change.*" Classes should have a singular focus, wherein all methods inside of the class have the same basic goal and purpose; basically, the contents of the class must be **coherent.** 

This makes a class easier to test because it greatly enhances its **traceability.** You can easily understand what the purpose of the class methods are once you've understood one of them, and if you test one, you supposedly should have a much easier time testing the others due to your understanding of their purpose. SRP also has a subcategory in defining that every method should only have one reason to change as well, called the **inside view.** Following this rule also makes the methods much less complex, which in turn makes them much easier to test due to their inherently low **cyclomatic complexity.**

#### Open-Closed Principle

OCP states that a class must be "*open for extension but closed for modification.*" You want to be able to change a class, or the *behavior* of a class, without having to change the source code inside of the class. This could probably easily be coupled with **dependency injection patterns,** as you can extend the operations of a class by passing in a **test double** with exactly the parameters you want. 

[An example of it can be found here.](http://joelabrahamsson.com/a-simple-example-of-the-openclosed-principle/)

#### Liskov Substitution Principle

This is the principle that Lars told us we basically shouldn't ever have to worry about too much, because he hates inheritance and singleton patterns.

It basically outlines that when you have subclasses of a superclass, you should be capable of substituting instances of those superclasses with instances of their subclasses without issue. It's a way of discouraging lazy usage of subclasses that isn't focused on polymorphism, but instead on just code reuse.

#### Interface Segregation Principle

"*Many client specific interfaces are better than one general purpose interface.*" Interfaces should be kept **small and focused.** Having small interfaces makes them much more easily testable, and much easier to use as **test doubles** if you're intending on creating **stubs, fakes and mocks** without having to double the same enormous interface for every implementation you instantiate.

#### Dependency Inversion Principle

"*Code should depend on abstractions, not on concretions.*" This is the SOLID version of the **dependency injection pattern.** It describes that a class shouldn't instantiate its own collaborators, but have their interfaces passed in through either setter methods or the constructor. 

It's basically giving the tester the ability to pass in their own collaborators instead of selectively overwriting parts of the code to suit the tester's needs. It's the #1 with a bullet most important principle in SOLID when it comes to testing.

### ● Explain the topic “data driven testing” and ways to do it, using both “plain” JUnit and alternative libraries which easily lets you read test data from files (CSV, Excel, etc.)

Data-driven testing more or less goes hand-in-hand with test cases based upon **equivalence partitioning** and **boundary values.** If we have a method that we want to test with a wide range of different inputs to ensure that all of them are handled correctly, data-driven test makes this a whole lot easier, and cuts down drastically on the amount of test methods that need to be created.

An example of a data-driven test is the **parameterized test** we made in JUnit for the study point exercise "*Testing Real Life Code*", where we created a parameterized test that loaded in a CSV file, and ran the same test over and over again for every input found in that CSV file. The test was run over a hundred times, but without having to create a new test for every input. This is done by adding the annotation `@RunWith(Parameterized.class)` to the test class, creating a method with the `@Parameterized.Parameters` annotation that loads and initializes the test data from the data file, and then making regular unit tests with the data gained from that initialization method.

Other frameworks include the Apache POI Framework, which is an API that supports read/write operations for Excel files, which is often used in conjunction with Selenium. Doing this can make the task of creating Selenium tests noticeably easier, cuts down on code generation, and is generally a pretty useful aide in black-box testing.

Data-driven testing is also a factor when using tools like JMeter, as it takes in CSV files for input.



### ● Explain how, or if, tools like JaCoCo or similar can be used to measure the "quality" of our tests

Tools like Jacoco are not explicitly capable of measuring the *quality* of our tests as such. Jacoco is a code coverage tool, which does provide assistance in structural coverage testing by outlining the **statement coverage** and **line coverage** of our test cases. As such, in some way it doesn't directly measure the quality of our *tests*, but rather the quality of our approach to **coverage testing**.

**Coverage testing** has a flaw in that while it is capable of measuring the amount of code is being executed by our test procedures, it does not explicitly state if that code is covered by varying types of input. Jacoco can't tell us whether we have outlined a sufficiently thorough set of test cases, conditions and partitions for a test basis, it just tells us how much of the code has been executed by tests. 



### ● Explain strategies/frameworks used to unit test single classes with dependencies

First off you wanna take a good long look at **dependency injection.** Single classes with dependencies should be capable of dependency substitution, such that unit tests can much more easily change the state and behavior of the object instance to fit what's needed for the test. 

The dependency substitution then allows us to test the class in different ways depending on what our intentions are. We could send in test doubles as **stubs** if we're interested in making sure the collaborator objects function properly within a certain method call, or we can create **mock** objects to send in if we're not interested in the collaborators actually *doing* anything, especially if the collaborators were to start calling other methods and doing more difficult-to-substitute operations deeper down. 



### ● Explain about Test Doubles and specific types like: Dummy Objects, Test Stubs, Mock Objects and their purpose for Unit testing objects with dependencies.

**Test doubles** are dummy implementations of **collaborator objects** in a unit test. They're made and used when you're stubbing out a dependency in a class, doubling for the actual implementation, having the exact implementation that you want for your test to run as you want it to. It's a pretend object that's used in place of real objects for testing purposes.

**Dummy objects** are objects passed around but never used. These are commonly made when you're trying to instantiate a class with a constructor that requires certain dependencies, so you create a dummy object to throw in, although in your unit test the object is never used. It just fills out a parameter list so the compiler will stop crying.

**Fake objects** are objects that have actual working implementations, but the implementation has been modified and shortcutted to make then not suitable for production, but perfectly suitable for a test due to higher efficiency. An example of a **fake** would be an **in-memory database.**

**Stubs** are objects wherein you have specified the object instances' **state,** making sure that when you call a function on the stub, it returns exactly what you want it to, while still doing the real work behind the curtains. The functions run as they should, but the result is canned and prepared, so what you're really testing is whether the stub handles that data properly.

**Spies** are **stubs** that log information about the operations taking place in the stub. 

**Mocks** are fake implementations of real class objects, wherein the tester specifies their exact behavior, and never actually calls anything in the real class. It contains the same bytecode signatures as the real class, tricking the compiler into running it as it would a real implementation, but the mock object has been specified to wait for certain method calls, and when those calls are made, have a specific canned response to send back without actually running any method in the back. These are often used when we're not interested in what's going on in the collaborator object, we just wanna send it in as a dependency to the **system under test** to provide it with a canned response, reducing processing time.



### ● Explain the difference between state based testing versus behavior based testing, and provide practical examples using JUnit and a relevant Mock-framework.

**State verification** means we're determining whether an executed method worked correctly by examining the state of the **primary object** and its **collaborator objects** after execution. State verification makes use of **stubs,** wherein we instantiate the collaborator objects and change their state, either through dependency injection or get/set methods, and then use its native functions as normal.

**Behavior verification** means we're working with **mocks** instead, as we're not interested in stubbing out the state of a collaborator object, we're just making a dummy object that does exactly what we tell it to do. In the setup phase, or the **act** phase of AAA, it's not just instantiating objects, it's instantiating objects and then specifying expectations, telling the Mock object to do a certain thing when asked for something specific, or when a specific function call is made.

The difference between the two types of verification come down to what we're focusing on asserting against. In the example by Martin Fowler, he tests against a Warehouse object that can contain certain items and a quantity of each of those items, and then functions can ask for a specific quantity of those items. In his example, **state verification** is basically testing that the state of the Warehouse object is correct; if it contains the correct items and the correct quantity of them, it should behave as intended. **Behavior verification** however focuses on the **primary object,** the Order, ensuring that it calls the correct functions and performs the correct actions with the output of those functions. 

**Stubs** are canned answers to function calls made in the test. They're basically test fixtures that are set up to provide a certain state to test against; an example of this would be if we used DBUnit and created a test database through an SQL fixture. In this case, the DBUnit database would be a stub.

**Mocks** are objects pre-programmed with expectations that they enact upon whenever those expectations are met. They're set up to mimic the structure of another class, and then when a specific method is called, they have a pre-defined output to send back. 

The strategies for testing each of them comes down to which frameworks to use. Behavior verification makes usage of Mocks, through frameworks such as Mockito or xMock, and State verification makes usage of test fixtures and frameworks such as DBUnit if stubbing out things in system integration.

An example using JUnit and a Mock framework would be the study point exercise "*Unit Testing, Testable Code, Mocking and Code Coverage*", where we use Mockito to mock out the DateFormatter class.



### ● Explain about the development process TDD in general, and the steps involved when using this process.

**Test-Driven Development** is a core tenet in **Extreme Programming**, and in basic terms, it describes that when writing code, unit tests should be written before writing the function itself. It follows that using testing techniques to set up test bases, partitions and test cases beforehand allows for the purpose of the test to be greatly clarified, and if the test is written correctly, possibly with the help of a test oracle to explain what the function is supposed to do, we are basically locking ourselves into how the function itself should behave. We define what the input and output must be, and thus gain a much clearer vision of how to build the function. Along with that, having a unit test built beforehand allows us to easily and quickly test the function we're building to see if it works or not, without having to manually test it.

![](https://i.imgur.com/hMpM4Bw.jpg)

It's closely linked to **refactoring,** because at first, you'll usually build the function in a way such that it simply passes. Once it does pass, you add more tests to ensure that it passes several kinds of input. Once you have ensured that the function works as intended, you refactor the function for clarity, cleanness and efficiency, run the tests again, and ensure that they still pass.

Kent Beck's description of TDD boils down to a couple of different rules to follow, that'll generally put you on the right track:

- Only write new business code when an automated test has failed.
- Eliminate any duplication that you find.
- Develop organically, with the running code providing feedback between decisions.
- Write your own tests, because you can't wait 20 times a day for people to write them for you.
- Your development environment must have fast responses to small changes, through fast test designs, fast compiler and a regression testing suite.
- Designs must be **highly cohesive, loosely coupled** components.

What it boils down to, is that good tests **run fast, run in isolation, have easily readable and understandable data, use real data when needed,** and **represent a step towards the overall goal.**



### ● Why would you consider alternative matchers like for example Hamcrest matchers in a JUnit project? Provide examples to demonstrate, how to set up a project to use Hamcrest, the effect of using Hamcrest matchers compared to JUnit's basic Asserts.

The primary reason for alternative matchers like Hamcrest is for readability and error clarity. Hamcrest matchers follow a much more readable, almost behavior-driven design that is more directly descriptive of what is being asserted, and along with that, the matchers are specialized such that if a test fails, the error message is descriptive in a way that directly explains what went wrong.

The old way of asserting equality in JUnit was done like this;

`assertEquals("expected", "actual");`

whereas asserting with Hamcrest is done thusly;

`assertThat("actual",is("expected"));`

Reading the Hamcrest assertion, it actually reads like a descriptive sentence rather than a functional statement. We assert that "actual" is "expected". Of course, this test will fail, because "actual" is not "expected", but instead of an error message just throwing an exception, Hamcrest describes the error for us:

```
java.lang.AssertionError:
Expected: is "actual"
got: "expected"
```

It tells us exactly what assertion went wrong, and the part of the assertion that does not match. It's just a much friendlier, clarified and useful way of telling us that a test has failed, and then telling us *why* it failed.

Setting up a project using Hamcrest is done by adding Hamcrest to the pom.xml of a Maven project.

```
<!-- https://mvnrepository.com/artifact/org.hamcrest/hamcrest-all -->
        <dependency>
            <groupId>org.hamcrest</groupId>
            <artifactId>hamcrest-all</artifactId>
            <version>1.3</version>
        </dependency>
```

After this, you import the static `org.hamcrest` matcher libraries in your test class, and use the `assertThat()`  method as usual.

We have examples of using Hamcrest matchers both in the PlateScanner test exercise, as well as in our own project.

### ● Explain why testers just love the Dependency Injection Pattern

It's basically giving the tester the ability to pass in their own collaborators instead of selectively overwriting parts of the code to suit the tester's needs. It's the #1 with a bullet most important principle in SOLID when it comes to testing.

Dependency Injection Pattern allows us to make extensive use of **dummy objects** to substitute the **collaborator objects** that function as dependencies in the code we're testing. We can **stub, mock and fake** out dependencies to suit our needs, potentially making our tests dramatically more simple, effective, fast and low on resource requirements. It allows us to test functions that potentially make several deeper, further method calls throughout the system, or even call upon external systems such as databases or CDN servers, allowing us to make true unit tests instead of integration tests for these methods. 



### ● Explain about a typical suggested Project layout for a Java/JUnit based project (for example the one you get with a typical maven project) and the benefits gained from such a layout

When creating a regular Java/JUnit project, the project structure is usually divided such that you have two different groupings of packages; Source Packages and Test Packages. These groupings separate the test classes from the real source classes, but the big benefit to this is that while they are visually separated, the names and classpaths of the packages are **shared.** What this means, is that especially with regards to **visibility,** test classes located inside a package in the Test Packages grouping that has the same package name as a package in the Source Packages grouping are technically within the same package.

As such, visibility rules apply in the same way to the test classes as they do the source classes. This means that, for example, if you have **protected** methods in a source class, if the test class is located in the same package, the methods are **visible** for the test class, allowing it to test them. Visibility is a major factor in **testable design**, so having this kind of project layout is a major benefit. 

 

