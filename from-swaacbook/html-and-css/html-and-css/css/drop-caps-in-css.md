# Drop Caps in CSS

* published date: 2013-08-25 19:44
* keywords: \[“css”, “design”, “drop-caps”, “howtos”, “swaac”\]

**CSS** is a powerful little language for specifying all sorts of things you can do with layouts and elements on a web page. Here we look at bringing an old typography trick for books to the modern web: **Drop Caps**.

Drop Caps are pretty much what the name implies: the first letter of a paragraph is enlarged and dropped to the left of the first paragraph on the page. This is seen in books, newspapers, and magazines all over. It is a classic design trick that can be successfully brought to a web page to give it a bit of elegance.

#### Example: [Drop Caps](https://codepen.io/tamouse/pen/vYBZxqG) a pen by [Tamara Temple](https://codepen.io/tamouse)

Of course, there's a much earlier example of someone else doing this as well: [https://css-tricks.com/snippets/css/drop-caps/](https://css-tricks.com/snippets/css/drop-caps/) from 2010

### Cross-browser method

This is the not-a-trick method that will work in all browsers. Create a `span` with a class that denotes the letter to be drop-capped.

```text
<p><span class="dropcap">L</span>orem ipsum dolor sit amet,
consectetur adipisicing elit, sed do eiusmod tempor incididunt ut
labore et dolore magna aliqua. Ut enimad minim veniam, quis nostrud
exercitation ullamco laboris nisi ut aliquip ex ea commodo
consequat. Duis aute irure dolor in reprehenderit in voluptate velit
esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat
cupidatat non proident, sunt in culpa qui officia deserunt mollit anim
id est laborum.</p>
```

### :first-letter pseudo-class

The trick is to use the pseudo-class `:first-letter` on the paragraph you are styling. This selector allows you to just pick the first letter off a paragraph without the need for spans. The HTML is almost identical:

```text
<p class="dropcap">Lorem ipsum dolor sit amet,
consectetur adipisicing elit, sed do eiusmod tempor incididunt ut
labore et dolore magna aliqua. Ut enimad minim veniam, quis nostrud
exercitation ullamco laboris nisi ut aliquip ex ea commodo
consequat. Duis aute irure dolor in reprehenderit in voluptate velit
esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat
cupidatat non proident, sunt in culpa qui officia deserunt mollit anim
id est laborum.</p>
```

I like this version better because it is describing something that will be happening to this paragraph, rather than calling out something specific on a particular span within the paragraph.

### The CSS

It turns out the CSS will not be different using both the cross-browser \(span\) and the CSS3 selector.

```text
span.dropcap, p.dropcap:first-letter {
    font-size: 200%;
    font-weight: bold;
    float: left;
    padding: 5px;
    border: 3px solid blue;
    margin: 5px;
    height: 50px;
    width: 50px;
    color: blue;
    text-align: center;
}
```

The letter is given a type face and size commensurate with a dropped cap in this design. We make it big and bold. Next comes the tricky part: we make this character float left on the paragraph. This is what makes it a drop cap. When you float the character, it becomes a block display, and drops down compared to the rest of the first line.

But now we’re going to make it a little prettier.

We give the letter some nice padding, center the text, and put a solid box around it. We make the border and the text colour blue \(I like blue!\). We set the width and height to make the box square, and add a bit of margin to it.

You may need to nudge this around based on your other padding and margins.

The next step will be to make this drop cap more ornate. Book of Kells, anyone?

##  <a id="item-title"></a>

