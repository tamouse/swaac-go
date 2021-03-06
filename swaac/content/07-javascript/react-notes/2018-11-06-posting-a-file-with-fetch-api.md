---
title: "2018 11 06 Posting a File With Fetch Api"
date: 2020-01-11T09:28:03-06:00
draft: true
---

# Posting a file using the fetch API

- Time-stamp: <2019-10-09 01:08:48 tamara>
- published date: 2018-11-06 Tue 13:17
- keywords: javascript, fetch, file upload

I'm investigating this for work

See [MDN: Uploading a file (fetch)](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch#Uploading_a_file)

> Files can be uploaded using an HTML <input type="file" /> input element, FormData() and fetch().

```javascript
let formData = new FormData()

const fileField = document.querySelector("input[type='file']")

formData.append("username", "abc123")

// file fields provide a collection of files, apparently.
formData.append("avatar", fileField.files[0])

fetch("https://example.com/profile/avatar", {
  method: "PUT",
  headers: {
    "Content-type": "application/x-www-form-urlencoded",
  },
  body: formData,
})
  .then(response => response.json())
  .catch(error => console.error("Error:", error))
  .then(response => console.log("Success:", JSON.stringify(response)))
```

In a React context, the information would be obtained using a React \`ref\` instead of the POJS \`querySelector\`, but it ends up close to the same afterwards:

```javascript
class FileUploadForm extends React.Component {
  fileFieldRef = React.createRef()

  handleSubmit = () => {
    let formData = new FormData()
    const fileField = this.fileFieldRef.current

    formData.append("username", "abc123")
    formData.append("avatar", fileField.files[0])

    fetch("https://example.com/profile/avatar", {
      method: "PUT",
      headers: {
        "Content-type": "application/x-www-form-urlencoded",
      },
      body: formData,
    })
      .then(response => response.json())
      .catch(error => console.error("Error:", error))
      .then(response => console.log("Success:", JSON.stringify(response)))
  }

  // ...

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <input type="file" ref={this.fileFieldRef} />
      </form>
    )
  }
}
```

And in ever more modern React:

```javascript
function FileUploadForm(props) {
  const fileFieldRef = useRef()

  function handleSubmit() {
    let formData = new FormData()
    const fileField = fileFieldRef.current

    formData.append("username", "abc123")
    formData.append("avatar", fileField.files[0])

    fetch("https://example.com/profile/avatar", {
      method: "PUT",
      headers: {
        "Content-type": "application/x-www-form-urlencoded",
      },
      body: formData,
    })
      .then(response => response.json())
	  // I'm sure there is something more useful than this, but ...
      .then(response => console.log("Success:", JSON.stringify(response)))
      .catch(error => console.error("Error:", error))
  }

  // ...

  return (
    <form onSubmit={handleSubmit}>
      <input type="file" ref={fileFieldRef} />
    </form>
  )
}
```
