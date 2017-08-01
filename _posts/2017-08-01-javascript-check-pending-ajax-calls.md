---
layout: post
title: JavaScript check if pending ajax calls exist
description: Small code example how to check if pending ajax calls exists on the page.
---
Sometimes you have to wait until some ajax calls are finished. And then you want to execute some JavaScript code on that
new objects that where putted in from the ajax call.  To check if there are activeRequests you can use 
**window.Ajax.activeRequestCount**. And to re-check if they are now finished you can use **window.setInterval**.

Important is also to clear the intervalID with **window.clearInterval(intervalID)**.

_Here is a small code snippet_
```javascript
// we need to wait for ajax calls to be finished
var intervalID = window.setInterval(
    function() {
        if(window.Ajax.activeRequestCount === 0) {
            console.log('No active ajax calls');
            window.clearInterval(intervalID);
        } else {
            console.log('There are ' + window.Ajax.activeRequestCount + ' active ajax requests');
        }
}, 500);
```
