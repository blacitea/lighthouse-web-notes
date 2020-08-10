# HTML - HyperText Markup Language
- index is the default, the thing in control of what's going on, engine will search for index first by default
- Why semantic tags?
  - other devs
  - google bot
  - screen reader
- meta : information above information, put them in the head section
- sibling - element in the same level (with the same parent element)
- always only ONE parent, unlimited no. of child & siblings

  ## Attributes
  - Extra information, inside any element *openning tag* , data attributes, classes, ids
  - <img> Don't give your img both width & height, browser to aspect, just 1 and it will auto adjust the other, alt is in case the img cannot load, a msg
  - if it gets too long, just put them one on each line (spacing!)
  - data attribute : data-userid = "7" data-whatever="something"  <= we can retreive it with js afterwards, it is hidden from viewer
# CSS - Cascading Styles Sheets
- 1 em = 1 times parent's font size  (regular font size 16px)
- *{ box-sizing : border-box;} (content + padding + border)
- declarative programing language, ask it to do something, no tell it how to do it
- styles apply top from bottom
- parent styles apply to the child
- the style below will override the one from above
- SASS?
- user agent stylesheet = browser built in style

  * style attributes inside element tags / inline style !! This is the worst
    * style="border: 2px; font-size: 5px;"
    * cannot be override, hard to maintain, html mixed up with css
  * style tag inside head
    * <style>
    *   h2 {        <= selector , apply the style to everything match with the selector
    *      border: 5px solid magenta;
    *   }
    * </style>
    * <.> for class, <#> for id
  * external stylesheet (style.css)
    * tell your html to grab the css style rules externally
    * put it inside the <head> tag
    * <link rel="" href="">
      * rel - relationship - "stylesheet"
      * href - where is it? = "styles.css"
      * bring in other's style first, then bring in your own (yours at the bottom, so it is the most important)
    * Reset vs Normalize
      * Reset set everything to zero!
      * Normalize keep some style, just make it normal

## Padding
- push the content away from the box border