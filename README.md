# Yodairish Sass Style Guide

*Guide which should be followed when updating or write a new project.*

**Version: 0.1.0**

## Table of Contents
  
  1. [Formatting](#formatting)
  1. [CSSDoc](#cssdoc)
  1. [Preprocessor](#preprocessor)
  1. [Selectors](#Selectors)
  1. [Reset](#reset)
  1. [Components](#components)
  1. [Colors](#colors)
  1. [Z-index](#z-index)
  1. [Font-size](#font-size)

##Formatting

  - Use 2 spaces indents.
  - 80 characters per line.
  - Always write semicolons.

  - Each rule on a new line.
 
  ```scss
  // bad
  .rule1, .rule2:hover {
  }
  
  // good
  .rule1,
  .rule2:hover {
  }
  ```

  - Each property on a new line.

  ```scss
  // bad
  .rule { color: #fff; font-size: 15px; }
  
  // good
  .rule {
    color: #fff;
    font-size: 15px;
  }
  ```
  
  - Use spaces and new line to correct formatting:
    * Space before a opening braket.
    * New line after a opening braket.
    * Space after a property colon.
    * No space before a property colon.
    * New line before a closing braket.
  
  ```scss
  // bad
  .rule{
    color:#fff;
    font-size : 15px;
  }
  
  // good
  .rule {
    color: #fff;
    font-size: 15px;
  }
  ```
  
  - Use shorthand properties where possible.
 
  ```scss
  // bad
  .rule {
    padding-top: 5px;
    padding-bottom: 2px;
    padding-left: 10px;
    padding-right: 15px;
  }
  
  // good
  .rule {
    padding: 5px 15px 2px 10px;
  }
  ```
  - Omit unit specification after 0 values.
 
  ```scss
  // bad
  .rule {
    margin: 0px;
  }
  
  // good
  .rule {
    margin: 0;
  }
  ```
  
  - Omit leading “0”s in values.

  ```scss
  // bad
  .rule {
    opacity: 0.5;
  }
  
  // good
  .rule {
    opacity: .5;
  }
  ```
  
  - Ordering properties meaningfully.
  - **Comments**:
    - Use `//` for single line comments.
    - Use `/* ... */` for multiline comments.

##CSSDoc

  - Now we use [CSSG](http://operatino.github.io/MCSS/en/modules/cssg.html); and thinking about [KSS](https://github.com/kneath/kss/blob/master/README.md).
  
  ```scss
  /*
    post
        post_header
            post_header_name
            post_header_date

        post_body
            ...
  */
  
  .post {
    ...
  }
  .post-header {
    ...
  }
  .post-header-name {
    ...
  }
  ```

##Preprocessor

  - Now we use [Sass](http://sass-lang.com/)
  - All imports at the top of the file.
  - Don't use nesting.
  - Don't use extend.
  - Don't use mixin. This is good for browser-specific, but you should use [autoprefixer](https://github.com/postcss/autoprefixer).

##Selectors
  
  - Don't use ID's for styling.
  - Don't use Tags for styling.

  - **JS Selector**: for javascript use specific class with prefix `js-`. Don't use this class for styling.

  ```html
  <button class="btn js-login">Login</button>
  ```
  
  - **State**: for state-based component use specific class with prefix `is-`.
  
  ```html
  <ul class="menu">
    <li class="menu-item">Item 1</li>
    <li class="menu-item is-active">Item 2</li>
  </ul>
  ```

##Reset

  - Use [HTML5 doctor reset file](http://www.cssreset.com/scripts/html5-doctor-css-reset-stylesheet/).

##Components

  - **Syntax**: `<componentName>[--modifierName|-elementName]`
 
  ```html
  <div class="dialog">
    <h2 class="dialog-title"></h2>
    <p class="dialog-text"></p>
    <button class="btn btn--success">OK</button>
  </div>
  ```
  
  - **Types**: components are devided into 2 types:
    * Basic: buttons, inputs..
    * Module: menu, login form.. can be simple or complex(i.e. contains inside the other modules).

  - Use camelCase for naming. Names should be abstract.
 
  ```html
  <!-- bad -->
  <ul class="left-menu">
    
  </ul>
  
  <!-- good -->
  <ul class="verticalMenu">
    
  </ul>
  ```
  
  - Each component in a separate file with the same name.
 
##File structure

  - Use component approach:
    * Shared scss are in a 'style' folder.
    * Shared js are in a 'js' folder. 
    * Componetns files (scss, js, html..) are in a 'components' folder
  
  ```
  style
  |-- variables
  |   |-- colors.scss
  |   |-- fontSize.scss
  |-- reset.css
  js
  |-- constants
  |   |-- sound.js
  |-- parser.js
  components
  |-- basic
  |   |-- input.scss
  |   |-- button.scss
  |-- header
  |   |-- header.scss
  |   |-- header.js
  ```
  
##Variables

  - **Syntax**: `<property>-<value>[--componentName]`
  
  ```scss
  $margin-small--menu: 2px 4px;
  ```

##Colors

  - All colors should be stored in variables in a separate file. Names start with the prefix 'color'.
  
    ```scss
    // color.scss
    $color-primary: #673ab7;
    $color-secondary: #9575cd;
    
    // menu.scss
    @import 'color';
    
    .menu {
      background-color: $color-primary;
    }
    ```
  
  - Use HEX for colors. Letters in lowercase.
  
    ```scss
    // bad
    $color-primary: rgb(103, 58, 183);
    
    // bad
    $color-primary: #673AB7;
    
    // good
    $color-primary: #673ab7;
    ```
  
  - Use 3 letter notation where possible
  
    ```scss
    // bad
    $color-primary: #aabbcc;
    
    // good
    $color-primary: #abc;
    ```
    
  - Use abstract names
  
    ```scss
    // bad
    $color-red: #f00;
    $color-menu: #9575cd;
    
    // good
    $color-secondary: #9575cd;
    ```

## Z-index

  - Use the 10 values of z-index which stored are stored in a separate file.

  ```scss
  // zIndex.scss
  $zIndex-1: 100;
  $zIndex-2: 200;
  ...
  $zIndex-10: 1000;
  
  // menu.scss
  @import 'zIndex';
  
  .menu {
    z-index: $zIndex-3;
  }
  ```

## Font-size

  - Use `px` unit for font size.
  - Use for font size values range from micro to giant. Stored in a separate file
  
  ```scss
  // fontSize.scss
  $fontSize-micro: 7px;
  ..
  $fontSize-small: 10px;
  ..
  $fontSize-medium: 16px;
  ..
  $fontSize-big: 27px;
  ..
  $fontSize-giant: 50px;
  
  // menu.scss
  @import 'fontSize';
  
  .menu {
    font-size: $fontSize-medium;
  }
  ```

## License

MIT © Yodairish 2014
