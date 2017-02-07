## aframe-uploadcare-component

A Uploadcare component for A-Frame.

For [A-Frame](https://aframe.io).

### API

| Property | Description | Default Value |
| -------- | ----------- | ------------- |
| publicKey  | You uploadcare's public key |               |

### Functions
- **upload(value, contentType)**
- **download(fileId, callback, binary)**

### Events
- **Upload**
 - `uploadcare-upload-started`: Upload started.
 - `uploadcare-upload-completed` Upload completed succesfully:
   - `url`: Uploadcare CDN url of the uploaded resource.
   - `fileInfo`: Uploadcare [fileInfo  object](https://uploadcare.com/documentation/javascript_api/#file-info).
 - `uploadcare-upload-error`: Something went wrong when uploading.
   - `errorInfo`: Error info.
   - `fileInfo`: Uploadcare [fileInfo  object](https://uploadcare.com/documentation/javascript_api/#file-info).
 - `uploadcare-upload-progress`, {progress: uploadInfo.progress, uploadInfo: uploadInfo})
   - `progress`: Percentage of the current upload progress.
   - `uploadInfo`: [uploadInfo object](https://uploadcare.com/documentation/javascript_api/#upload-info)

### Installation

#### Browser

Install and use by directly including the [browser files](dist):

```html
<head>
  <title>My A-Frame Scene</title>
  <script src="https://aframe.io/releases/0.5.0/aframe.min.js"></script>
  <script src="https://unpkg.com/aframe-uploadcare-component/dist/aframe-uploadcare-component.min.js"></script>
</head>

<body>
  <a-scene uploadcare="publicKey: asdf-1234-zxcv">
  </a-scene>
</body>
```

<!-- If component is accepted to the Registry, uncomment this. -->
<!--
Or with [angle](https://npmjs.com/package/angle/), you can install the proper
version of the component straight into your HTML file, respective to your
version of A-Frame:

```sh
angle install aframe-uploadcare-component
```
-->

#### npm

Install via npm:

```bash
npm install aframe-uploadcare-component
```

Then require and use.

```js
require('aframe');
require('aframe-uploadcare-component');
```

### Example
#### Upload a JSON
```
  var sceneEl = document.querySelector('a-scene');
  sceneEl.addEventListener('uploadcare-upload-completed', function (url) { alert('Uploaded: ' + url);});
  sceneEl.upload(jsonObject, 'application/json');
```

#### Download a JSON
```
  var sceneEl = document.querySelector('a-scene');
  sceneEl.download(url, function (data) {
    console.log('Loaded data', data);
  });
```
