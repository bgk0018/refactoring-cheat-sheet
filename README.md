# Refactorings List
The below will be my notes on each of the sections in Refactoring Improving the Design of Existing Code

 - **Composing Methods**
	 - [Extract Method](#extract-method)
	 - [Inline Method](#inline-method)
	 - [Inline Temp](#inline-temp)
	 - [Replace Temp with Query](#replace-temp-with-query)
	 - [Introduce Explaining Variable](#introduce-explaining-variable)
	 - [Split Temporary Variable](#split-temporary-variable)
	 - [Remove Assignments to Parameters](#remove-assignments-to-parameters)
	 - [Replace Method with Method Object](#replace-method-with-method-object)
	 - [Substitute Algorithm](#substitute-algorithm)
 - **Moving Features Between Objects**
	 - [Move Method](#move-method)
	 - [Move Field](#move-field)
	 - [Extract Class](#extract-class)
	 - [Inline Class](#inline-class)
	 - [Hide Delegate](#hide-delegate)
	 - [Remove Middle Man](#remove-middle-man)
	 - [Introduce Foreign Method](#introduce-foreign-method)
	 - [Introduce Local Extension](#introduce-local-extension)
 - **Organizing Data**
	 - [Self Encapsulate Field](#self-encapsulate-field)
	 - [Replace Data Value with Object](#replace-data-value-with-object)
	 - [Change Value to Reference](#change-value-to-reference)
	 - [Change Reference to Value](#change-reference-to-value)
	 - [Replace Array with Object](#replace-array-with-object)
	 - [Duplicate Observed Data](#duplicate-observed-data)
	 - [Change Unidirectional Association to Bidirectional](#change-unidirectional-association-to-bidirectional)
	 - [Change Bidirectional Association to Unidirectional](#change-bidirectional-association-to-unidirectional)
	 - [Replace Magic Number with Symbolic Constant](#replace-magic-number-with-symbolic-constant)
	 - [Encapsulate Field](#encapsulate-field)
	 - [Encapsulate Collection](#encapsulate-collection)
	 - [Replace Record with Data Class](#replace-record-with-data-class)
	 - [Replace Type Code with Class](#replace-type-code-with-class)
	 - [Replace Type Code with Subclasses](#replace-type-code-with-subclasses)
	 - [Replace Type Code with State/Strategy](#replace-type-code-with-state/strategy)
	 - [Replace Subclass with Fields](#replace-subclass-with-fields)
 - **Simplifying Conditional Expressions**
	 - [Decompose Conditional](#decompose-conditional)
	 - [Consolidate Conditional Expression](#consolidate-conditional-expression)
	 - [Consolidate Duplicate Conditional Fragments](#consolidate-duplicate-conditional-fragments)
	 - [Remove Control Flag](#remove-control-flag)
	 - [Replace Nested Conditional with Guard Clauses](#replace-nested-conditional-with-guard-clauses)
	 - [Replace Conditional with Polymorphism](#replace-conditional-with-polymorphism)
	 - [Introduce Null Object](#introduce-null-object)
	 - [Introduce Assertion](#introduce-assertion)
 - **Making Method Calls Simpler**
	 - [Rename Method](#rename-method)
	 - [Add Parameter](#add-parameter)
	 - [Remove Parameter](#remove-parameter)
	 - [Separate Query from Modifier](#separate-query-from-modifier)
	 - [Parameterize Method](#parameterize-method)
	 - [Replace Parameter with Explicit Methods](#replace-parameter-with-explicit-methods)
	 - [Preserve Whole Object](#preserve-whole-object)
	 - [Replace Parameter with Method](#replace-parameter-with-method)
	 - [Introduce Parameter Object](#introduce-parameter-object)
	 - [Remove Setting Method](#remove-setting-method)
	 - [Hide Method](#hide-method)
	 - [Replace Constructor with Factory Method](#replace-constructor-with-factory-method)
	 - [Encapsulate Downcast](#encapsulate-downcast)
	 - [Replace Error Code with Exception](#replace-error-code-with-exception)
	 - [Replace Exception with Test](#replace-exception-with-test)
 - **Dealing with Generalization**
	 - [Pull Up Field](#pull-up-field)
	 - [Pull Up Method](#pull-up-method)
	 - [Pull Up Constructor Body](#pull-up-constructor-body)
	 - [Push Down Method](#push-down-method)
	 - [Push Down Field](#push-down-field)
	 - [Extract Subclass](#extract-subclass)
	 - [Extract Superclass](#extract-superclass)
	 - [Extract Interface](#extract-interface)
	 - [Collapse Hierarchy](#collapse-hierarchy)
	 - [Form Template Method](#form-template-method)
	 - [Replace Inheritance with Delegation](#replace-inheritance-with-delegation)
	 - [Replace Delegation with Inheritance](#replace-delegation-with-inheritance)
 - **Big Refactorings**
	 - [Tease Apart Inheritance](#tease-apart-inheritance)
	 - [Convert Procedural Design to Objects](#conver-procedural-design-to-objects)
	 - [Separate Domain from Presentation](#separate-domain-from-presentation)
	 - [Extract Hierarchy](#extract-hierarchy)

---
# Composing Methods
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

## Remove Assignments to Parameters
https://refactoring.com/catalog/removeAssignmentsToParameters.html

- Avoid assigning value to parameters, instead use a temp variable
- Helps avoid clarity issues between pass by reference and pass by value
- Output parameters are an exception but should be used in very limited circumstances

## Replace Method with Method Object
https://refactoring.com/catalog/replaceMethodWithMethodObject.html

- Introduces the [Command Pattern](https://sourcemaking.com/design_patterns/command/java/2)
- Reduces duplication in common work by encapsulating that functionality in an object

## Substitute Algorithm
https://refactoring.com/catalog/substituteAlgorithm.html

- Given two algorithms, select the one that is either
  - More performant
  - More succinct
  - More expressive
- Have tests that assert the result of the original algorithm and run them after replacing to insure the new algorithm is a proper substitute

# Moving Features Between Objects
## Move Method
https://refactoring.com/catalog/moveMethod.html
