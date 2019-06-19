# CSS

## CSS

Cascading Style Sheets \(CSS\) is a style sheet language used for describing the presentation of a document written in a markup language like HTML.

## CSS3 New Features

* Media Query
* Selector
* Round Corner
* Transform
* Multicolumn Layout

## Box Model

All HTML elements can be considered as boxes. In CSS, the term box model is used when talking about design and layout. The CSS box model is essentially a box that wraps around every HTML element. It consists of **margin, border, padding and context**. 

## Position

* Static
  * This is the default value, all the elements are in order as they appear in the document
* Fixed
  * The element is positioned relative to its normal position
* Absolute
  * The element is positioned absolutely to its first positioned parent
* Relative
  * The element is positioned related to the browser window
* Sticky
  * The element is positioned based on the user's scroll position

## Display

* Inline
* Block
  * It will change the width and height based on the settings, and block the lane for wrapped content
* Inline-Block
  * It will deal better both has the width and height setting and keep wrapped content in line

## Display: none vs Visibility: hidden

Display: none - means that the tag will not appear on the page at all, although you can still interact with it through the DOM. There will be no space allocated for it between the other tags.

Visibility: hidden - means that unlike display: none, the tag is not visible, but space is allocated for it on the page. The tag is rendered, it just isn't seen on the page. 

## CSS Selectors

## Specificity Rules

* Equal specificity: the latest rule counts
* ID selectors have a higher specificity than attribute selectors
* Contextual selectors are more specific than a single element selector
* A class selector beats any number of element selectors
* The universal selector and inherited values have a specificity of 0

inline style &gt; ID selector &gt; class, attribute and pseudo-class selector &gt; tag and pseudo-element selector

## Responsive Design

* Media query 
  * Media query made it possible to define different style rules for different media types. By using media query, we can do responsive web design to handle different devices' viewport. 
* Flexbox 
  * Need a container with attributes display: flex, flex-direction: column/row\(-reserve\), flex-wrap: \(no\)wrap\(-reverse\), flex-flow: setting both the flex-direction and flex-wrap

## Media Query 

It uses the @media rule to include a block of CSS properties only if a certain condition is true. In order to implement Responsive Design to adapt different screen. 

## CSS Grid vs Flex-box

* CSS Grid Layout is a two-dimensional system, meaning it can handle both columns and rows, unlike flex-box which is largely a one-dimensional system either in a column or a row
* CSS Grid's approach is layout-first while flex-box's approach is content-first
* Flex-box layout is most appropriate to the components of an application and small-scale layouts, while the Grid layout is intended for larger scale layouts which aren't linear in their design
* Flex-box is for defining a layout as a row or a column, whereas Grid is for defining a grid and fit content into it in two-dimensions

Shorthand for using Flex-box: performance issues and browser compatibility. 

## Animation vs Transition

Animations within CSS3 allow the appearance and behavior of an element to be altered in multiple keyframes. Transitions provide a change from one state to another, while animations can set multiple points of transition upon different keyframes. 

## Pseudo Class

* It is used to define a special state of an element 
* Active, checked, disabled, first-child, link, visited
* Pseudo elements: after, before, first-letter, first-line, selection

## Pseudo elements

A CSS pseudo-element is a keyword added to a selector that lets you style a specific part of the selected element. e.g. :first-letter, :before, :after.

## CSS Preprocessors - pros & cons

Advantages: 

* CSS is made more maintainable
* Easy to write nested selectors
* Variables for consistent theming. Can share theme files across different projects
* Mixins to generate repeated CSS
* Splitting your code into multiple files. CSS files can be split up too but doing so will require an HTTP request to download each CSS file

Disadvantages:

* Requires tools for preprocessing. Re-compilation time can be slow

## Mixin in SASS / SCSS

A mixin lets you make groups of CSS declarations that you want to reuse throughout your site. You can even pass in values to make your mixin more flexible. A good use of a mixin is for vendor prefixes. 

## Z-index

The z-index property specifies the stack order of an element. An element with greater stack order is always in front of an element with a lower stack order. z-index only works on positioned elements. 

## How to add a padding but not influence the box size

`box-sizing: border-box`;

## Accessibility

* Test size for different device resolution and user's distance
* Setting line height to make text better readable and visually more appealing
* Add @media block to tweak the styling of elements, like set a static header and hide the ads. 

## How many px is equal to 1 rem

Rem is a new feature for CSS3, which stands for root em. It's equal to the computed value of font-size on the root element, the rem units refer to the property's initial value. This means that 1rem equals the font size of the HTML element, which for most browser has a default value of 16px.

