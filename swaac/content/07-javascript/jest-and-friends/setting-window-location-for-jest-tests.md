---
title: "TIL: Setting Window Location in Jest Tests"
date: 2018-11-13T09:28:03-06:00
---
- Time-stamp: <2020-01-11 09:57:45 tamara>
- capturedate: 2018-11-23 Fri
- keywords: jest, window.location, testing

## TIL: Setting \`window.location\` during Jest testing ##

By default, the `window.location` properties are read-only. But for some tests, I need these to be specific, set values.

In [Jest issue 890](https://github.com/facebook/jest/issues/890) over on github, there is a long discussion about this, and ways people have solved this issue for themselves.

### first solution ###

The first one I happened upon is one used by Facebook engineers:

I needed to modify `pathname` property only for my test:

```javascript
Object.defineProperties(
    window.location,
    'pathname',
    {
        writeable: true,
        value: defaultPathname
    }
)
```

### second solution ###

Here's a more universal one:

```javascript
const setURL = (url) => {
    const parser = document.createElement('a');
    parser.href = url;
    [
        'href',
        'protocol',
        'host',
        'hostname',
        'origin',
        'port',
        'pathname',
        'search',
        'hash'
    ].forEach(
        prop => {
            Object.defineProperty(
                window.location,
                prop,
                {
                    value: parser[prop],
                    writable: true,
                }
            );
        }
    );
};
```

The sneaky trick of creating a wee little parser out of a document anchor element is pretty dang cool, too.

### third solution ###

Later in the issue page, there's some discussion about how this might break in future versions of `jsdom`, and another way to set the location property, by modifying the history on `window`:

In your Jest configuration, include the following setting:

```javascript
{
    // other config items...
    "testUrl": "https://somehost.com/some/path/test.html"
}
```

And in your test setup:

```javascript
window.history.pushState(
    {},
    'Test Title',
    '/another/path/test.html?query=true'
);
```

### sources ###

This is from the [Jest and URL testing](https://www.ryandoll.com/post/2018/3/29/jest-and-url-mocking) blog post by Ryan Doll.
