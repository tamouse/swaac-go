
# Table of Contents

1.  [Example](#example)
2.  [References](#references)

-   Time-stamp: <span class="timestamp-wrapper"><span class="timestamp">&lt;2018-09-16 Sun 14:34&gt;</span></span>
-   original date: 2017-08-02 10:54
-   keywords: react, react-router, react-router-dom, memory-router, jest, enzyme, testing

Today, I was writing some React code that used the `<Link>` component from `react-router-dom`, and writing the Jest tests to go along with that.

`<Link>` requires a router and a history component to be available to it, and the recommended tool for testing this is to use `<MemoryRouter>`.

The `enzyme` testing package that works with Jest provides both deep and shallow renderers. Shallow rendering is good for doing snapshot testing on components where you don't want to or haven't yet finalized the underlying components.

The MemoryRouter, however, provides a history object that generates a collection of objects with randomly generated keys, so when you shallow render your component under test, wrapped in the MemoryRouter, you can't use the snapshot, because it changes every time.

I got around this particular problem by deep rendering, using `enzyme`'s `render` function. The component under test was very simple, just a few `<Link>` components, and no other components I was developing underneath it.

There will likely be cases coming up that cannot be addressed well with a deep render as a unit test, however, in which case I will have to rely more on writing many more expectations.


<a id="example"></a>

# Example

    import React from 'react'
    import {MemoryRouter} from 'react-router'
    import {Link} from 'react-router-dom'
    import {render, shallow} from 'enzyme'
    
    const MyComp = props => {
      const {href, linkText, icon} = props
      const iconClass = `fa fa-sm fa-${icon}`
      return (<div>
    	<h2>Some header</h2>
    	<Link to={href}>{linkText}<i className={iconClass}/></Link>
          </div>)
    }
    
    
    test("This will work with a deep render", () => {
      const actual = render(<MemoryRouter>
        <MyComp href="http://example.com" linkText="An Example" icon="external-link"/>
      </MemoryRouter>)
      expect(actual).toMatchSnapshot()
    })
    
    test("This will fail with a shallow render", () => {
      const actual = shallow(<MemoryRouter>
        <MyComp href="http://example.com" linkText="An Example" icon="external-link"/>
      </MemoryRouter>)
      expect(actual).toMatchSnapshot()
    })


<a id="references"></a>

# References

1.  `<Link>` <https://github.com/ReactTraining/react-router/blob/master/packages/react-router-dom/docs/api/Link.md>
2.  `<MemoryRouter>` <https://reacttraining.com/react-router/core/api/MemoryRouter>
3.  React Router Testing <https://reacttraining.com/react-router/core/guides/testing>

