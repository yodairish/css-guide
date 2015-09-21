# Yodairish Sass Style Guide

*Guide which should be followed when updating or write a new project.*

**Version: 0.1.0**

## Table of Contents
  
  1. [Formatting](#formatting)
  1. [Postprocessor](#postprocessor)
  1. [Selectors](#selectors)
  1. [Reset](#reset)
  1. [Components](#components)
  1. [Colors](#colors)
  1. [Z-index](#z-index)
  1. [Font-size](#font-size)

##Formatting

  - Use 2 spaces indents.
  - 80 characters per line.
  - Always write semicolons.
  - Put blank lines between rule declarations.

  - Each rule on a new line.
 
  ```css
  // bad
  .rule1, .rule2:hover {
  }
  
  // good
  .rule1,
  .rule2:hover {
  }
  ```

  - Each property on a new line.

  ```css
  // bad
  .rule { color: #fff; font-size: 15px; }
  
  // good
  .rule {
    color: #fff;
    font-size: 15px;
  }
  ```
  
  - Use spaces and a new line to correct formatting:
    * Space before a opening braket.
    * New line after a opening braket.
    * Space after a property colon.
    * No space before a property colon.
    * New line before a closing braket.
  
  ```css
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
 
  ```css
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
 
  ```css
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

  ```css
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

##Postprocessor

  Don't use preprocessors!

  - We use [PostCSS](https://github.com/postcss/postcss).

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

  - **Syntax**: `<componentName>[--modifierName|__elementName]`.
 
  ```html
  <div class="dialog">
    <h2 class="dialog__title"></h2>
    <p class="dialog__text"></p>
    <button class="btn btn--success">OK</button>
  </div>
  ```
  
  - **Types**: components are devided into 2 types:
    * Basic: buttons, inputs..
    * Module: menu, login form.. can be simple or complex(i.e. contains inside other modules).

  - Prefer dashes over camelCasing.
  - Names should be abstract.
 
  ```html
  <!-- bad -->
  <ul class="leftMenu">
    
  </ul>
  
  <!-- good -->
  <ul class="vertical-menu">
    
  </ul>
  ```
  
  - Each component in a separate file.
 
##File structure

  - Use component approach:
    * Shared css in a 'style' folder.
    * Components files (css, js, html..) in a 'components' folder.
  
  ```
  style
  |-- variables
  |   |-- colors.css
  |   |-- fontSize.css
  |-- reset.css
  components
  |-- basic
  |   |-- input.css
  |   |-- button.css
  |-- header
  |   |-- style.css
  |   |-- index.js
  ```
  
##Variables

  - **Syntax**: `--<property>-<value>[--componentName]`.
  
  ```css
  :root {
    --margin-small--menu: 2px 4px;
  }

  .menu-button {
    margin: var(--margin-small--menu);
  }
  ```

##Colors

  - All colors should be stored in variables in a separate file. Names start with the prefix 'color'.
  
    ```css
    // color.css
    :root {
      --color-primary: #673ab7;
      --color-secondary: #9575cd;
    }
    
    // menu.css
    @import 'color.css';
    
    .menu {
      background-color: var(--color-primary);
    }
    ```
  
  - Use HEX for colors. Letters in lowercase.
  
    ```css
    // bad
    --color-primary: rgb(103, 58, 183);
    
    // bad
    --color-primary: #673AB7;
    
    // good
    --color-primary: #673ab7;
    ```
  
  - Use 3 letter notation where possible.
  
    ```css
    // bad
    --color-primary: #aabbcc;
    
    // good
    --color-primary: #abc;
    ```
    
  - Use abstract names.
  
    ```css
    // bad
    --color-red: #f00;
    --color-menu: #9575cd;
    
    // good
    --color-secondary: #9575cd;
    ```

## Z-index

  - Use 10 values of z-index which stored in a separate file.

  ```css
  // z-index.css
  :root {
    --z-index-1: 100;
    --z-index-2: 200;
    ...
    --z-index-10: 1000;
  }
  
  // menu.css
  @import 'z-index.css';
  
  .menu {
    z-index: var(--z-index-3);
  }
  ```

## Font-size

  - Use `px` unit for font size.
  - Use for font size values range from micro to giant. Stored in a separate file.
  
  ```css
  // font-size.css
  --font-size-micro: 7px;
  ..
  --font-size-small: 10px;
  ..
  --font-size-medium: 16px;
  ..
  --font-size-big: 27px;
  ..
  --font-size-giant: 50px;
  
  // menu.css
  @import 'font-size.css';
  
  .menu {
    font-size: --font-size-medium;
  }
  ```

## License

MIT © Yodairish 2015
