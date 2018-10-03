# HTML and CSS Fundamentals

I. HTML
II. CSS

## HTML Basics
- HTML stands for hypertext markup language; used to add meaning to text and link documents to one another
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
 

### Supporting Multiple Languages in HTML
- Designate a primary language using: `<html lang="en">`
- Use the `lang` tag

## CSS Basics
- CSS stands for cascading stylesheet 
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
 - Can do inline CSS but it's generally considered bad practice because it can be repetitive
  



@Copyright. Information obtained during UCI's INF133 course by Daniel Epstein.
