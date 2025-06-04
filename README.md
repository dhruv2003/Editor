# Quill Editor iframe Integration

This project provides a simple, embeddable rich text editor using Quill.js that can be integrated into any website via an iframe. The editor automatically saves content to localStorage based on a document ID parameter.

## Features

- Rich text editing with Quill.js
- Automatic saving to localStorage every 5 seconds
- Document identification via URL parameter
- Easy integration via iframe

## How to Use

### Basic Integration

To embed this editor in your website, use an iframe with the path to the editor:

```html
<iframe 
  src="path/to/index.html" 
  width="100%" 
  height="400" 
  frameborder="0">
</iframe>
```

### Multiple Documents

To manage different documents, use the `docId` query parameter:

```html
<iframe 
  src="path/to/index.html?docId=document1" 
  width="100%" 
  height="400" 
  frameborder="0">
</iframe>

<iframe 
  src="path/to/index.html?docId=document2" 
  width="100%" 
  height="400" 
  frameborder="0">
</iframe>
```

This ensures each document's content is saved separately in localStorage.

### Styling the iframe

You can style the iframe using CSS:

```css
iframe.quill-editor {
  width: 100%;
  height: 400px;
  border: 1px solid #ccc;
  border-radius: 4px;
}
```

### Accessing Editor Content from Parent Page

To access the editor's content from the parent page containing the iframe:

```javascript
// Get content from the iframe's editor
function getEditorContent(iframeId) {
  const iframe = document.getElementById(iframeId);
  return iframe.contentWindow.document.querySelector('.ql-editor').innerHTML;
}

// Example usage
const content = getEditorContent('myEditorIframe');
```

## Browser Support

This editor works in all modern browsers that support:
- localStorage
- iframe
- ES6 JavaScript features

## Customization

You can customize the Quill editor by modifying the initialization options in `index.html`. See the [Quill documentation](https://quilljs.com/docs/configuration/) for more options.

## Limitations

- Content is stored in localStorage, which has a size limit (typically 5-10 MB)
- No server-side storage is implemented by default
- Cross-origin restrictions apply when embedding in different domains
