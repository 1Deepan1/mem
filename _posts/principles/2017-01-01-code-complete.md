## Code Complete Notes ##

- This could be usefull if you had read Code Complete 
or taken up the on demand e-learning from construx.com by Steve.

- In few of the slides, added my learnings as well, 
which can be identifed by the tag [MDK]

---

### Steve's Point of View ###
1. Source Code is the only long lasting accurate description of software
2. Software construction is the only activity thats guaranteed to be done
3. Great Softwares are created through the thousands of tiny decisions,design,comments and so on.
4. Construct the software well the first time , you wont get a chance to do it again.
5. Leave the code more pristine than it was.

---

###Essential Properties

- The properties a thing has by virtue of being that thing.

car --> engine , wheels

---

###Accidental Properties

The properties a thing just happens to have.

car --> color , engine type

---

#### Technology Knowledge

1. Short lived
2. Readily accquired
3. Accidental

---

#### Principles Knowledge

1. Essential
2. Long lived
3. Not so readily accquired

---

###Complexity 
1. Main reason for project failure is arround the requirement gathering 
2. Second reason is poor project planning
3. Third reason - code quality

---

###Manage Complexity
1. Divide program into manageable size chunks, chunks should be isolated safely to ignore other chunks
2. Stay away from accidental complexity 

---

###Tools for dealing with Complexity
1. Abstraction
2. Cohession / single responsibility
3. Encapsulation
4. Hierarchies
5. Seperation of concerns
6. Coding Conventions
7. Deep Nesting - avoid more than 3 nesting levels
8. Avoid global data
9. Go for the simplest design
10. Quality interfaces
11. Read time vs write time - Code is read many times than it is written

---

###Abstraction

- Allows you to look at a complex information in a simplest way.

---

###Encapsulation

- Hiding the implementation details - the complex information , 
in modern programming languages there is no more encapsulation.
- [MDK]
The other way would be encapsulate the details which may vary.

[MDK]Example :

	List<String> stooges = Arrays.asList("Larry", "Moe", "Curly");
- Here client is not aware of the concrete implemetation 
that the above operation is going to return. 
So it makes easier for further enhancements or changes, 
client will not be affected.There is much more to it, hope you get the point.

---

### Avoid Global Data

- The title is more sufficient to understand , this is related to encapsulation.
- Dont provide global access to the members of the class. Basically it boils down to getters and setters,
 Steve calls it as access routines. 

---

###Code Level Optimisation

>The best is the enemy of the good

- Working toward perfection might prevent completion. Complete it first and then perfect it.
The part that needs to be perfect is usually small.(80/20 rule)

>We should forget about small efficiencies, say about 97% of the time : 
premature optimisation is the root of all evil --Donald Knuth

---

### It is not about

- Algorithim selection
- Design for performance.

---

### Reasons to be defensive about code level optimization

- Root cause for complexity and code quality
- Results in accidental complexity

---

### Defensive Approach

- Step 1: Don't worrry about optimization , always write a emphasising , readable , simple and maintainable code

- Step 2: Measure the performance, if performance is not satisfactory

- Step 3: Find the performance hotspots.

- Step 4: Perform transformations one at a time.

- Step 5: Measure each transformations and rollback the changes that dont work

- Step 6: Repeat untill done.

---

### Steve's Rule for Code optimization

>If you haven't measured , you dont know

Invalid Exceptions(Don't Believe)

- Everybody know that this approach is faster than that.
- I read in that book , that this approach is faster than that.
- I applied this optimization on my last project. 

---

### Error Processing 

---

### Times When Error Processing Required

- input values are out of range
- input values are of wrong type of data
- input values that are incomplete
- input values that are unusual
- input values that aren't defined

---

### Error Processing Decisions

- What does your program do with bad input values
- Do you need to handle every error or just common errors
- Which part of the program is responsible
- Should all error be treaded same way
- Should all parts of the program handle errors the same way
- Are these coding or design or architecture decisions

---

### Correctness Vs Robustness

- Correctness means 100% accurate, else will not return result
- Robustness means always return the result, even if it is not accurate

---

### Importance of Error Processing

- It should be a architecture decision
- 25 - 75 % of code is related to error handling

---

### Error handling Techniques 

- Return a neutral value 
- Substitue the next piece of valid data
- Return the same answer as the previous time
- substitue the closest legal value
- log warning message to a file
- Return an error code 
- Shutdown

---

### Exceptions

- Use Exceptions to notify other parts of the program about errors that should not be ignored
- Throw an exception only for condtions that are truly exceptional
- Dont throw an uncaught exception in a section of code if you can handle the error locally
- Throw exceptions at the right level of abstractions
- Consider creating your own project specific exception class , which can serve as the base class for all exceptions
  thrown on your project.
- Consider alternatives to exceptions
- Define a standardized approach to exception handling.

---

### Assertions

- Way to document design assumptions , an executable documentation
- Rather than documenting in comments consider using assertions
- If an assertion fails the corrective action is to recode
- Development time aid , not for production
- Do not use assertions to check the parameters of a public method
- Use an assertion to test a nonpublic method's

---

### Need for Assertions
- Large code base
- complex programs
- large team , geographically distributed
- long lived code base
- eg: from java docs.
	
		/**
	 	* Sets the refresh interval (which must correspond to a legal frame rate).
	 	*
	 	* @param  interval refresh interval in milliseconds.
	 	*/
	 	private void setRefreshInterval(int interval) {
	  	// Confirm adherence to precondition in nonpublic method
	  	assert interval > 0 && interval <= 1000/MAX_REFRESH_RATE : interval;

	  	... // Set the refresh interval
	 	} 

---

### Minimize Gap between defect insertion and defect detection

- Unit Test
- Assertions
- Formal code inspection
- Pair Programming
- Single Stepping through debugging

---

### Minimizing defects beyond coding

- Requirement inspection
- UI prototyping
- Architecture inspections
- Customer demos
- Frequent releases
- Self review

---

### Pseudocode Programming process

- [MDK] I had done this very fewer times before reading Code Compelte book , from now on I am going to follow it strictly.
- Write each step of routing in English using comment syntax 
- Reveiw the pseudocode
- Fill in the code below each comment
- Keep the pseudocode as comments

---

### Need for Pseudocode 

- Easier to write code
- No blocks while coding , don't have to look back at the requirement doc.
- Easier to review
- Better organised code
- Easier to resume in a multitasking environment
- Fewer errors.
- Last but not the least , comments are already in place.










