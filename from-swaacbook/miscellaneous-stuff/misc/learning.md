
# Table of Contents

1.  [Resources for learning how to program, especially how to program in Ruby and Rails](#orgeafa63b)
    1.  [Introduction](#orgce2e2e4)
    2.  [Books](#orgb3c1091)
        1.  [Object-Oriented Programming](#org80cf749)
        2.  [Ruby-specific](#orgcdd3dd8)
        3.  [Rails-specific](#org1258dd3)
        4.  [JavaScript-specific](#orgc6abf4f)
        5.  [HTML and CSS Specific](#orgbee07d4)
    3.  [Web sites](#orgb5b1214)
    4.  [Podcasts](#orgd55c8b3)
    5.  [Teaching Organizations](#orgc3094e2)
    6.  [Bootcamps](#org415a66e)
    7.  [Conferences and Meetups](#org1baa67a)
    8.  [More Advanced](#orga9d127a)


<a id="orgeafa63b"></a>

# Resources for learning how to program, especially how to program in Ruby and Rails

-   last updated Time-stamp: <span class="timestamp-wrapper"><span class="timestamp">&lt;2018-12-30 Sun 12:42&gt;</span></span>


<a id="orgce2e2e4"></a>

## Introduction

Many people ask me "How do I learn to program?" and "What book(!) should I read to learn Rails?".

These are legitimate questions, but they aren't necessarily the right questions to ask in order to begin the journey of becoming a software craftsperson.

Better questions, I feel, are:

-   What resources do you recommend for beginners?
-   Where can I go for help?

I've been finding things around the 'net that can greatly help people new to programming, new to web development, new to Rails, and so on.

---

**UPDATE:** I've created a section for the [Absolute Beginner](./beginners-section.md) as well, you might find it useful.

This is a quick, short list of things. I urge you to seek them out, and seek out others as well, and create your *own* list of learning resources. People will begin to ask you, and it's nice to have something handy.

Also, [learning Rails is hard](https://www.codefellows.org/blog/this-is-why-learning-rails-is-hard). But don't despair! The key to learning is break things down, focusing and practicing small things, and build up a lot of skills slowly. ("Wax on, wax off." "Ok, Mr. Myagi.") I'm going to jump ahead and tell you to download the first chapter (free) of Justin Weiss's book [Practicing Rails](https://www.justinweiss.com/practicing-rails/). Search for "first chapter" and fill out the form to get it. You're also signing up to get e-mail from Justin, but it's always good stuff.

---

*Update Sun Jun 8 11:39:13 2014:* Recently came across web post [Best Way To Learn Ruby and Rails](http://astonj.com/tech/best-way-to-learn-ruby-rails/) and must say it is a great compilation of resources. In addition, Ashton puts the focus right at the heart of the matter: you have learn *both* Ruby *and* Rails.

---


<a id="orgb3c1091"></a>

## Books

-   [**Think Like a Programmer: An Introduction to Creative Problem Solving**](https://www.goodreads.com/book/show/13590009-think-like-a-programmer) by V. Anton Spraul.
    
    Spraul's purpose in this book is not to teach you how to write a program, but to begin to understand the problem-solving approach that is inherent in good programmers. Like so many skills, programming is driven by the desire and vision of the practitioner. A painter uses brushes, canvas, paints, other media to create a work of art, but it isn't the tools, it isn't the specific techniques, and it isn't even the particular skill the painter has that makes a good work of art; it is their composition, the melding of media and surface, the use of different techniques, and practice in developing the skills that come together to form the work of art. Spraul is going to take you deeper than just the syntax, semantics, and data structures of software to the heart of what makes a good programmer: the ability to creatively find and generate solutions to problems.

-   [**Learn to Program**](https://www.goodreads.com/book/show/520.Learn_to_Program) by Chris Pine.
    
    To be honest, I have not looked through this book. It is, however, nearly universally recommended to people new to programming. The original tutorial is available online for free as well: <https://pine.fm/LearnToProgram/>. LtP was featured on the great webcomic [Unshelved](http://www.unshelved.com/2014-7-25).

-   [\*\*The Pragmatic Programmer](https://pragprog.com/book/tpp/the-pragmatic-programmer) by Andrew Hunt and David Thomas
    
    This is the best modern treatise on the craft of programming. It represents the best of experiences programmers have come to appreciate during years of development. I read this book after years of practice, and found everything in it to ring true. (The thought "I could have written this!" came up frequently.) This book is not about any specific language or technology, but spans the gamut of software development. This is a must-have for practitioners.

-   [**A Pattern Language: Towns, Buildings, Construction**](https://www.goodreads.com/book/show/79766.A_Pattern_Language) by Christopher Alexander.
    
    You may be wondering why I've included a book on building construction. The answer is quite simple: the concepts in building towns and houses is nearly directly translatable to building software applications and systems. One part of being an excellent craftsperson is being able to apply abstract learning in different problem domains. If you are an expert in writing software, you are almost *never* going to be solving problems only for other software developers. (You can and should do so, but the client and users are generally non-programmers.) Thus you're most likely going to be working in someone else's domain of expertise. Alexander's views on architecture apply to software architecture as well.

-   [**Beautiful Code**](http://shop.oreilly.com/product/9780596510046.do) by Andy Oram and Greg Wilson.
    
    A book with a purpose, that isn't a how to, so much as a how to think. It's a collection of essays by various software developers on what they think makes code beautiful. In all, the following holds true:
    
    1.  First, make it correct.
    2.  Second, make it pretty.
    3.  Third, make it fast.

-   **Programming Proverbs** by Henry F. Ledgard
    
    This book, published in 1975, and a subsequent volume dedicated to the Pascal language published in 1979, were essential to me back when I was in university learning computer science. They're out of print now, so I'm starting a blog series covering them. [Programming Proverbs: Introduction](%7B%7Bsite.baseurl%7D%7D%7B%%20link%20_posts/2017-07-23-pp-introduction.markdown%20%%7D)

-   [**Systems Design Heuristics**](https://leanpub.com/systemdesignheuristics) - by the late, great Jerry Wienberg.
    
    Jerry was a friend as well as a teacher. I miss him enourmously. This book is full of his thoughts and writings on how one should do systems design. As the title implies, there are no rules, but there are some heuristics one can apply to the overall design and architecture of systems.


<a id="org80cf749"></a>

### Object-Oriented Programming

-   [**99 Bottles of OOP**](https://www.sandimetz.com/99bottles) by Sandi Metz and Katrina Owen.
    
    A recent book, representing the absolute best by two teachers of software engineering. Sandi has been teaching Object-oriented programming for decades, and Katrina brings in her expertise with refactoring, resulting in a deep book that stretches beyond the basics and deep into the structures and understanding of object systems and idioms. It brings up to date the actual concepts of refactoring, test-driven development, naming things, reducing code "smells" and making code more easily and economically maintainable and sustainable. They take all the buzzwords and unbuzzify them into practical, useful methodologies and techniques.


<a id="orgcdd3dd8"></a>

### Ruby-specific

-   [**Eloquent Ruby**](https://www.goodreads.com/book/show/9364729-eloquent-ruby) by Russ Olsen.
    
    Olsen's approach in this book is to go far beyond just learning a programming language, but a way to learning the idioms and the "Ruby Way". Even if your chosen language is something other than Ruby, reading this book will give you an appreciation for how to delve into a language and get the most out of it.

-   [**Confident Ruby**](http://www.confidentruby.com/) by Avdi Grimm.
    
    More than any other book I've read on Ruby, "Confident Ruby" has affected my coding habits more than any other. If Ruby is about making programmers happy, *Confident Ruby* is about making programming joyful, and not just in the immediate, but being able to look at code you've written in the future and recall the joy. *Confident Ruby* seeks to combat software rot from the get-go.

-   [**Well-Grounded Rubyist**](http://www.amazon.com/The-Well-Grounded-Rubyist-David-Black/dp/1617291692) by David A. Black
    
    Also known as the "Black Book" (because of the author's name), WGR is the successor to *Ruby for Rails* by Black that provided me with the much-needed introduction to how to write Ruby code, with the idea of using it in Ruby for Rails. This book is a fabulous primer on the Ruby idioms and expressions that help make one a good Ruby programmer.

-   [**Practical Object-Oriented Design in Ruby**](http://www.poodr.com/) by Sandi Metz
    
    This book provides a deeply-needed introduction to object-oriented design, specifically targeted to the Ruby language. Ruby is one of the richest languages in which to express object-oriented patterns, but it is easy to fall of the OO wagon and start to get things messed up. Sandi provides the thinking tools necessary to decide how to structure your code for better maintainability, extensibility and testability. Comprehension and forward communication of the choices made during software design are crucial to programming, and Sandi is one of the very best at explaining things.


<a id="org1258dd3"></a>

### Rails-specific

-   [**Rails 4 in Action**](http://www.manning.com/bigg2/) by Ryan Bigg, Yehuda Katz, Steve Klabnik, and Rebecca Skinner.
    
    A follow-on the highly successful Rails 3 in Action, R4iA has been completely rewritten, with new examples, case study, and all the great new features in Rails 4.
    
    A great book for beginning Rails developers to start with, and for intermediate developers to step up their game.

-   [**Practicing Rails**](https://www.justinweiss.com/practicing-rails/) by [Justin Weiss](http://www.justinweiss.com).
    
    The first chapter alone (free!) is worth a download and very thorough read. Justin has provided one of the most effective strategies for learning just about *anything* skill based, and it's especially effective for learning software skills. The focus of the book and the examples and such are obviously Rails, but the first chapter is applicable to anything.


<a id="orgc6abf4f"></a>

### JavaScript-specific

-   [**JavaScript: The Good Parts**](https://www.goodreads.com/book/show/2998152-javascript) by David Crockford.
    
    JavaScript is a vast, sprawling language and ecosystem, and has been maligned for much poor code on the web. Crockford extracts out the parts that are really useful, giving the reader a better grounding. This book is the progenitor of many of the JavaScript frameworks that have come up the past few years, as well as CoffeeScript and other \*Script derivatives.

-   [**You Don't Know JS series**](https://github.com/getify/You-Dont-Know-JS) by [Kyle Simpson](https://github.com/getify).
    
    A *tour de force* by one of the great teachers and evangelists of JavaScript, Kyle's "You Don't Know JS" series is a must-read collection of books. You can get the books in raw form on-line at the above address, and you can get the published e-books at your favourite vendor.

-   [**Eloquent Javascript**](http://eloquentjavascript.net/) by Marijn Haverbeke.
    
    When I was more naive about JS, I wrote a bit of a negative review of this book. Subsequently, I've learned of it's true eloquence and meaning in giving a model of how to organize and implement modern JS. The subtitle "A modern introduction to programming" is still a bit misleading, perhaps, because you have to understand a fair bit of JavaScript *and* programming to get the message, I feel. But that's just a quibble at this point. Read this before you strike out on creating a client-based JS application; you won't regret it.

-   **Test-Driven JavaScript Development** by Christian Johansen (Addison-Wesley Professional, September 2010, ISBN 9780321683915)
    
    (The [ebook](http://www.informit.com/store/test-driven-javascript-development-9780321684042) for this title is ridiculously expensive. I read it via [safarionline](https://learning.oreilly.com/library/view/test-driven-javascript-development/9780321684097/).)
    
    This book provides some great insights into testing JavaScript applications. Released in 2010, the things that are out of date are the specific tools used for testing, *however*, the concepts for writing tests and performing test-driven Javascript development are still very appropriate.

-   [**JavaScript Allongé**](https://leanpub.com/javascriptallongesix) by Reginald "raganwald" Braithwait
    
    Using the metaphor of a coffee barista, Reg goes in depth on thinking about how JavaScript works; this is not a practical book from the standpoint of "tell me what code to write", but rather from the standpoint of knowing how JavaScript works inside so you can write better code yourself.


<a id="orgbee07d4"></a>

### HTML and CSS Specific

-   [**HTML and CSS Design and Build Websites**](https://www.amazon.com/HTML-CSS-Design-Build-Websites/dp/1118008189?ie=UTF8&*Version*=1&*entries*=0) by Jon Duckett.
    
    This book has been recommended by several people in the [GDI] courses I've been helping in. A very visual approach, using full-colour photographs to explain the two declarative languages.


<a id="orgb5b1214"></a>

## Web sites

This is just going to be a list of sites I've found or been pointed at for helping people learn to program. These are most definitely biased towards Ruby and Rails, as that is my current area of concentration, and generate the most requests that come to me.

-   [**The Odin Project**](http://www.theodinproject.com/home) &#x2013; pulling together a curriculum from around the web, this is a curation site that gives order and structure to learning how to develop web applications.

-   [**Code Kata**](http://codekata.com/) &#x2013; Dave Thomas's site that lists a great set of coding exercises. You can work these more than once, in fact that is what you do with kata.

-   [**Exercism.IO**](http://exercism.io/) &#x2013; a site devoted to helping people learn and think deeply about writing excellent code. It has projects you implement and then get feedback on from others, and allows you to give feedback as well.

-   [**RailsBridge**](http://docs.railsbridge.org/docs/) &#x2013; a site devoted to helping people get up and running on learning Ruby on Rails, with emphasis on reaching out to women and LGBTQ folks. RailsBridge workshops are run around the world and the documents here can be used individually to help turn your computer into a development machine. What so often isn't addressed directly by very many of these sites and books is the ecosystem that one has to learn as well: a coding editor, the command line, rake, irb/pry, git, heroku if that is your choice for deployment (which I do recommend for small beginner projects so you can show it off to your friends); RailsBridge tutorials include these very important tools.

-   [**RailsGirls Guides**](http://guides.railsgirls.com/) &#x2013; I haven't explored these in depth yet, I just got the site yesterday. However, I can see just from the list of guides these would be pretty great, just like the RailsBridge site above.

-   [**Hartl's Rails Tutorial**](http://www.railstutorial.org/) &#x2013; the most often recommended site to learn how to create web applications in Rails, it goes beyond the Rails stack itself, teaching Ruby, HTML5, CSS3, JavaScript, user authentication and authorization, data modeling, and so on. While Michael sells the book, tutorials, and screen casts, the text of the tutorial online is free at <http://www.railstutorial.org/book>. Considerable work has gone into this effort, however, so if you can afford to, please purchase at least the book.

-   [**CodeSchool**](https://www.codeschool.com/) &#x2013; learn from the "Comfort of your own browser". Codeschool has web casts, coding practices, challenges, and so on.

-   [**CodeAcademy**](http://codeacademy.com) &#x2013; although I do not personally like the way one interacts with the web site, it does offer an gentle introduction to ruby, javascript, python and other subjects in an immediate feedback environment.

-   [**Kahn Academy**](https://www.khanacademy.org/computing/cs) &#x2013; learning to program with JavaScript (if you are just starting out, JS is a fine language to learn. It's fairly ubiquitous in the online world.). Their approach is teaching young folks, which might or might not appeal.

-   [**RailsCasts**](http://railscasts.com/) &#x2013; another super awesome effort has been put together by Ryan Bates. Current production is on hiatus, so the $9/month fee for the full screen casts is being pro-rated, so you can buy in for $9 and there won't be further monthly charges until production starts up again.

-   [**RubyTapas**](https://www.rubytapas.com/frequently-asked-questions/) &#x2013; Avdi Grimm is a fabulous Ruby and Rails mentor and guide, who puts out two very short screen casts a week (tapas &#x2013; small plates). These are really impeccably done, and I personally love listening to Avdi talk.

-   [**LearnCodeTheHardWay**](http://learncodethehardway.org/) &#x2013; provides online versions of books and tutorials for [**Python**](http://learnpythonthehardway.org/book/), [**Ruby**](http://ruby.learncodethehardway.org/book/), [**C**](http://c.learncodethehardway.org/book/), [**SQL**](http://sql.learncodethehardway.org/book/), [**Regular Expressions**](http://regex.learncodethehardway.org/book/) and more.

-   [**Ruby Koans**](http://www.rubykoans.com/) &#x2013; "koans" are an Eastern discipline tradition: small, repeated exercises to learn skills and build them into your muscles and memory, so you can use them without thinking consciously about them. In this sense, the ruby koans are small exercises intended to lead you on the way to learning ruby. I can't say if they're that successful, but some people definitely enjoy this progressive way of learning. The ruby koans definitely guide you in the way of test-first development, which is a beneficial practice for all to know.

-   [**Upcase, by Thoughtbot**](https://thoughtbot.com/upcase) &#x2013; not a bootcamp, a finishing school. Where to go to level-up.


<a id="orgd55c8b3"></a>

## Podcasts

I am not such a big fan of podcasts, but that has more to do with my personal learning style. Nevertheless, there are some great pocasts out there.

-   [**Greater Than Code**](http://www.greaterthancode.com/) Also known as `>Code`, this is a podcast that's more about people that practice software development and allied things, about management of such people, and making all our lives better.

-   [\*\*Frontend Happy Hour](http://frontendhappyhour.com/) A handful of front end developers, including Brian Holt, Jem Young, Ryan Burgess, Augustus Yuan, and Stacy London, joined by various guests. It's a fun podcast, each week with a special word or phrase that when uttered, everyone takes a drink.

-   [**CodeNewbies**](http://www.codenewbie.org/) &#x2013; started off as a twitter chat, and grew into a thing, CodeNewbies offers podcasts on topics that range far and wide. Recent topics have included Scrum/Agile methods, maintaining your mental health while programming, interviews with folks who have created significant web sites (Gina Trapani of LifeHacker!!), mobile, databases, single-page apps, you name it. One of the best aspects I can see directly is that this is a *very* open, diverse collaboration.


<a id="orgc3094e2"></a>

## Teaching Organizations

These are the ones I'm familiar with at this point in time (late 2015) in the Twin Cities area:

-   [**Frontend Masters**](https://frontendmasters.com/) &#x2013; Based out of Savage, MN, they offer both live in-person and online courses, and they have recorded all the training sessions for on-demand viewing if you're a member. The quality of these sessions and the videos are extremely good (these are not your twitch.tv live sessions of someone rambling about their code as they hack away) All the courses I've taken and viewed are fantastic.
    
    FrontendMasters tackles intermediate and advanced topics in developing on the front end of web applications. Heavy into JavaScript, libraries, frameworks, techniques, and so on.


<a id="org415a66e"></a>

## Bootcamps

These are becoming quite popular, if expensive, but they seem to provide what's being offered: intensive training in the skills necessary to become a web application developer, with experience and skills in the entire lifecycle of modern software development. I can't really provide much information on them, as I've never experienced them. [Bootcamps.in](http://www.bootcamps.in/) provides at least a first-glance at several bootcamps.


<a id="org1baa67a"></a>

## Conferences and Meetups

Going to conferences, hanging out, meeting like-minded people, and generally instilling one's self into the millieau of the Ruby and Rails communities can be extremely rewarding. Even if you're not the conference type, make an effort to find people in your area to talk to.

There's lots of other meetups in the Twin Cities I'm regularly trying to attend:

-   [Women Who Code Twin Cities](https://www.meetup.com/Women-Who-Code-Twin-Cities/)
-   [Ruby.MN](https://www.meetup.com/ruby-mn/)
-   [JavaScript.MN](https://www.meetup.com/JavaScriptMN/)
-   [React Minneapolis Meeetup](https://www.meetup.com/React-Minneapolis-Meetup/)
-   [Elixir MN](https://www.meetup.com/Elixir-MN/)
-   [MSP WP](https://www.meetup.com/Minneapolis-St-Paul-WordPress-User-Group/)


<a id="orga9d127a"></a>

## More Advanced

If you want to go deep and learn more about computer science, the book [*Structure and Interpretation of Computer Programs*](https://mitpress.mit.edu/sicp/) is probably your best bet in terms of a real CS text book that's available online for free. It's not a tutorial, but there are exercises in the text. The book uses Scheme, a lisp-like programming language. Everyone should learn a little lisp at some point. :) However it's not mandatory one use Scheme (or Clojure as the local Clojure user group has been doing). The analytical concepts apply across all languages. If you're focused on JavaScript or Ruby, you can work the examples in those languages, too.

The afore-mentioned Frontend Masters has been producing some much more advanced courses lately:

-   [Four Semesters of Computer Science in 5 Hours](https://frontendmasters.com/courses/computer-science/) with [Brian Holt](https://frontendmasters.com/teachers/brian-holt/)

-   [Four Semesters of Computer Science in 5 Hours, Part 2](https://frontendmasters.com/courses/computer-science-2/) with Brian Holt

-   [A Practical Guide to Algorithms with JavaScript](https://frontendmasters.com/courses/practical-algorithms/) with [Bianca Gandolfo](https://frontendmasters.com/teachers/bianca-gandolfo/)

-   [Introduction to Data Structures for Interviews](https://frontendmasters.com/courses/data-structures-interviews/) with Bianca Gandolfo

-   With Will Sentance:
    -   [JavaScript: The Hard Parts](https://frontendmasters.com/courses/javascript-hard-parts/)
    
    -   [JavaScript: The New Hard Parts](https://frontendmasters.com/courses/javascript-new-hard-parts/)
    
    -   [JavaScript: The Hard Parts of Object Oriented JavaScript](https://frontendmasters.com/courses/object-oriented-js/)

I'm just going to list [Kyle Simpson's entire collection](https://frontendmasters.com/teachers/kyle-simpson/) because they are **all** great

Other fav instructors:

-   [Scott Moss](https://frontendmasters.com/teachers/scott-moss/)
-   [Shirley Wu](https://frontendmasters.com/teachers/shirley-wu/)
-   [Kent C. Dodds](https://frontendmasters.com/teachers/kentcdodds/)
-   [Jem Young](https://frontendmasters.com/teachers/jem-young/)
-   [Lukas Reubbelke](https://frontendmasters.com/teachers/lukas-ruebbelke/)
-   [Sarah Drasner](https://frontendmasters.com/teachers/sarah-drasner/)

