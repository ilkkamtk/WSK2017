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

### AJAX get metodilla
#### Vanha tapa
```javascript
const xhr = new XMLHttpRequest();
xhr.open('get', 'tulostaJSON.php');
xhr.onreadystatechange = function(){
   if (xhr.readyState == 4 && xhr.status == 200) {
         const tulos = JSON.parse(xhr.responseText);
         console.log(tulos);
      }
}
xhr.send();
```
#### Uudempi
```javascript
fetch('tulostaJSON.php')
  .then( (vastaus) => {
    return vastaus.json();
  })
  .then( (tulos) => {
    console.log(tulos);
  });
```

### AJAX post metodilla
#### Vanha tapa
```javascript
// haetaan data esim. lomakkeesta
const lomake = document.querySelector('form');
const tiedot = new FormData(lomake);
const xhr = new XMLHttpRequest();
xhr.open('post', 'tulostaJSON.php');
xhr.onreadystatechange = function(){
   if (xhr.readyState == 4 && xhr.status == 200) {
         const tulos = JSON.parse(xhr.responseText);
         console.log(tulos);
      }
}
xhr.send(tiedot);
```
#### Uudempi
```javascript
// haetaan data esim. lomakkeesta
const lomake = document.querySelector('form');
const tiedot = new FormData(lomake);
// asetusobjekti fetchiä varten 
const asetukset = {
  method: 'post',
  data: tiedot
};
fetch('tulostaJSON.php', asetukset)
  .then( (vastaus) => {
    return vastaus.json();
  })
  .then( (tulos) => {
    console.log(tulos);
  });
```