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

## Customizing the appearance of the IDE

You can customize the behavior of the IDE by using parameters in the URL.

The following parameters are supported:
- `brand` - allows you to change the color of the buttons of the IDE. When not mentioned, the AgorApp brand will be used as default one. The following values are supported:
  - `rare-skills` - purple brand
- `hideTheory` - allows you to hide theory sidebar and menu. The following values are supported:
  - `1` - hide theory sidebar
  - `0` - hide theory sidebar. Default value.

Example:
```
https://agorapp.dev/ide-embed/solidity/optimized-array-sum?brand=rare-skills&hideTheory=1
```
