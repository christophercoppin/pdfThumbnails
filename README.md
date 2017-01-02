# PDF Thumbnails

A small script to parse html files and generate a source image  for `img` elements 
with a `data-pdf-thumbnail-file` attribute linking to a pdf file.  
The image is a view of the first page of the pdf. The script relies on the [pdf.js](https://github.com/mozilla/pdf.js) library.
 
## Online demo

See a [PDF Thumbnails demo here](https://scandel.github.io/pdfThumbnails/).

## Getting started

First get a local copy of the code, clone it using git:
```
$ git clone git://github.com/scandel/pdfThumbnails
$ cd pdfThumbnails
```
Then get a local copy of pdf.js. Use the prebuilt version that you can find on [this page](https://mozilla.github.io/pdf.js/getting_started/).
Download and extract it. You only need to keep the `build` directory (with both `pdf.js` and `pdf.worker.js`). Make 
sure your directory structure looks like: 

```
    pdfThumbnails
    |--pdf.js
    |  |--build
    |     |--pdf.js
    |     |--pdf.worker.js
    |--pdfThumbnails.js
    |--index.html
    |--example.pdf
    ...
```    

Now visit `index.html` in your browser, you should see the demo page with thumbnails of `example.pdf`. 

## Use it in your own project

You just need to keep the `pdfThumbnails.js` file from this project, and the `pdf.js` and `pdf.worker.js` files from pdf.js
(let them both in the same directory as pdf.js will try to load the worker). In your html file, include the javascripts:
```
<script src="/path/to/pdf.js"></script>
<script src="/path/to/pdfThumbnails.js"></script>
```
To show a thumbnail, write an `img` element with a `data-pdf-thumbnail-file` attribute:
```
<img data-pdf-thumbnail-file="/my/file.pdf">
``` 
The pdf file path is a relative or absolute path to a file hosted on your site (no cross domain request).

You can add a width _or_ a height in pixels for the generated image. If not, the size of the generated image will be 
the one of the pdf.
```
<img data-pdf-thumbnail-file="/my/file.pdf" data-pdf-thumbnail-width="200">
<img data-pdf-thumbnail-file="/my/file.pdf" data-pdf-thumbnail-height="150">
```