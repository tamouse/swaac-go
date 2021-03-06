---
title: "Testing React Checkbox Component"
date: 2020-01-11T09:28:03-06:00
draft: true
---

# Testing React Checkbox Component

**published date:** \[2019-08-29 Thu\]

**keywords:** react, testing, checkbox, querySelector, rerender, queryByTestId, testing-library

Recently, I built a partial form section that included a couple of checkboxes, and I wanted to verify their operation with a unit test.

I’m using [testing-library](https://testing-library.com/docs/intro), including the react-specific methods. I’m finding this a _godsend_ in making tests easier to write and understand.

Testing and debugging react components is still fraught with uncertainty for me, I’m still learning and fumbling my way around. Hooks have made writing components much easier, without a doubt, yet there are still times I just don’t know what’s happening.

In this particular episode, your intrepid frontend dev \(me\) had to find out three things about the form segment:

1. a lookup \(autosuggest\) field was completely hidden until a particular checkbox was set.
2. another checkbox was disabled until another field had data in it.
3. a specific row of the form would appear only when another value was true.

For our purposes here, only 1 and 2 are of interest.

## Displaying a field form when a checkbox is set

For this form row, the code under test looks like this:

```javascript
const ServiceLocation = ({ name, value, initialValue, onSelectParent }) => {
  const [serviceArea, setServiceArea] = useState(!!value)
  const toggleCheckbox = () => {
    setServiceArea(!serviceArea)
  }
  return (
    <FormField name={name}>
      <FormFieldSubRow>
        <Checkbox
          value={serviceArea}
          onChange={toggleCheckbox}
          data-testid="service-area-checkbox"
        >
          {" "}
          {I18n.t("service_location.label", { scope: i18nScope })}
        </Checkbox>{" "}
        {serviceArea ? (
          <CustomerLookupWrapper data-testid="customer-lookup-wrapper">
            <CustomerLookup
              name={name}
              initialValue={initialValue}
              placeholder="Parent"
              onSelect={onSelectParent}
            />
          </CustomerLookupWrapper>
        ) : null}
      </FormFieldSubRow>
    </FormField>
  )
}
```

Placing the `data-testid` “service-area-checkbox” on the `Checkbox` component gives the test a way of finding the DOM element it needs to work with. The “customer-lookup-wrapper” \`data-testid\` will be used to determine if the second element shows up when the that checkbox is clicked.

The spec for this looks like:

```javascript
it("displays the parent lookup field when the service location checkbox becomes checked", async () => {
  const LOOKUP_WRAPPER_TESTID = "customer-lookup-wrapper"
  const props = {
    fields: {},
    parent: {},
    handleChange: jest.fn(),
    onDuplicateCustomerName: jest.fn(),
    onSelectParent: jest.fn()
  }

  const { queryByTestId, getByTestId, rerender } = render(
    <Providers>
      <CustomerInfoFormSection {...props} />
    </Providers>
  )

  const serviceAreaCheckbox = getByTestId("service-area-checkbox")
  const checkBoxActual = serviceAreaCheckbox.querySelector(
    "input[type=checkbox]"
  )

  /* PRECONDITIONS */
  expect(queryByTestId(LOOKUP_WRAPPER_TESTID)).not.toBeInTheDocument()
  expect(checkBoxActual.checked).toEqual(false)

  /* ACTION */
  fireEvent.click(checkBoxActual)

  /* VERIFY */
  expect(checkBoxActual.checked).toEqual(true)
  expect(queryByTestId(LOOKUP_WRAPPER_TESTID)).toBeInTheDocument()
})
```

The two lines where things get really interesting for me \(meaning: it took me a while to figure this out\) are:

```javascript
const serviceAreaCheckbox = getByTestId("service-area-checkbox")
const checkBoxActual = serviceAreaCheckbox.querySelector(
  "input[type=checkbox]"
)
```

We can get the `Checkbox` component with the first line, but this only gets us the label wrapper and not the actual checkbox, so the second line pulls up the actual checkbox from within it.

The rendered code from the `Checkbox` component looks like this:

```jsx
<label
  class="sc-kAzzGY dXoiwv"
  data-testid="service-area-checkbox"
>
  <input
    class="sc-cSHVUG bYZObx"
    type="checkbox"
  />

  service_location.label
</label>
```

The funky looking classes are the result of `style-components`. What’s interesting to note is that the `data-testid` was placed on the `label` node. Using `querySelector` let’s me pull out the actual checkbox, which is an HTML element of type “checkbox”.

From there, verifying the preconditions and postconditions becomes fairly easy:

* the state of the check box \(ie. checked or not checked\) is available as a property of the element
* using `queryByTestId` tests whether the particular element is in the document or not

Making the change happens with the `fireEvent.click`. \(Note: the `change` event doesn’t work for checkboxes. See: [https://github.com/testing-library/react-testing-library/pull/178/files\#diff-04c6e90faac2675aa89e2176d2eec7d8R631](https://github.com/testing-library/react-testing-library/pull/178/files#diff-04c6e90faac2675aa89e2176d2eec7d8R631) \) \(and beware the drift of time as well…\)

## Verifying a checkbox is en-/disabled based on another value

This case shows something a little different, and shows how to approach changing props as related to component testing.

The code under test in this case is:

```jsx
const SmsNotifications = ({ name, value, onChange, isMobileSet }) => {
  return (
    <FormField name={name} label={null}>
      <div>
        <strong>{I18n.t("notify_via_sms.title", { scope: i18nScope })}</strong>
        <Checkbox
          name={name}
          value={value || ""}
          onChange={onChange}
          disabled={isMobileSet ? null : "disabled"}
          wrap={"wrap"}
          data-testid="notify-via-sms-checkbox"
        >
          {" "}
          {I18n.t("notify_via_sms.label", { scope: i18nScope })}
        </Checkbox>
      </div>
    </FormField>
  )
}
```

The spec test for this feature is:

```jsx
it("enables the notify via sms checkbox when the mobile field has a value", () => {
  const NOTIFY_CHECKBOX_TESTID = "notify-via-sms-checkbox"

  const props = {
    fields: {},
    handleChange: jest.fn(),
    onDuplicateCustomerName: jest.fn(),
    onSelectParent: jest.fn()
  }
  const { queryByTestId, getByTestId, rerender } = render(
    <Providers>
      <CustomerInfoFormSection {...props} />
    </Providers>
  )
  const notifyCheckBoxComponent = getByTestId(NOTIFY_CHECKBOX_TESTID)
  const checkBoxActual = notifyCheckBoxComponent.querySelector(
    "input[type=checkbox]"
  )
  expect(checkBoxActual.disabled).toEqual(true)

  rerender(
    <Providers>
      <CustomerInfoFormSection {...props} fields={{ mobile: "555121" }} />
    </Providers>
  )

  expect(checkBoxActual.disabled).toEqual(false)
})
```

I’m doing the same trick as before about grabbing the actual checkbox by using `querySelect` on the element returned with `getByTestId("NOTIFY_CHECKBOX_TESTID")`. This provides access to the `disabled` property.

This test uses the testing library’s `rerender` method, which is used to apply different props. In this case the props for the component are controlled above this component, so this is actually a valid test matching how it would work in the user’s environment.

For the re-render, I’m passing in a value for the mobile phone number, which is used to determine whether the checkbox is en-/disabled.

