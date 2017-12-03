#JavaScript cheatsheet

### Muuttujat
#### Vanha tapa
```javascript
var nimi = 'Jeppe';
var ika = 10:
```

#### ES6
```javascript
// jos arvo ei muutu myöhemmin
const nimi = 'Jeppe';
// jos arvo muuttuu myöhemmin
let ika = 10;
```

### Funktiot
#### Tosi vanha tapa (paitsi jos teet luokkaan metodia)
```javascript
function munFunktio(param1, param2) {
  // tee jotain 
}
```
#### Vanha tapa
```javascript
var munFunktio = function(param1, param2) {
  // tee jotain
}
```
#### ES6
```javascript
const munFunktio = (param1, param2) => {
  // tee jotain
}
```

### Elementin valitseminen
```html
<p id="namiska">Klikkaa mua</p>
```
```javascript
const elementti = document.querySelector('#namiska');
```

### Tapahtumankäsittely
#### Tosi vanha tapa
```html
<p onclick="munFunktio('jokuarvo1', 'jokuarvo2')">Klikkaa mua</p>
```
#### Vanha tapa
```javascript
elementti.onclick = function(evt){
  munFunktio('jokuarvo1', 'jokuarvo2');
};
```
#### ES6
```javascript
elementti.addEventListener('click',  (evt) => {
  munFunktio('jokuarvo1', 'jokuarvo2');
});
```