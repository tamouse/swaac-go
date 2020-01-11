# Yet another swaac site, this time in hugo - ABANDONED (for now)

## Welp. So much for that ##

I discovered this isn't going to work how I want it to.

What I was after:
- a sidebar navigation scheme that made it easy to go through the articles, or find one that you wanted.

What I go:
- a sidebar navigation scheme that resets to the top of the page, and doesn't allow sub-category views expand / collapsed views.
- it's pretty cool to create pages and it was easy to generate the side bar (hah, who am I kidding, someone else did all the work for it).

## why ##

Why another version?

The history of this dev blog is rather checkered.

It started off life as a Jekyll site, which was cool and all, but I found it was taking too much of my time to create blog entries, so I started writing them in emacs' [org-mode](https://org-mode.org).

That was also difficult, translating, tooling, etc. -- not what I wanted. I converted *everything* to org-mode, and made a repo with just the org files.

That was not great either.

I read an article about gitbook, and how the person used it to publish their notes. I thought I'd give it a go. Sadly, for me, the gitbook editor itself was too clunky to use, getting in the way to creating new content, and organizing things by dragging articles around was too painful once I got above a certain number of them.

So a friend suggested I try hugo, which is writting in go, and is blazingly fast. So here we are, learning how to do a site in hugo.

Ultimately, the answer to "why?" is it is something else to learn.

## dependencies ##

Built using [hugo](https://gohugo.io/ "The fastest static site generator").

I adopted the [Learn](https://themes.gohugo.io/hugo-theme-learn/ "Documentation theme for Hugo, based on Grav Learn theme") for this version. It most closely resembles what I was doing on gitbook.

## development ##

### running the hugo server ###

I've made a `package.json` `start` script to launch the hugo server in "drafts" mode:

``` shell
yarn start # runs (cd swaac ; hugo server -D)
```

### project structure ###

The actual hugo static site is in the `swaac/` directory. This, I think, will let me keep other stuff not directly part of the static site in the same repo without having to deal with special filenames. So far, there really haven't been any, but hey.

### making a new page ###

Hugo has a subcommand `new` that creates new stuff, including pages:

``` shell
hugo new <chapter>/<section>/<page>.md
```

Which creates a new markdown file with the front matter already injected, and the page title derived from the page filename.

Since I'm copying stuff over from the gitbook version, I'm doing the following shuffle:

``` shell
# in swaacbook project
pbcopy < <section>/<subsection>/<page>.md

# in swaac-go project
pbpaste >> <chapter>/<section>/<page>.md
```

This moves the content, then I just need to go in and do a little editing. So far this has consisted of demoting the headings. (Yay for emacs' markdown mode!)

### weights ###

This took me a minute to figure out.

Hugo has a weighting system for pages, and the grav learn theme takes full advantage of this in building the navigation menu. This is a lot nicer than having to create alpha-numeric sorting in jekyll, or in gitbook using the SUMMARY.md file.

### chapters ###

The grav learn theme provides the concept of a chapter, which gives some structure to the collection of information. In my old way of organizing, this is akin to the jekyll category, and in swaac-org and swaac-book, it's done with subdirectories. This is arranged in subdirectories as well, here using the lexicographic ordering with numbers for the chapter prefixes. I don't think this is actually mandatory for hugo, but it's helpful for me to be able to visualize the order easier.

