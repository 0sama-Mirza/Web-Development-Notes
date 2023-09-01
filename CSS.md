# In CSS you can animate change color of the background but here I will just focus on the website layout and some tricks that are needed alot
# 1. How to add background:
```CSS
html,body {
    width: 100%;
    height: 100%;
    background: url("image.png") fixed;
    background-repeat: no-repeat;
    background-size: cover;
    margin: 0;   
}
```
# 2. How to add fonts:
## Local Fonts:
```CSS
@font-face {
    font-family: "Custom-Font-Name"; 
    src: url("FontFile.ttf") format("truetype");
    /* OR */
    src: url("FontFile.otf") format("opentype");
}
```
## Google Fonts:
### Go [Here](https://www.w3schools.com/howto/howto_google_fonts.asp) and copy the text below, paste it into your <head> tag in the HTML:

```CSS
<link href='https://fonts.googleapis.com/css?family=Sofia' rel='stylesheet'>
```

# 3. How to make website responsive:
```CSS
@media only screen and (max-width: 810px) {
	/* Add the rest here */
}
```
[CSS Tricks For Responsive Website](https://css-tricks.com/snippets/css/media-queries-for-standard-devices/)

# 4. How to remove bullet points from lists and make them horizontal:
```CSS
li {
	list-style: none;
	display: inline-block;
}
```
# 5. px vs em vs rem Explained!:
### 1. px:
- Simply pixels.
- Fixed size.
### 2. em:
- x time the containing element e.g:
#### HTML:
```HTML
<p><span>Hello There!</span>How are you all doing today?</p>
```
#### CSS:
```CSS
p {
font-size: 20px;
}
span {
font-size: 2em;
}
```
So here Hello There! = 2*20 = 40px.
### 3. rem:
- Relative To The Root Element Which Is Most Likely ``<html>`` tag.  


# 6. CSS Selectors Explained By ChatGPT:
1. `.class`: This selector targets elements with a specific class attribute. For example, `.header` would target any element with `class="header"`.

2. `#id`: This selector targets a specific element with a unique ID attribute. For example, `#main-title` would target the element with `id="main-title"`.

3. `*`: The universal selector matches any element.

4. `element`: This selector targets all instances of a specific HTML element, like `p` for paragraphs or `div` for divisions.

5. `element, element`: Targets all instances of multiple elements. For example, `h1, h2` would target both `h1` and `h2` elements.

6. `element element`: Targets an element that is a descendant of another element. For example, `ul li` targets `li` elements within a `ul`.

7. `element > element`: Targets an element that is a direct child of another element. For example, `ul > li` targets `li` elements that are direct children of a `ul`.

8. `element + element`: Targets an element immediately preceded by another element. For example, `h2 + p` targets a `p` element directly following an `h2`.

9. `:hover`: Targets an element when the mouse pointer hovers over it.

10. `:last-child`: Targets the last child element of its parent.

11. `:first-child`: Targets the first child element of its parent.

12. `!important`: A declaration with this keyword has the highest specificity and cannot be overridden by other styles. It is often used to give a style precedence.

**Cascade Priority:**

1. **Specificity**: The more specific a selector is, the higher its priority. Inline styles have the highest specificity, followed by IDs, classes, and elements. For example, `#main-title` has higher specificity than `.header`.

2. **Importance**: Styles marked with `!important` have the highest priority, regardless of specificity. However, it's generally recommended to use `!important` sparingly, as it can lead to difficult-to-maintain code.

3. **Source Order**: If two selectors have the same specificity and importance, the one that appears later in the stylesheet takes precedence. This is the order in which the styles are applied based on where they appear in the CSS file.

In summary, when multiple styles apply to the same element, the cascade is determined by their specificity, importance, and source order. It's important to have a good understanding of these concepts to control how styles are applied to your HTML elements.
# 7. Flex-Box And CSS-Grid:
## [Flex-Box Frog Website](https://flexboxfroggy.com/)
## [CSS Tricks Teaching Flex-Box](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
## [CSS Tricks Teaching CSS-Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)
## [Add Vendor Prefixes Into Your CSS](https://autoprefixer.github.io/)
## [CSS-Grid Cheat Sheet](https://grid.malven.co/)

# 8. Now learn [[Javascript]]