## Week 2 - Static testing techniques

### Explain what static testing means

Static testing are a way of improving quality and trying to discover and fix as many mistakes with the code as early as possible. It is focused on reviews of code being done by a developer and giving feedback to that developer in order to make him fix his own mistakes and hopefully learn by them. So the major difference between static and dynamic testing is that dynamic testing is code being run and validated whereas static test is code being evaluated manually or with certain tools, but not executed.

The flaws usually found through static testings are standard deviations, missing requirements, non maintainable code etc. So primarily developers having misunderstood the requirements, or written bad code that did not live up to the standards.

Reviews: Which vary from non formal to formal reviews, e.g. in our project we had reviews of code when a pull request was made to the master branch. Before accepting the code another developer read through the code in order to find errors which could then be fixed before merging to the master branch. This was pretty informal as it was a quick review and any flaws, though stated in the log, was just handed verbally to the developer who could then fix it before supplying with a new pull request. Formal reviews on the other hand are much more comprehensive and consists of:

1 **Planning** (a moderator/inspection leader request and schedules a formal review, the part of the code set for review/inspection is chosen and the participants of the review are given different focuses e.g. 

- Higher level documents: does the code apply with the requirements
- Standard level documents: does the code follow the code standards etc.
- Usability level documets: is the code maintainable/testable).

2 **Kick-off** (A introduction meeting before the review in order to inform everyone what the review is focused on and handing out the roles and describing the code in review and any additional documents that should be used together with reviewing the code. This is optional by highly recommended as it gives a better result in discovering flaws.)
3 **Preparation**: In this face the individual roles review the code with the main object in mind, in order to measure that its done good we use checking rate which is the number of pages of code being reviewed by the hour. Depending on the complexity of the code being review this vary from 5 pages per hour for non complex code to 1 page per hour with complex systems. There should not be reviewed more than said numbers of pages in order to ensure that the thoroughness of the review is consistent.
4 **Review meeting**: The review meeting usually consists of a logging phase, a discussion phase and a decision phase. The logging phase, every reviewer tells of their discovery which is added to a log either written by the developer who is reviewed or better yet by a assistant, so the developer being reviewed can have full attention. In the discussion phase the different participants comes with input to the material and tries to find a resolution, the moderator should keep the discussion on track and ensure that the discussion doesn't escalate into something personal. After the discussion phase a decision phase creates a document with the conclusion of the discussion which then can be used to do the rework and later on to be a tool to asses that the rework is done as per agreement.
5 **Rework**: The rework phase is where the developer that did the code initially, reworks the code to live up to the document that was created during the review meeting.
6 **Follow-up**: After the work is redone a follow up meeting can take place where the code is reexamined to ensure that everything is corrected and that the code now lives up to the agreed exit criteria.



There are three different types of reviews:

- Walk-trough: Where the developer goes through the code page by page in order to give a general overview of what is happening in the code. This is usually done if code has to be explained to non technical persons that don't understand code easily, or if the code is very complex and maybe the developer has expert knowledge and needs to include the other developers.
- Technical review: this can be both formal and informal. Here the technical aspects of the code is explained to achieve consensus of the use of the technology. Its much less focused on finding flaws, but still some domain experts or technical oracles can determine if there are flaws present.
- Inspection which was discussed in the last paragraph.

### Recognize software artifacts that can be examined by different static techniques

As you create the different artifacts like code, UML diagrams and specifying the requirements there is a good reason for using some of the static techniques to discuss the possibilities with different technology and frameworks to gain a common ground on what is achievable and where we are heading. So here you could do reviews of the artifacts produced and have the person responsible for an artifact do a walk-through to get everyone up to speed.

As we did in the project we had both informal reviews of each others code which consisted of just reviewing others code to get a shared code knowledge and find errors early. This was a good approach and did not demand to much of an effort. Then we had walk-through's when it came to different frameworks and technologies that some of the others did not know about. So in order to gain a common ground we ran through the framework to help each member to be able to work in said framework.

