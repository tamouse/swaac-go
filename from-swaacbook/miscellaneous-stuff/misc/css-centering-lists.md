
# Table of Contents

    1.  [Codepen Snippet](#codepen-snippet)
    2.  [A double wrapper](#a-double-wrapper)
    3.  [CSS magic isn't](#css-magic-isnt)
1.  [Update: Wed Jul 27 08:55:22 2016](#update-wed-jul-27-085522-2016)
    1.  [Centering Font Icons in Circles](#centering-font-icons-in-circles)
    2.  [Codepen Snippet](#codepen-snippet-1)
    3.  [Using Plain Old CSS](#using-plain-old-css)

A common issue folks encounter in CSS land is the vertical and horizontal centering of something that the exact height and width cannot be predetermined.

Over on [css-tricks](https://css-tricks.com/), there's a general set of guidelines to do this. I prefer [this solution](https://css-tricks.com/centering-css-complete-guide/#both-unknown) over the others mentioned.

Sometimes it's a bit unclear still what to do when you have a list of items to center as a unit such as social icons or images.

Here's an example of doing that:


<a id="codepen-snippet"></a>

## Codepen Snippet

<div class="HTML">
<p data-height="449" data-theme-id="light" data-slug-hash="YWvpOo" data-default-tab="result" data-user="tamouse" data-embed-version="2" class="codepen">

</div>

See the Pen CSS Centering Lists Hrz & Vrt by Tamara Temple (@tamouse) on CodePen.

<div class="HTML">
</p>

</div>

<div class="HTML">
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>

</div>


<a id="a-double-wrapper"></a>

## A double wrapper

In the example, there's a section on the page that's being used to show "cases" for something (for example, use cases for a tool, portfolio example boxes, site features, etc). Inside are the actual cases. To make the cases stay together while centering the set of them in the section, I've placed a wrapper div around the set of cases (and their header).

{% highlight html linenos %}

<div class="HTML">
<section class="cases">

</div>

    <heading>
      <h2>Use Cases</h2>
    </heading>
    <div class="case">
      <img src="http://placekitten.com/50"><br> You love it!
    </div>
    <div class="case">
      <img src="http://placekitten.com/50"><br> You love it!
    </div>
    <div class="case">
      <img src="http://placekitten.com/50"><br> You love it!
    </div>

<div class="HTML">
</section>

</div>

{% endhighlight %}


<a id="css-magic-isnt"></a>

## CSS magic isn't

The CSS uses the relative parent and absolute child, making the `cases` section the parent and `cases-wrapper` the child.

{% highlight css linenos %} // reset should be done first .cases { postiion: relative; } .case-wrapper { position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); background-color: #ddffdd; padding: 10px; } .case { display: inline-block; padding: 10px; margin: 0; text-align: center; font-weight: bold; background-color: #eee; } {% endhighlight %}


<a id="update-wed-jul-27-085522-2016"></a>

# Update: Wed Jul 27 08:55:22 2016


<a id="centering-font-icons-in-circles"></a>

## Centering Font Icons in Circles

We had an additional problem of centering font icons in a circle. Originally we banged away with `text-align` and `line-height` but that's rather pointless if anything changes very much (including viewport).

So back to the CSS way. Doing this in Sass by using a mixin ends up being rather easy. Using Sass, create a couple of mixins:

{% highlight scss linenos %} @mixin center-parent { position: relative; } @mixin center-child { position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); } {% endhighlight %}

In this case, we set up the HTML in much the same way:

{% highlight html linenos %}

<div class="HTML">
<h3 class="icon-list-caption">

</div>

Follow me on:

<div class="HTML">
</h3>

</div>

    <div class="icon-list">
      <div class="icon-item">
        <div class="icon fa fa-facebook"></div>
        <div class="icon-text">Facebook</div>
      </div>
      <div class="icon-item">
        <div class="icon fa fa-github"></div>
        <div class="icon-text">Github</div>
      </div>
      <div class="icon-item">
        <div class="icon fa fa-twitter"></div>
        <div class="icon-text">Twitter</div>
      </div>
    </div>

{% endhighlight %}

And the following Sass using the mixins above:

{% highlight scss linenos %} $icon-size: 62px; $icon-font-size: 24px;

.icons { margin-top: 40px; margin-bottom: 40px; }

.icon-list-caption { display: block; margin: 40px 0; text-align: center; }

.icon-list-wrapper { @include center-parent; }

.icon-list { @include center-child; }

.icon-item { border: 0.5px solid #ccc; padding: 10px; display: inline-block; border-radius: 50%; width: $icon-size; height: $icon-size;

@include center-parent; }

.icon { @include center-child;

display: inline; font-size: $icon-font-size; color: darken(cyan, 30%); }

.icon-text { display: none; } {% endhighlight %}


<a id="codepen-snippet-1"></a>

## Codepen Snippet

<div class="HTML">
<p data-height="265" data-theme-id="light" data-slug-hash="jAKGWW" data-default-tab="result" data-user="tamouse" data-embed-version="2" class="codepen">

</div>

See the Pen Social Icon Font Centering by Tamara Temple (@tamouse) on CodePen.

<div class="HTML">
</p>

</div>

<div class="HTML">
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>

</div>


<a id="using-plain-old-css"></a>

## Using Plain Old CSS

If you don't want to use Sass, you can accomplish the same thing in plain old CSS by creating new classes for the parent and child, and add them to the appropriate HTML elements:

{% highlight css linenos %} .center-parent { position: relative; } .center-child { position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); } {% endhighlight %}

{% highlight html linenos %}

<div class="HTML">
<h3 class="icon-list-caption">

</div>

Follow me on:

<div class="HTML">
</h3>

</div>

    <div class="icon-list center-child">
      <div class="icon-item center-parent">
        <div class="icon fa fa-facebook center-child"></div>
        <div class="icon-text">Facebook</div>
      </div>
      <div class="icon-item center-parent">
        <div class="icon fa fa-github center-child"></div>
        <div class="icon-text">Github</div>
      </div>
      <div class="icon-item center-parent">
        <div class="icon fa fa-twitter center-child"></div>
        <div class="icon-text">Twitter</div>
      </div>
    </div>

{% endhighlight %}

<div class="HTML">
<p data-height="265" data-theme-id="light" data-slug-hash="BzVmvJ" data-default-tab="result" data-user="tamouse" data-embed-version="2" class="codepen">

</div>

See the Pen Social Icon Font Centering by Tamara Temple (@tamouse) on CodePen.

<div class="HTML">
</p>

</div>

<div class="HTML">
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>

</div>

