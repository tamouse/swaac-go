---
title: "Til Mounting Stand Alone React Client as a React_component in React Rails"
date: 2020-01-11T09:28:03-06:00
draft: true
---

# TIL: mounting stand-alone react client as a react\_component in react-rails

* last updated: Time-stamp: &lt;2019-04-05 00:59:22 tamara&gt;
* capture date: \[2019-04-05 Fri 00:40\]
* keywords: react-rails, rails, react

This should have been obvious, but for some reason seemed like it was the “wrong” way to do this.

We have a product that we’re converting slowly to react-based components. One of the central philosophies has been to build towards a standalone react client, and move the rails app to be more strictly an API provider.

I started out using the standard `ReactDom` style of mounting the application to the page. This has worked well so far, until we ran into a strange issue.

The library `styled-components` has been something we’ve adopted for putting our CSS in JS. However it has a problem: if multiple copies are loaded on the page in different bundles, it gets confused and the styles seem to go missing.

My first reaction was to remove all the `styled-components` and go with inline style objects instead.

However, my colleague pointed out that we could **also** just build one bundle which would keep the issue at bay.

I ran an experiment to do this, and it worked. The essential parts are:

1. Create a new component, in my case I named it `ReactClient`, in the `app/javascript/components/` directory.
   * the component essentially just imports the `App` and renders it.
2. Change the layout where you’re loading the app to instead issue and ERB call to `react_component` that calls `ReactClient`, possibly adding props options and HTML options.
3. Remove the `webpacker` packs the build the client.

This worked really well, with the caveat that the application bundle is rather large since it now contains everything.

