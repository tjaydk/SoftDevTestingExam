### Week 12 - Integration testing

#### Explain what the focus and purpose of integration testing is

Integration testing is when you combine produced components which has been unit tested in order to see if they work together. There are to ways to do integration testing, in the agile world you use CI (Continues Integration) which means that as you deliver small parts of the application along the way you will then be able to test these with integration test. This will then demand for stubs and mocks to mimic the parts of the system not yet done which is needed by the components. Here there are two ways of doing it:

Top-down: where you use stubs to do state verification of the underlying components missing. So you start from the GUI and work your way down.

Bottom-up: you start from the back end and work your way up to the GUI. Here you would use mocks to insure behavior of the missing components.

The other approach is 'Big Bang' where all components are put together in the end to test. This removes the necessary mocks and stubs of the above approach but will make it difficult to locate the root cause of an error as it can be in any of the components.



#### Account for the relation between integration scope and defects isolation

When an error occur within a integration test it should be possible to isolate which interface or which part of the application that caused the error. This is also one of the reasons for using a lot of interfaces in order to narrow the error down to a minimum. When the interface which triggered the defect is discovered you can then do a static analysis or refer to documentation to see which underlying components are used. Then you would hopefully be able to narrow the debugging phase down as you go.

#### Explain when integration is done and under which conditions

As explained earlier there are different approaches to integration test, either it is done continuously, where a tool like Travis comes in to play, in order to automate the process of building the application and running the tests and afterwards give feedback if said build failed. Or the big bang approach which can also be done using Travis, but is first done when all the components are finished. So this is more like a System Test actually. Common for the tests are that they should be done in a staging environment in order to ensure that it mimics the final environment and that it gives the same feedback to all developers running the test.

#### List different types of integration tests and elaborate on the differences between them

We had the:

Top-down: where we go from the GUI down the pipe.

Button-up: the opposite approach from top-down.

Big-Bang: Everything is tested when all the components are done.

System-integration: This is in order to ensure that the system produced can communicate with other systems and works in the environment. This is done after system testing. 