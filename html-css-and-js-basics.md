# HTML, CSS, and JS Fundamentals

## HTML Basics
- HTML stands for hypertext markup language; used to add meaning to text and link documents to one another
- HTML specifies *how content is rendered*
- Tags
  - All content in an HTML document is located within a tag
  - There are many different tags, some of the most common are `<div>`, `<h>`, and `<p>`
  - It's good practice to put HTML inside an <html> tag
  - Tags can be placed inside other tags, like the example below
  - Note that all tags must have a starting and closing tag, except `<img>` 
- Basic structure of an HTML document:
  
  ```
   <!DOCTYPE html>
    <div>
      <p> A basic page! </p> 
    </div>
   </html>
  ```
 
 - IDs must be unique
 - General rule: don't put block inside of inline elements
 - Designate a primary language using: `<html lang="en">`
 - Use the `lang` tag

### Website Layout
- There are many ways to organize a website, grids and tables are most common

## CSS Basics
- CSS stands for cascading stylesheet 
- CSS specifies *how the content is visually styled*
- Used to format the design/look of a website, does not affect content of the website
- Benefits of CSS:
 - Reusability - can reuse the same stylesheet for multiple pages
 - Modularity - can organize it into components
 - Makes file management easy
 - Maintainability 
- CSS syntax
  - Selectors - specifies which element a rule applies to 
    - Element: what tag will be styled, ex. paragraphs
      - Can have many classes but only one ID
    - Class: html attribute, a type of element, `<div class='classNameHere'>`
    - ID: a specific element, ex. `#redtext { css-here }`
      - Can use IDs for navigation
    - Can be chained together to select things where all the conditions hold
  - Rules - specifies values with differing properties
  - Example of CSS h1 formatting:
     ```
     h1 {
      font-family: 'Arial';
      color: 'blue';
      background-color: #ff0000;
     }
    ```
 - CSS Properties
  - font-family, font-size, font-weight, color, background-color, opacity (transparency), and a lot more!
 - There are multiple ways to style a webpage:
  - Incline CSS - repetitive and considered bad practice
  - Internal - not prefered for similar reasons as above
  - External - preferred, best practice to separate it from .html file
 - Box Model 
  - Padding extends the content area
  - Border is similar
  - Margin is outside of the border and is intended to separate different elements from their neighbors
  
## Responsive Design
- There are many resolutions across devices and we should make sure that our website/application can adjust to them
- Responsive design vs. adaptive design
  - Responsive: 
    - Easier to maintain
    - Futureproof
    - Focus on "looking right"
    - Performance is worse than adaptive
  - Adaptive:
    - Can use JS to find out how someone is looking at your website
    - Specify with media queries
  
## Bootstrap
- Framework that makes development easier
  - Problems: can lead to similar-looking webpages, must load more files -> lower performance, stifles creativity
- Components - elements pre-arranged into common patterns
- Grid system: 
  - Rows are block elements
  - Columns are inline elements
  
## JavaScript
- Javascript is a programming language that specifies *function*
- JS is the standard for web programming

### History
- Originally named Mocha and renamed to Javascript as a marketing ploy because Java was being popularized at the time
- JS was intended to be a web language to run on any web platform
- ECMAscript is the standard for JS
- JavaScipt is not Java! Debugging depends on the execution environment, prototype based, used in every browser without a plugin

### Language Basics
- JS has functions and objects
- Variables are dynamically-typed
- Arithmetic: 
 
  `console.log("Hello, World!") //print to a separate console, not your webpage; can right-click your webpage and click "inspect"
   console.log('40' + 2); //will print '402'
   console.log('40' - 4); // will print 36
   var x = 'hello'; //value is string
   console.log("Hello, World!") //print to a separate console, not your webpage; can right-click your webpage and click "inspect"
   `
 - String are immutable in JS
 - Can call methods like in other languages using dot after the object name: `className = className.toUpperCase();`
 - JS arrays: 
    - Dynamically-typed so you don't need to specify it up front
    - Mutable 
    - Similar to Java
      `
        var numbers = [1,2,3];
        var things = ['rain', 2.5, true, [5,9,8]]; //arrays can be nested
        var blankStr = new Array(5); //empty array with 5 items
       `  
  - Accessing properties
    - Similar to other languages using dot feature `var name = person.firstName; //get value of firstName`
  - Functions
    - Similar to Java static methods 
    - Functions are objects in JS
    `
      //note that there isn't an access modifier
      function sayHello(name) {
        return "Hello, " + name;
      }
      //if you pass in nothing sayHello() output is "Hello, undefined"
      //if you pass in sayHello("inf133", "joe") output is "Hello, inf133"
     `
      
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  


@Copyright. Information obtained during UCI's INF133 course by Daniel Epstein.
