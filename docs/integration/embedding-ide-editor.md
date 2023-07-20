# Embedding IDE Editor

The AgorApp IDE Editor can be seamlessly integrated into partner websites using an iframe.

## Basic usage

Insert editor by following code:

```html
<iframe
  src="url"
  title="IDE"
  allowFullScreen
  style="width: 100%; height: 600px"
  id="editor"
/>
```

`url` has to be in following format `https://agorapp.dev/ide-embed/{topic}/{slug}`, where `{topic}` and `{slug}` is 
defined by AgorApp Challenge/Course.

Example of live URL: `https://agorapp.dev/ide-embed/solidity/optimized-array-sum`

## Advanced usage

Based on a prior agreement with AgorApp, you can transfer information about the currently logged-in user to the IDE, 
in order to match the solution with the user.

Communication is based on [Window: postMessage() method](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage).

### External ID

Here is a sample code to pass the external ID towards the IDE.

```javascript
let externalId = '0xFFF00000000000000000000000000FFF';
document.getElementById("editor").contentWindow.postMessage({
        action: 'set-external-id',
        data: {
            type: 'metamask',
            value: externalId
        },
    },
    "*"
);
```