So you can review code, frameworks, tests etc.

### Describe the importance and value of using static techniques for the assessment of software artifacts

 When it comes to gaining a common understanding of the requirements and how to achieve them it is a very good idea to have a person who created the artifact do a walk through of said artifact if it is complex or specialized, in order to a achieve shared understanding of the particular artifact. When it comes to code it is a very good way to find errors early and to gain a more collective approach to development by agreeing on standards and being guided if you maybe have misunderstood some information or requirement.

### Explain how static techniques can improve software quality

As said in the above section you can use the static techniques to improve the quality of your software as it helps gain a consensus of good coding standards. So just like with XP pair programming where you can discover errors and share information while working on the software. Then with reviews and walk-through's you are able to get more opinions and members to share knowledge and lead each other in the right direction.

### Explain the difference between static and dynamic techniques, considering objectives, types of defects to be identified, and the role of these techniques within the software life cycle

Dynamic testing techniques has to do with testing running code, so everything from unit tests to integration and system tests are dynamic tests that are either done manually or automatically, and can produce documentation in some cases which can be used to ensure customers of working software and to be used with reviews and in scrum meetings. These types of tests are usually focused on discovering flaws in the system itself, like functionality not working as expected or bad performance with slow algorithms etc. Whereas static testing is still looking at the software, but not executing it but reviewing the lines of code or the artifact in question. These tests are more focused, when it comes to code artifacts, in discovering code standard deviation, unmaintainable code or misunderstanding or requirements. Both techniques can be incorporated in the different phases of the development life cycle but the static tests are mainly done under the development phase whereas there can still be a lot of dynamic tests like system tests, security tests etc. done after the planned development is over and before and after the product has been delivered.

### Explain when in the development life cycle static techniques can be used

Is explained in last paragraph. But usually during development. Either at the beginning phase of development of a new functionality which demands special knowledge to be run through by an expert or when code is delivered ad hoc to improve on the quality of the delivered code and on the code yet to come. The further we come in the development life cycle, there less gain comes from these static tests and more gain comes from dynamic tests as more and more will be focused on the application living up to requirements.

### List some alternatives to static techniques that can help reduce costs for defects in software projects

Alternative to static techniques that help reduce the cost for defects in software programs are early testing like TDD, and CI which can help give quick feedback if the code is functioning as it should or not. The earlier errors are discovered, the less it will cost to fix them.

### Explain the following cost curve and discuss how static techniques can help reduce cost of defects

