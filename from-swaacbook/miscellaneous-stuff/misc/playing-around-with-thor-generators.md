
# Table of Contents

1.  [Playing Around with Thor Generators](#org724c87a)
    1.  [so what is a generator?](#org6b0b4f3)
    2.  [generating &#x2013; what?](#org1a9cd0c)
    3.  [A typical project directory](#org6df2ca7)
    4.  [gems](#org6f1b512)
        1.  [continuous testing with `guard`](#orgfca488c)
        2.  [so what about thor, again?](#orga1cf74c)
        3.  [what else?](#org7a9d6b2)
        4.  [I am sure I've reimplemented the wheel&#x2026;](#org6a5c404)
        5.  [Feedback](#org750fa53)


<a id="org724c87a"></a>

# Playing Around with Thor Generators

-   published date: 2014-03-08 15:06
-   keywords: ["automation", "fun-with-programming", "ruby", "swaac", "thor", "tools"]
-   source:

Automating things has been somewhat of a life goal for me. Ultimately, I'm a pretty lazy person, and I hate to have to do things repetitively, and if I can get the computer to do it for me, I'll write a script. (Although I admit this sometimes devolves into Yak shaving.)


<a id="org6b0b4f3"></a>

## so what is a generator?

Simply put, a generator is something that builds something else for further use. Sometimes this is referred to as a factory if you're doing it in code. But here, I'm taking the meaning of creating files and directories, with possibly customized content, that will be used to frame in a bit of a coding project.

[Thor](http://whatisthor.com) is a nifty tool that was extracted from Rails to be a stand-alone tool. Generators are tools that build other things, typically used in Rails for models, controllers, and so on, but generators can live anywhere. Thor is also a very viable alternative to [methadone](http://davetron5000.github.com/methadone/) or [GLI](http://davetron5000.github.io/gli/), which are both very awesome and worthy starting points (and generators in their own right!). In fact, I owe *a lot* to  [Dave Copeland (@davetron on Github)](https://github.com/davetron5000) for his super awesome ideas and directions on making cli applications in Ruby.


<a id="org1a9cd0c"></a>

## generating &#x2013; what?

I have often started off a learning exercise by creating a gem skeleton with `bundler` :

{% gist 9439598 bundler-gem %}

This is itself a generator, and rather a cool way to start something up. However, it's intended to create an actual gem, which I don't necessarily want to do, especially if it's something I'm trying to learn, or demonstrate, or somehow work out, but not something I'm going to publish in [rubygems][rubygems].

So what would I generate, exactly, and how?


<a id="org6df2ca7"></a>

## A typical project directory

Below is a typical project directory structure I like for starting out:

{% gist 9439598 directory-structure %}

Several of these might remain empty or unused, but it's a great starting point for me. If I do wish to turn it into a gem, All I need do is add a `.gemspec` file.


<a id="org6f1b512"></a>

## gems

I also have my favourite set of gems that I like to start out with:

-   `rspec` - my testing framework of choice
-   `guard` - for continuous testing
-   `guard-rspec` - to watch rspec tests
-   `guard-bundler` - to watch changes to Gemfile
-   `pry` - my REPL of choice
-   `pry-nav` - nice navigation inside pry
-   `pry-git` - link to git for blaming code
-   `pry-doc` - link to internal documentation
-   `pry-remote` - to attach to a remote ruby process
-   `pry-rescue` - to jump into the pry REPL if an exception happens
-   `pry-byebug` - debugger for ruby MRI 2.x
-   `pry-stack_explorer` - to jump up down or sideways in the execution stack
-   `awesome_print` - really nice looking output, integrated into pry
-   `rb-readline` - a necessary evil running on the Mac
-   `coolline` - nice colouriser
-   `coderay` - syntax highlighting on the fly in pry

These are in the Gemfile in a default group. If I were to release the project as something, I'd move these into the `:development` and `:test` groups.


<a id="orgfca488c"></a>

### continuous testing with `guard`

[Guard](https://github.com/guard/guard) is a fabulous system that builds on *top* of [pry](http://pryrepl.org) that watches various directories and reruns tests (or other commands if you set it up to). I have the Guardfile in the generator, though, because out-of-the-box `guard-rspec` does not run `rspec` bundled, and I'm nearly *always* running under `bundler`.

The modification is simple:

{% gist 9439598 Guardfile %}

You add the `:cmd` to the `rspec` `watch` section. But it's just one more thing to have to remember and slow me down.

A difference between `bundle gem` and `guard-rspec` is that the former expects spec tests to live directly under the `spec/` directory, while the latter figures the `lib/` structure is mirrored under `spec/`. This isn't such a big deal, but it is one more thing to think about, and I'm often puzzled why things don't work. (Convention over configuration, perhaps not enough time spent together.)


<a id="orga1cf74c"></a>

### so what about thor, again?

Thor seems all about generating things. Included in [`Thor::Actions`](http://rdoc.info/github/wycats/thor/master/Thor/Actions) are some really useful items for copying, converting, templating, and so on. There are also commands for interacting with the user, should that prove necessary.

Here's the new project generator:

{% gist 9439598 new<sub>ruby</sub><sub>project.thor</sub> %}

Let's talk a bit about this script.

1.  Thor::Group

    The first thing we make is the class declaration for our thor command. The class inherits from `Thor::Group` instead of from `Thor` proper. This causes the defined methods to be executed in order, rather than creating individual sub-commands, as is the case when you inherit from `Thor`. This essentially turns the command into a script, which is how we usually want things done in a generator.

2.  Thor::Actions

    We include `Thor::Actions` in our class to give us the useful tools for interacting with the user (`say`, `ask`, etc ), as well as the building tools, `create_file`, `copy_file`, `template`, and so on.
    
    In this generator, I'm using `template` nearly everywhere, as it copies a source file with `ERB` directives in it and writes out the result to the destination.

3.  argument :name

    This is telling thor to expect one argument upon invocation, in this case, the name of the new ruby project.

4.  def self.source<sub>root</sub>

    Thor::Action arguments typically follow the convention of source, destination, and options, with passing a block if there are further things that need to be done.
    
    The source is determined by the class method `source_root`. The default method ends up using the current working directory as the source root. Redefining the class method permits the author to specify a completely different directory to use as the source root folder.
    
    In this case, I've specified the skeleton directory for new projects, which looks like that above.

5.  def name<sub>components</sub>

    This is doing a bit of munging on potential input from the user. It's quite possible to put pretty much anything as the first argument, but what we really only want are the alpha-numeric bits, which we will consider as project name components.
    
    Supplying things like `Able & Louis: Go @@CRAXY@@` would end up as name components `["Able", "Louis", "Go", "CRAXY"]`. The components are used by later methods to construct useful names for things.

6.  def snake<sub>name</sub>

    Here's one now: out of something like `["Able", "Louis", "Go", "CRAXY"]`, would come `able_louis_go_craxy`, which is a very nice name for files and directories, where this is usually used.

7.  def camel<sub>name</sub>

    The other method using `name_components`, this will produce `AbleLouisGoCraxy` which gives us our useful module name.

8.  def copy<sub>files</sub>

    This picks up the files that we want to transfer to the root directory of the new project, translates them, and writes them to the destination's root.

9.  def dot<sub>files</sub>

    These are the "hidden" files in a directory, that begin with a "." but are so useful. These are picked up from the source, translated, and saved to the destination with a "." pre-pended.

10. def other<sub>file</sub>

    The rest of the project is translated and saved into the appropriate places.


<a id="org7a9d6b2"></a>

### what else?

This is still pretty blunt and could use some work to make it even more useful. It works for me now quite well. Here are some additional ideas:

1.  use a manifest

    Instead of hard-coding the source file names in the methods, create a manifest that lists what files should be moved from which locations to which destinations. I think a YAML file would do this quite nicely.

2.  allow a different skeleton

    Instead of nailing the skeleton inside the thor script, pass it in as a parameter.


<a id="org6a5c404"></a>

### I am sure I've reimplemented the wheel&#x2026;

&#x2026;but I am learning from doing this. There have been many ways to make gems, command line applications, web applications, and so on. I can see using this to build jekyll pages, or an entry for a new art project I'm working on to collect images, notes, etc.


<a id="org750fa53"></a>

### Feedback

While I don't use any sort of comment system here on the blog, feel free to leave comments at my [Facebook Page](https://www.facebook.com/pontikiweb) or hit me up on [Twitter](http://twitter.com/tamouse). I'd love to hear from you.

