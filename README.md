# Image Tool Tune

Tunes for the Image Tool Block [Editor.js](https://editorjs.io).

## Features

- Float Image Left/Right
- Resize : 50%, 70%, 100%
- Manual resizing
- Image cropping

**Notes**

The Float functionnality is done in pure CSS. Works seamlessly when creating block, nevertheless, when using it along side Resize or Crop, it might be usefull sometimes to deactivate it while resizing/cropping as it will prevent the next content block from overlapping the current image block, when finished you can reactivate it.

## Installation

### Install via NPM

The package is not available on NPM yet.


### Other methods

#### Manual downloading and connecting

1. Download the file `dist/image-tool-tune.js` to you project
2. Include the script where you normally import other Editor Js Tools.
3. Add new options to the EditorJS Class


## Import in Simple HTML

Include the script where you normally import other Editor Js Tools.

```html
    <!--Editor JS-->
    <script src="https://cdn.jsdelivr.net/npm/@editorjs/editorjs@2.27.2/dist/editorjs.umd.min.js"></script>
    <!--Editor Tool JS-->
    <script src="https://cdn.jsdelivr.net/npm/@editorjs/image@2.3.0"></script>
    <!--Editor Tool Tune-->
    <script src="./dist/image-tool-tune.js"></script>
    [...BODY...]
    <script>
        //On DOM LOADED
        document.addEventListener( 'DOMContentLoaded', function () {
            //Get tune class
            const ImageToolTune = window.ImageToolTune;
            //Get tool class
            const ImageTool = window.ImageTool;

            //Init editor JS
        } );
    </script>
```


## Import in Node (React, Next...)
```javascript
//IMPORT EDITOR JS
import EditorJS from '@editorjs/editorjs';

//IMPORT IMAGE TOOL
import ImageTool from '@editorjs/image';

//IMPORT IMAGE TOOL TUNE (CHANGE PATH ACCORDING TO YOU CONFIG)
import ImageToolTune from '../lib/image-tool-tune';

```

## Load tool in editor js
```javascript
const editor = new EditorJS( {
    holder: 'editorjs', //Your Editor JS Holder ID
    tools: {
        //LOAD THE TUNE
        imageTune: ImageToolTune,
        image: {
            //APPLY THE TUNE TO THE TOOL
            tunes: [ 'imageTune' ],
            class: ImageTool,
        },
    },
    data: {}, //EditorJS Json for loading pre-saved blocks
});
```

## Output data

This Tunes returns `tunes.imageTune` with following format

| Field          | Type      | Description                     |
| -------------- | --------- | ------------------------------- |
| floatLeft       | `boolean` | Image is floating to left        |
| floatRight      | `boolean` | Image is floating to right       |
| center         | `boolean` | Image has a margin:auto         |
| sizeSmall      | `boolean` | Image width is 50% of its container |
| sizeMiddle     | `boolean` | Image width is 70% of its container |
| sizeLarge      | `boolean` | Image width is 100% of its container |
| resize         | `boolean` | Manual resize mode activated ? |
| resizeSize     | `integer` | Width (in px) of the resized image |
| crop           | `boolean` | Manual cropping mode activated ? |
| cropperFrameHeight | `integer` | Height (in px) of the image relative container |
| cropperFrameWidth  | `integer` | Width (in px) of the image relative container |
| cropperFrameLeft   | `integer` | Left position (in px) of the image |
| cropperFrameTop    | `integer` | Top position (in px) of the  image |
| cropperImageHeight | `integer` | Height (in px) of the image |
| cropperImageWidth  | `integer` | Width (in px) of the  image |




```json
{
   "tunes": { 
    "imageTune": { 
        "floatLeft": true, 
        "floatRight": false, 
        "center": false, 
        "sizeSmall": false, 
        "sizeMiddle": false, 
        "sizeLarge": false, 
        "resize": false, 
        "resizeSize": 0, 
        "crop": true,
        "cropperFrameHeight": 158.16171875000003, 
        "cropperFrameWidth": 180.2658808997665, 
        "cropperFrameLeft": -222.4233718312208, 
        "cropperFrameTop": -149.29999999999995, 
        "cropperImageHeight": 638, 
        "cropperImageWidth": 639.7024683122081 
        }
    }
}
```


### About cropping
The cropping functionnality is implemented using Cropper.js v1.5.13. 
All documentation available here : https://fengyuanchen.github.io/cropperjs
