# Team 23 Code Style Guide

## Table of contents:
1. Naming
2. Documentation
3. Code Format
4. Coding Practices

### Terminology Note:
 - Must = absolute requirement
 - Should = recommended. There may be valid exceptions to the rule, but these are weighed and chosen deliberately
 - May = optional

## 1. Naming
These rules apply for all names you will be writing. For example,
 - File names
 - Function/method names
 - Variable names
 - Class names
 - etc.

#### Rules:
 - Names should be descriptive
   - Some few exceptions apply (like `i` in very simple for loops), but it is almost always better to use descriptive names, even inside loops.
     - Ex: use `rowIndex`, and `colIndex` instead of `i` and `j` while accessing a matrix with nested for loops.
   - Names may include short forms but only in very obvious/common scenarios
     - Ex: `getNumTeammates()` instead of `getNumberOfTeammates()`
   - A short form should not have multiple likely full forms
     - Ex: `getRes()` is not an acceptable function name, since it could mean getResolution or getResponse
   - Names must follow these naming conventions:
     - Names must only contain letters and underscores (and period for file extensions)
     - Most names should be lowerCamelCase
     - File names, variables, functions, properties, etc.
       - Ex: `createAccount.js`, `thisVariableHasManyWords` 
     - Classes and components (if using a frontend framework like React) must use UpperCamelCase
       - Ex: `class UserProfile(firstName, lastName)`, `let softwareDev = new SoftwareDeveloper()`
     - Helper functions must have an underscore before them, denoting that they are private
       - Ex: `_constructionHelper()`
     - constants should be all uppercase with underscores separating words (snake case)
       - Ex: `const PORT = 3000`, `const DAYS_PER_WEEK = 7`
       - This does not apply to everything with the const keyword. Ex: `const user_input = _getUserInput()` is valid
     - Booleans should be named with ‘is’ or ‘has’ at the start
       - Ex: `isEmpty` or `hasPermission`

## 2. Documentation
 - Each user function should have a multiline comment in the following form
    ```/*
    Description of function
    Parameters:
    - firstParameterName: description of first parameter
    - secondParameterName: description of second parameter
    - thirdParameterName: description of third parameter
    Returns:
    - description of return value
    */
    ```
- Note: if the function returns multiple values, add more bullet points to the return comment
- For helper functions that are less than 10 lines, they can have a more relaxed comment structure, as long as the header comment still includes a description, parameters, and return value

## 3. Code Format
 - Single lines of code must not exceed 100 characters unless they are imports
 - Indentations should be 4 spaces, not tabs
 - Use [prettier.io](https://prettier.io/playground/#N4Igxg9gdgLgprEAuEAzArlMMCW0AEAEnADYkQDqEATiQCYAUwA5tXHLlM-gLz4A6IABalyggDT5W7eHV74A5IKq06ghZIDOOEghjzUAQxKa4k6AFkI6UwHkAbnGriAvgEp8wflG-58OVAYAQmkOHC43YDYYdGoofCh0MhcAbm9fPz8Aeiz8ABVbABFbJHxC6AV9Gzh8akMoOggAW394tganDN19RJa+C0MYIQA6VHIafAYBoeG6huaGDwAqfABGAFEAagB2N2GYCABlGGpw5kXZuAAHEkMwOAYs-n5h57pNrJxmSUFBN3T4rUOLF4gAeOg4ez4MC3TSaAByhiacB4CmIZEoNHoCnwuBguh4wAABgBNaz4QxsfD2HDaA7UBLoJoAIyc+AAJMBGS0XESXPhLNY7I5qITBdUHE4XAA+AGZfCgzQnaDMaVc0KcZjDTQkHD3Bj4AAMklW+D2BwAqlcrk4AMKGUyLfCbKRsMJcbW6-Wrc0QAAyEAA7naHQ8PC5QVkldQVbLAX4WG7NcMEHRNBQcEMGBI-vgAPwCECF-ClRVXer4JUATwJwGAkHI1FKSn40irChcMokhcjmnLUGl+BcGT8oLgTTj-Bg6qTcDkw58MEj47j8q5DG0ulg-3jmQLgleIBHmVKgiCggXx8jEPs0rSPigLhA4hAECuuGgmmQoEpMcDAAVKQQL8UGMQNDCrL8X2ZOowAAaw4Q4kTgP1wjgZAjBMMwQBgu4EJgQ5yzAM5kBOdBsNMJocFI6hyJfOAAA8bVOZFYGMPInCgSkcDgEDMNMF9tC4XQAEV0AgeAMOMASQAAK00BjDjOUTxMkpB+OwgBHVS4H-GMrhAkAHQAWigdg6DnZ8QBOQwdDOW1miaQxkCMsgrKE5hdAAQRgE4cGZdB4H-JxULMqSsJfIQYCaEgKCETNeKIuBDmAzNIUzKsXLAOErPsciAEkOlgQ4wFOd8vIaY4a3Q9TpOwq4Y1MCg6iuFyGt4pxHCs8JTGoGA9MMZgnPCmTy2oXqXOZQxWRIKyGvCGAMzoIZkAADmNEA2G0nA2AGobnNqiKQGqPJpr4ur6JZOcLLoP16mYdBBrgAAxGgnN8kjQMCiArJgaalpWpAABZOyAA) with --tab-width = 4 for general formatting

## 4. Code Practices
 - KEEP CODE READABLE
 - Variables
   - When declaring a variable in JavaScript, always use `let` or `const`. Do not use `var`. For more information on their differences, check out this [article](https://www.freecodecamp.org/news/var-let-and-const-whats-the-difference/).
     - Ex: `let numUsers = 45`
   - Functions
     - Use helper functions to do sub-tasks.
     - A lower level helper functions should perform one task
     - Functions should be less than 100 lines long
     - Place helper function/methods definitions below user functions/methods
       - Ex: 
            ```
            function authenticateUser(){  //user function
                const userInput = _getUserInput();
                const isValidInput = _validateInput(userInput);
                if(isValidInput){
                    _logInUser()
                }
            }
            function isLoggedIn(){  // user function
                …
            }
            // helper functions
            function _getUserInput(){...}
            function _validateInput(userInput){...}
            function _logInUser(){...}
            ```
 - Global Variables
   - Generally avoid global variables. They can most often be replaced with class member variables
   - Global variables are fine when used as constants
     - Ex: `const DAYS_PER_WEEK = 7`
   - Avoid ‘hacky’ use of global variables. If you need to edit a variable a lot with several functions, consider passing it in as an argument instead.
 - Imports
   - Do not import the same file more than once
     - Ex: the following is not allowed:
        ```
        Import page.js
        Import foo from page.js
        ```
   - Do not create circular dependencies
     - Ex: the following is not allowed:
        ```
        // a.js
        Import b.js
        ```
        ```
        // b.js
        Import a.js
        ```
	
