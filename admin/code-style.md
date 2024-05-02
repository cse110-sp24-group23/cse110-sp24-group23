# Team 23 Code Style Guide

## Table of contents:


1. [Naming](#naming)
2. [Documentation](#documentation)
3. [Code Format](#code-format)
4. [Code Practices](#code-practices)

### Terminology Note:

- Must = absolute requirement
- Should = recommended. There may be valid exceptions to the rule, but these are weighed and chosen deliberately
- May = optional

## Naming

These rules apply for all names you will be writing. Make Sure you adhere to the appropriate Language Naming Conventions.

- File names
- Function/method names
- Variable names
- Class names
- etc.

### Rules:

Note: examples are given for JavaScript. Use correct naming conventions for each language.

- Names should be descriptive
  - Some few exceptions apply (like `i` in very simple for loops), but it is almost always better to use descriptive names, even inside loops.
    - Ex: use `rowIndex`, and `colIndex` instead of `i` and `j` while accessing a matrix with nested for loops.
- Names may include short forms but only in very obvious/common scenarios
  - Ex: `getNumTeammates()` instead of `getNumberOfTeammates()`
  - A short form should not have multiple likely full forms
    - Ex: `getRes()` is not an acceptable function name, since it could mean getResolution or getResponse
- Names must only contain letters, dashes, and underscores (and period for file extensions)
- Names must follow the following naming conventions.

### Naming Conventions:

- File names must be all lowercase with hyphens to separate words
  - Ex: `admin-auth.html`

#### HTML

- Try to keep file names to single names
  - Ex: `home.html`, `contact.html`, `login.html`

#### CSS

- Try to keep file names to single names
  - Ex: `home.css`, `contact.css`, `login.css`
- Use js-class names to denote a relationship with a DOM element
  - This allows for CSS class names and style to be updated without JS functionality breaking
  - Ex:
    ```
    <!--HTML File-->
    <div class="site-navigation js-site-navigation">...</div>
    ```
    ```
    /* CSS File */
    .site-navigation {   /* uses normal class name */
      border-bottom: 2px solid black;
    }
    ```
    ```
    // JavaScript File
    // uses js class name
    const nav = document.querySelector('.js-site-navigation')
    ```

#### JavaScript

- Most names (except file names) should be lowerCamelCase
  - variables, functions, properties, etc.
  - Ex: `thisVariableHasManyWords`, `getUserProfile()`
- Helper functions must have an underscore before them, denoting that they are private
  - Ex: `_constructionHelper()`
- constants should be all uppercase with underscores separating words (snake case)
  - Ex: `const PORT = 3000`, `const DAYS_PER_WEEK = 7`
  - This does not apply to everything with the `const` keyword. Ex: `const user_input = _getUserInput()` is valid
- Booleans must be named with ‘is’ or ‘has’ as a prefix
  - Ex: `isEmpty` or `hasPermission`
- Classes and components (if using a frontend framework like React) must use UpperCamelCase
  - Ex: `class UserProfile(firstName, lastName)`, `let softwareDev = new SoftwareDeveloper()`

## Documentation

- Each user function must have a multiline comment in the following form
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

## Code Format

- Single lines of code must not exceed 100 characters unless they are imports
- Indentations must be 4 spaces, not tabs
- For JavaScript, HTML, and CSS Use [prettier with VS Code](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) with tabWidth = 4 for general formatting. Find information on how to set it up [here](https://scottsauber.com/2017/06/10/prettier-format-on-save-never-worry-about-formatting-javascript-again/). Here is what the settings.json should look like after installing the prettier VS Code extension:
  ```
  {
      "[javascript]": {
          "editor.defaultFormatter": "esbenp.prettier-vscode"
      },
      "[html]": {
          "editor.defaultFormatter": "esbenp.prettier-vscode"
      },
      "[css]": {
          "editor.defaultFormatter": "esbenp.prettier-vscode"
      }
  }
  ```

## Code Practices

- KEEP CODE READABLE
- Follow the proper coding practices for each language. These are defined as follows:

### HTML

- Avoid generalized tags like `div` and `span`. Use appropriate tags instead (`input`, `section`, `p`, etc.)
- Use only one `h1` tag per page. This helps with search engine optimization.
- Do not skip heading levels while using header tags. This confuses screen readers
  - Ex:
    Don't do this:
    ```
    <h1>Main Header</h1>
    <h3>Next Header</h3>
    ```
    Do this:
    ```
    <h1>Main Header</h1>
    <h2>Next Header</h2>
    ```
- Use `figure` tags for adding captions to images
  - Ex:
    ```
    <figure>
      <img src=“a-man-coding.jpg” alt=“A man working on his computer”>
      <figcaption> This is a picture of a man working on his computer</figcaption>
    </figure>
    ```
- Don't use `b` and `i` tags. Use `strong` and `em` tags instead.
- Don't place block level elements inside inline elements
  - Ex:
    Don't do this:
    ```
    <a href="#">
      <p> click this link </p>
    <a>
    ```
    Do this instead:
    ```
    <p>
      <a href="#"> click this link </a>
    <p>
    ```

### CSS

- Use [variables](https://www.w3schools.com/css/css3_variables.asp) in CSS for colors, dimensions, etc.
  - Ex:
    ```
    /* Defining variables */
    :root {
      --blue: #6495ed;
      --white: #faf0e6;
    }
    /* Using variables */
    body {
      background-color: var(--blue);
    }
    ```
- Avoid excessive nesting
  - Ex:
    Don't do this:
    ```
    div#container > ul.navigation li.active a.btn-primary span.icon {
      /* CSS rules */
    }
    ```
    Instead, use proper selectors (like classes):
    ```
    .nav-link {
      /* CSS rules for navigation links */
    }
    ```
- Avoid using the !important property
  - Instead, leverage [CSS specificity rules](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity)
- Modularize CSS - break styles into small, reusable components

  - Ex:

    ```
    /* Button Module */
    .button {
      /* Button styles */
    }

    /* Navigation Module */
    .navbar {
      /* Navbar styles */
    }
    ```

- Add comments to non obvious styles

  - Ex:

    ```
    .box {
      /* NOTE: Not necessary to comment: */
      background: var(--brown);
      width: var(--box-width);

      /* NOTE: Should comment: */
      // Use flex for alignment (1-3)
      display: flex; // 1. allow flex styles
      align-items: center; // 2. vertically center contents
      justify-content: center; // 3. horizontally center contents

      // Hover/focus state
      @include hover-focus() {
        color: var(--box-highlight-color);
        text-decoration: none;
        outline: 0;
    }
    ```

### JavaScript

- Variables
  - When declaring a variable, always use `let` or `const`. Do not use `var`. For more information on their differences, check out this [article](https://www.freecodecamp.org/news/var-let-and-const-whats-the-difference/).
    - Ex: `let numUsers = 45`
- Functions
  - Use helper functions to do sub-tasks.
  - A lower level helper function should perform one task
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
  - Avoid ‘hacky’ use of global variables. If you need to edit a variable with several functions, consider passing it in as an argument instead.
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
