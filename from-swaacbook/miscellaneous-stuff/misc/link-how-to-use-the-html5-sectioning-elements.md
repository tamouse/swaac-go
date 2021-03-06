
# Table of Contents

1.  [Link: How to Use the HTML5 Sectioning Elements](#link-how-to-use-the-html5-sectioning-elements)
    1.  [The section elements discussed](#the-section-elements-discussed)


<a id="link-how-to-use-the-html5-sectioning-elements"></a>

# Link: How to Use the HTML5 Sectioning Elements

-   published date: 2015-03-05 21:34
-   keywords: ["html", "html5", "links", "sectioning", "tutorials"]
-   source:
-   link: {"href"=>"<http://blog.teamtreehouse.com/use-html5-sectioning-elements>", "title"=>"How to Use The HTML5 Sectioning Elements", "date"=>"February 18, 2014", "author"=>{"name"=>"Matt West", "url"=>"<http://mattwest.io>"}}
-   links: {"main<sub>element</sub>"=>{"text"=>"HTML 5.1 4.4. Grouping content - The main element", "title"=>"The main element is not sectioning content and has no effect on the document outline", "href"=>"<https://www.w3.org/TR/html51/grouping-content.html#the-main-element>"}, "html5<sub>sections</sub>"=>{"text"=>"HTML 5.1 4.3. Sections", "href"=>"<https://www.w3.org/TR/html51/sections.html#sections>"}, "html5<sub>grouping</sub>"=>{"text"=>"HTML 5.1 4.4. Grouping content", "href"=>"<https://www.w3.org/TR/html51/grouping-content.html#grouping-content>"}, "html5<sub>aria</sub>"=>{"text"=>"HTML 5.1 3. Semantics, structure, and APIs of HTML documents- WAI-ARIA tags", "href"=>"<https://www.w3.org/TR/html51/dom.html#wai-aria>"}}

Matt provides a great little tutorial on the sectioning elements in HTML5; what they're for and when to use them.

The article may be a year old, but the information is still current. Sectioning HTML pages is important for understanding the structure of a page. While most visual users will never notice, those using screen readers and voice over/text-to-speech systems will. They also provide a good sense for designing the elements of a page, and thinking about the content you're creating.


<a id="the-section-elements-discussed"></a>

## The section elements discussed

-   **main:** The `main` element represents the main content of the body of a document or application. (`main` is not one of the sectioning elements but it is still important to use. See: {% include link.html link=page.links.main<sub>element</sub> %})

-   **article:** The `article` element represents a complete, or self-contained, composition in a document, page, application, or site. This could be a magazine, newspaper, technical or scholarly article, an essay or report, a blog or other social media post.

-   **section:** The `section` element represents a generic section of a document or application. A section, in this context, is a thematic grouping of content. Each section should be identified, typically by including a heading (`h1-h6` element) as a child of the `section` element.

-   **nav:** The `nav` element represents a section of a page that links to other pages or to parts within the page: a section with navigation links.

-   **aside:** The `aside` element represents a section of a page that consists of content that is tangentially related to the content of the parenting sectioning content, and which could be considered separate from that content. Such sections are often represented as sidebars in printed typography.

-   **header:** The `header` element represents introductory content for its nearest ancestor sectioning content or sectioning root element. A header typically contains a group of introductory or navigational aids.

-   **footer:** The `footer` element represents a footer for its nearest ancestor sectioning content or sectioning root element. A footer typically contains information about its section such as who wrote it, links to related documents, copyright data, and the like.

-   **address:** The `address` element represents the contact information for its nearest `article` or `body` element ancestor. If that is the `body` element, then the contact information applies to the document as a whole.

Great quote at the end:

> **\*** Final Thoughts on the Sectioning Elements
> 
> :CUSTOM<sub>ID</sub>: final-thoughts-on-the-sectioning-elements

> In this post you've learned how to use the HTML5 sectioning elements when marking up your web pages. Using these elements has a number of benefits. One of the biggest being that it gives certain areas of your page more semantic meaning, allowing computer programs to identify key elements like the main content and page navigation. This information is extremely useful to applications like screen readers.

Additional useful links about HTML5 Sectioning:

<div class="HTML">
<ul>

</div>

<div class="HTML">
<li>

</div>

{% include link.html link=page.links.html5<sub>sections</sub> %}

<div class="HTML">
</li>

</div>

<div class="HTML">
<li>

</div>

{% include link.html link=page.links.html5<sub>grouping</sub> %}

<div class="HTML">
</li>

</div>

<div class="HTML">
<li>

</div>

{% include link.html link=page.links.html5<sub>aria</sub> %}

<div class="HTML">
</li>

</div>

<div class="HTML">
</ul>

</div>

