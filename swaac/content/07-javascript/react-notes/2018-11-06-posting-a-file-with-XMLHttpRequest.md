---
title: "2018 11 06 Posting a File With XMLHttpRequest"
date: 2020-01-11T09:28:02-06:00
draft: true
---

## RESEARCH: Posting a file with XMLHttpRequest ##

- Time-stamp: <2019-10-09 01:00:08 tamara>
- published date: 2018-11-06 Tue 13:46
- keywords: XMLHttpRequest, file upload, JavaScript, research, React

See: [Using nothing but XMLHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/Using_XMLHttpRequest#Using_nothing_but_XMLHttpRequest) &rarr; maybe not

See: [Using FormData objects](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/Using_XMLHttpRequest#Using_FormData_objects) &rarr; necessary for files, I think

In contrast to [Posting with Fetch API](./2018-11-06-posting-a-file-with-fetch-api.md), this is a bit lower on the food chain in terms of JS stuff, **but** it lets you get access to `progress` events, for doing such things as displaying a progress bar. Yay.

### Using FormData ###

[MDN](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/Using_XMLHttpRequest#Using_FormData_objects) makes a special note:

> Note: As we said, FormData objects are not stringifiable objects. If you want to stringify a submitted data, use the previous pure-AJAX example. Note also that, although in this example there are some file <input> fields, when you submit a form through the FormData API you do not need to use the FileReader API also: files are automatically loaded and uploaded.

### Using Event Handlers ###

From the top of the page, just using / setting event handlers:

```javascript
function reqListener () {
  console.log(this.responseText);
}

var oReq = new XMLHttpRequest();

// this sets the 'load' event handler, which fires when the file is fully loaded.
// I think this works for POST/PUT as well...
oReq.addEventListener("load", reqListener);

oReq.open("GET", "http://www.example.org/example.txt");
oReq.send();
```

There's a note [somewhere on the page](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/Using_XMLHttpRequest#Monitoring_progress) saying something about `progress` event handlers needing to be set before the `.open` call.

This would load up all the event handlers for XMLHttpRequest:

```javascript
let oReq = new XMLHttpRequest();

oReq.addEventListener("progress", updateProgress);
oReq.addEventListener("load", transferComplete);
oReq.addEventListener("error", transferFailed);
oReq.addEventListener("abort", transferCanceled);

oReq.open();
```

### Progress Indication ###

The `progress` event handler takes in the progress event, which is defined at [WhatWG Progress Event specification](https://xhr.spec.whatwg.org/#interface-progressevent). It has 3 attributes:

- `lengthComputable` [boolean] whether the length of the object is known
- `loaded` [number] how much has loaded so far
- `total` [number] how much there is to load

So progress can be calculated by (assuming class-style component):

```javascript
handleProgress = event => {
  let progress = 0
  if (event.total !== 0) {
    progress = event.loaded / event.total
  }
  const percentCompleted = progress * 100
  this.setState({ progress, percentCompleted })
}

handleLoaded = event => {
  this.setState({ progress: 1, percentCompleted: 100, loaded: true })
}

// ...

request = () => {
  const req = new XMLHttpRequest()

  req.addEventListener('progress', this.handleProgress)
  req.addEventListener('load', this.handleLoaded)

  // ... etc
}
```

This would be much cooler as a hook-based component, wouldn't it?