![Cost curve](http://agilemodeling.com/images/costOfChangeTraditional.gif)

What this curce shows is that the further you get in the life cycle of software development the more expensive it will become to fix errors as a piece of software builds upon components relying on each other, so if an application is very interwoven it will demand a lot of fixes cascading through the system the further ahead in the process we come, especially if it is fundamental flaws. And worse yet, if the product is canned by the customer due to too many defects or misunderstood requirements. So therefore it is very important to discover flaws early, as it is to ensure that the requirements are well understood and that the software developed lives up to high quality, also when it comes to maintainability in the long run. As the piece of software hopefully is to be used for a long time. So static techniques can help lead a developer back on the right track if he had misunderstood the requirements. Or help with quality of code, so it will be maintainable for the future. This is some of the reasons static test techniques can help with the overall development of software.

### List the activities, roles and responsibilities of a formal review

The activities in a formal review is explained earlier as is the roles. But to re cap.

Activities:

- Planning
- Kick off
- Preparation
- Review
- Rework
- Follow up

Roles:

- Moderator (the person who is responsible for the meeting, making sure that everyone is on the same page, avoiding personal conflicts etc.)
- The author (the person responsible for the artifact in review)
- The scribe (the person responsible for doing logging)
- The reviewers (all who has to go through the code with different scopes)
- The manager (the person with the overall responsibility, choosing times, having final say in decisions)

### Explain the differences between the different types of reviews: informal review, technical review, walkthrough and inspection

As stated earlier the difference between the different types of reviews are as follows:

- Informal review is the day to day review like what we did during our project, where we make a informal quick review of the code submitted to the repository when doing a pull request. This give the extra pair of eyes on the code which can sport errors and if the code deviates from the agreed coding standard etc.
- Technical review is where the technical aspects of a piece of code is reviewed to give a general consensus of the technology, so that everyone is one the same page and knowledge can be shared. Here only some experts will use their expertise to spot errors, but the main goal is not to find flaws.
- Walk-through is a general walk through of the code where every piece of the selected code is being run through by the developer, this is especially for giving people who are not developers an insight to what the code does, this is nor to focus on errors.
- Inspection is on the other hand to find errors or flaws in system code to ensure the quality of the code and also to give a general idea of what is happening. It is especially good to do with parts of the code that is prone to flaws.

### Explain the factors for successful performance of reviews

The success factors for a review is:

- Find a 'champion': This is a person with expertise and enthusiasm. One who can help the moderator with performing a good review and makes sure that everyone is giving their best. Everyone should know who the champion is.
- Pick things that really count: E.g. running through the requirements for the system or choosing critical piece of code are very important. But its also important not to try to run everything with inspection as a informal review or walk-through can be the better choice with some documents.
- Explicitly plan and track review activities: make it a day to day thing that is tracked and planned so people take it serious and spend the time needed for it.
- Train participants: the people who are participating in the review should learn from it, so for example with a inspection you should insure that the people not that familiar with the technology gains knowledge from reviewing the code.
- Manage people issues: make sure that it does not spin of track at some mud throwing match. As it is a specific persons code or documentation that is being reviewed there can be a tendency to get personal, this should be avoided and is part of the moderators.
- Follow the rules but keep it simple: try to start of with following the theory until you understand why you can avoid doing specific things. But don't be to formal with the reviews.
- Continuously improve process and tools: Make sure that you learn from the good and bad things and keep participants motivated to come with good feedback.
- Report results: Both the good and the bad as soon as possible. It can be normal just to make note of the errors and log that, but also good things should be documented and shared in order to motivate.
- Just do it!

### Describe the benefits of static analysis in a tool. Use examples by demonstrating static analysis in a tool and explain the results

There are different static analysis tools that can give you everything from code coverage and cyclomatic complexity documentation, api overview, appliance to coding standard. Even the compiler is a static analysis tool that performs a check of syntax to ensure that the code is formulated correctly. We used some different tools in our project e.g. Jacoco for code coverage together with Maven Site which creates documentation of test cases but also builds the API based on the JavaDoc, which also checks for correct JavaDoc, so if the given parameters for a method or return value differs from the javadoc it is made clear when running the ``` mvn site``` statement.

### Explain what typical defects can be identified by static analysis in a tool and compare them to reviews and dynamic testing

These types of tools can give you an overview of how well the code is done on a higher level, the jacoco gives the cyclomatic complexity of your code which shows how many paths a specific method can take based on the number of if statements, while loops, for loops etc. This can be used to check whether a given method would operate slow. There are three different types of CC. 

CC1: The original McCabe method treated each branch as a count.
CC2: A variation of the original method that counts Boolean operators within the decision point. For example, the statement:
IF a==1 AND b==1
Would receive a Cyclomatic Complexity value 1 for CC1, but received a value of 2 in
compliance with CC2.
CC3: Increments Cyclomatic Complexity for each CASE OF clause, and ignores the individual CASE clauses.
CC4: Counts distinct IF/ELSE IF statements. Hence, if an IF statement is present multiple times within a function or file, it is only counted once.

This artifacts can be good to use as a guidance in a review but needs tools to calculate as they would be to time consuming to calculate manually for great amounts of code.