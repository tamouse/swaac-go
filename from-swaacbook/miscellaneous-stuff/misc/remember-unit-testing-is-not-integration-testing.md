
# Table of Contents

1.  [Remember &#x2013; Unit Testing is NOT Integration Testing](#orgcc0374c)


<a id="orgcc0374c"></a>

# Remember &#x2013; Unit Testing is NOT Integration Testing

-   last update: Time-stamp: <span class="timestamp-wrapper"><span class="timestamp">&lt;2018-11-04 Sun 08:18&gt;</span></span>
-   published date: <span class="timestamp-wrapper"><span class="timestamp">[2018-09-16 Sun 13:34]</span></span>
-   keywords: testing, react, unit testing, components

I seem to forget this from time to time when creating a component, that the unit test does not and should not test things outside the component, or things that interact with the component.

It also helps if you remember this while you're creating the component, and why it often helps to write the tests first, even if you just give the test a title, at least spend a minute thinking about how you'll execute the test in the unit environment.

This can be a problem with testing React components that build upon other components, or that need to interact with providers such as Apollo client, Redux, and so on.

At least Apollo provides a mock client provider.

Even then, if you're using the recent `Query` and `Mutation` components from `react-apollo`, it helps to write your inner child function in a way that your unit tests can interact with it without requiring the mock provider.
