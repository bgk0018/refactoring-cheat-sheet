# Refactorings List
The below will be my notes on each of the sections in Refactoring Improving the Design of Existing Code

 - **Composing Methods**
	 - [Extract Method](##extract-method)
	 - [Inline Method](##inline-method)
	 - [Inline Temp](##inline-temp)
	 - [Replace Temp with Query](##replace-temp-with-query)
	 - [Introduce Explaining Variable](##introduce-explaining-variable)
	 - [Split Temporary Variable](##split-temporary-variable)
	 - Remove Assignments to Parameters
	 - Replace Method with Method Object
	 - Substitute Algorithm
 - **Moving Features Between Objects**
	 - Move Method
	 - Move Field
	 - Extract Class
	 - Inline Class
	 - Hide Delegate
	 - Remove Middle Man
	 - Introduce Foreign Method
	 - Introduce Local Extension
 - **Organizing Data**
	 - Self Encapsulate Field
	 - Replace Data Value with Object
	 - Change Value to Reference
	 - Change Reference to Value
	 - Replace Array with Object
	 - Duplicate Observed Data
	 - Change Unidirectional Association to Bidirectional
	 - Change Bidirectional ASsociation to Unidirectional
	 - Replace Magic Number with Symbolic Constant
	 - Encapsulate Field
	 - Encapsulate Collection
	 - Replace Record with Data Class
	 - Replace Type Code with Class
	 - Replace Type Code with Subclasses
	 - Replace Type Code with State/Strategy
	 - Replace Subclass with Fields
 - **Simplifying Conditional Expressions**
	 - Decompose Conditional
	 - Consolidate Conditional Expression
	 - Consolidate Duplicate Conditional Fragments
	 -  Remove Control Flag
	 - Replace Nested Conditional with Guard Clauses
	 - Replace Conditional with Polymorphism
	 - Introduce Null Object
	 - Introduce Assertion
 - **Making Method Calls Simpler**
	 - Rename Method
	 - Add Parameter
	 - Remove Parameter
	 - Separate Query from Modifier
	 - Parameterize Method
	 - Replace Parameter with Explicit Methods
	 - Preserve Whole Object
	 - Replace Parameter with Method
	 - Introduce Parameter Object
	 - Remove Setting Method
	 - Hide Method
	 - Replace Constructor with Factory Method
	 - Encapsulate Downcast
	 - Replace Error Code with Exception
	 - Replace Exception with Test
 - **Dealing with Generalization**
	 - Pull Up Field
	 - Pull Up Method
	 - Pull Up Constructor Body
	 - Push Down Method
	 - Push Down Field
	 - Extract Subclass
	 - Extract Superclass
	 - Extract Interface
	 - Collapse Hierarchy
	 - Form Template Method
	 - Replace Inheritance with Delegation
	 - Replace Delegation with Inheritance
 - **Big Refactorings**
	 - Tease Apart Inheritance
	 - Convert Procedural Design to Objects
	 - Separate Domain from Presentation
	 - Extract Hierarchy

---

## Extract Method
https://refactoring.com/catalog/extractMethod.html

- Helps provide clarity of purpose for the enclosed statements
- Removes the need for comments when using expressive method names
- Consider using even over short pieces of code that are semantically dense
- Consider using if inside the method the statements deal with different [layers of abstraction](http://principles-wiki.net/principles:single_level_of_abstraction)
- Don't use if the extracted piece of code cannot be given a better name than the current method's

## Inline Method
https://refactoring.com/catalog/inlineMethod.html

- Helps with needless indirection
- Consider using as an intermediate step to cleaning up badly factored, smaller methods
- Don't use if a subclass overrides the method

## Inline Temp
https://refactoring.com/catalog/inlineTemp.html

- Only use when assigning the value of a method call
- Consider using as an intermediate step when refactoring to a [Replace Temp with Query](##replace-temp-with-query)

## Replace Temp with Query
https://refactoring.com/catalog/replaceTempWithQuery.html

- Helps reduce method size by extracting a commonly used query
- Consider using if a given expression is used only once within the method
- Consider using if the temp variable is only assigned to once within the method

## Introduce Explaining Variable
https://refactoring.com/catalog/extractVariable.html

- Helps with expressiveness of conditional statements
- Consider using if many conditionals are being considered
- Consider using [Extract Method](##extract-method) for the conditional statement if it is a recurring check instead
- Often leads to [Replace Temp With Query](##replace-temp-with-query)


## Split Temporary Variable
https://refactoring.com/catalog/splitTemporaryVariable.html

- Consider using if you are re-using a temp variable
- Helps refactor code to follow [Single Responsibility Principle](http://principles-wiki.net/principles:single_responsibility_principle)
- Can likely be identified if the name of the variable does not express what it's used for in a meaningful way (temp, foo, etc.)
- 