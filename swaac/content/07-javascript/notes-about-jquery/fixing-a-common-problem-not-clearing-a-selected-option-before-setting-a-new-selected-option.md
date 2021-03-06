---
title: "Fixing a Common Problem Not Clearing a Selected Option Before Setting a New Selected Option"
date: 2020-01-11T09:28:03-06:00
draft: true
---

# Fixing a common problem: not clearing a selected option before setting a new selected option

* keywords: javascript, jquery
* capture date: Fri Apr 5 01:11:42 2019
* last updated: Time-stamp: &lt;2019-04-05 01:54:31 tamara&gt;

### Intro

This was a problem that our customers found \(OOPS! :\( \) that caused the wrong itme to be sent up to the server. What was most interesting about this is the way it presented itself was it was only failing in Safari on macOS. It worked as “expected” on both Chrome and Firefox.

### The problem

The problem was that when the user selected and option button, the app was using jQuery to change a hidden select tag by marking the option \`selected\`. The issue was the originally selected item was not cleared.

So in the case of Chrome and Firefox, in particular, they used the **first** selected option, while Safari used the **last**selected option. Neither are particularly right or wrong, and open to interpretation.

### The solution

The answer is that before setting an item “selected”, remove all the existing “selected” options. Theoretically there should be only one, however unless there’s some ungodly number of options that it might affect perceived performance, it’s easiest to just clear every option, first.

### Some code

THis is a tiny bit of jQuery that implemented the fix:

```text
function setTaskType(type) {
    // missing this caused the problem
    $('#task_task_type_id option')
	  .attr('selected', false);

    // this was the original
    $('#task_task_type_id option')
	  .filter(function() { return $.trim( $(this).text() ) == type; })
	  .attr('selected',true);
}
```

### Other thoughts

I’m calling this a “common error” because I’ve seen this exact problem crop up in other circumstances, perhaps a dozen times. If **I’ve** seen it that often, and I haven’t been writing a lot of JS for very long \(a handful of years\), it’s probably something that happens more often. It’s easy to forget it. It’s even easier to neglect to test this, especially if it looks like it’s working on one browser.

I think, in actuality, if this feature had been tested by pressing random buttons, in different orders, and selecting different options more than once, this error might have shown up a lot earlier, and on all browsers, too. That it showed up in the customers’ world is a let down. That it took one line to fix was pure luck.

* 
