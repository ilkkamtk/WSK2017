# Lomaketapahtumat, File API ja Canvas

## Lomaketapahtumat
* [HTML Events](https://www.w3schools.com/tags/ref_eventattributes.asp)
* [All events](https://developer.mozilla.org/en-US/docs/Web/Events)
* [Input attributes](https://www.w3schools.com/tags/tag_input.asp)

### Esimerkki
* Kokeile esim JSFiddlessä

HTML:
```html
<input type="file" name="fileInput" multiple>
```
JS:
```ecmascript 6
const inputElement = document.querySelector('input');

inputElement.addEventListener('change', (evt) => {
  const allFiles = inputElement.files;
  console.log(allFiles);
});
```

## File API

* [Blob](https://developer.mozilla.org/en-US/docs/Web/API/Blob)
* [File API](https://developer.mozilla.org/en-US/docs/Web/API/File)
* [FileReader](https://developer.mozilla.org/en-US/docs/Web/API/FileReader)

### Esimerkki
HTML:
```html
<input type="file" name="fileInput">
<img>
```
JS:
```ecmascript 6
const inputElement = document.querySelector('input');
const reader = new FileReader();

inputElement.addEventListener('change', (evt) => {
  const file = inputElement.files[0];
  reader.readAsDataURL(file);
});

reader.addEventListener('load', (evt) => {
  console.log(reader.result);
  document.querySelector('img').src = reader.result;
});

```
## Canvas
* [HTML5 Canvas](https://www.w3schools.com/html/html5_canvas.asp)
* [Kuvat ja canvas](https://www.w3schools.com/graphics/canvas_images.asp)
### Esimerkki
HTML:
```html
<input type="file" name="fileInput">
<canvas></canvas>
```
JS:
```ecmascript 6
const inputElement = document.querySelector('input');
const reader = new FileReader();
const canvas = document.querySelector('canvas');
const ctx = canvas.getContext("2d");
const img = document.createElement('img');

inputElement.addEventListener('change', (evt) => {
	const file = inputElement.files[0];
  reader.readAsDataURL(file);
});

reader.addEventListener('load', (evt) => {
  img.src = reader.result;
});

img.addEventListener('load', (evt) => {
  ctx.drawImage(img, 0, 0, 200, 200);
});
```
CSS:
```css
canvas {
  width: 200px;
  height: 200px;
  border: 1px #000 solid;
}
```
## Harjoitus
1. Lataa tämä repo zippinä https://github.com/ilkkamtk/WebPer6 ja pura se
