---
id: dangerouslySetInnerHTML
title: Render HTML in AJAX response
layout: cookbook
permalink: dangerouslySetInnerHTML.html
prev: initial-ajax.html
---

### Problem
How do I prevent React from escaping HTML

### Solution
By default, React escapes the HTML to prevent XSS. If you really want to render HTML, you can use the dangerouslySetInnerHTML property.

```js
/** @jsx React.DOM */

var fooHTML = React.createClass({
  render: function() {
    return <div dangerouslySetInnerHTML={{__html: this.state.actions}} />
  }
});

React.renderComponent(<fooHTML />, mountNode);
```

### Discusion
React forces this intentionally-cumbersome syntax so that you don't accidentally render text as HTML and introduce XSS bugs.