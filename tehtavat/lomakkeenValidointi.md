### JavaScrip LAB 1


## Lomakkeen validointi
  * Tee Documents kansioon uusi kansio 'WebPerusteet'
  * Lataa tämä repo zippinä https://github.com/ilkkamtk/WebPer1 ja pura se 'WebPerusteet' kansioon

## Elementtien valitseminen ja muokkaaminen sekä tapahtumat
  * avaa ladattu kansio PHPStormilla (tai vast)
  * avaa esimerkki.html
  * opetellaan yhdessä valitsemaan ja muokkaamaan elementtejä sekä lisätään tapahtumia (event)
  * Apuja: 
    * http://www.w3schools.com/jsref/met_document_queryselector.asp
    * http://www.w3schools.com/jsref/prop_html_innerhtml.asp
    * http://www.w3schools.com/jsref/met_element_setattribute.asp
    * http://www.w3schools.com/js/js_htmldom_eventlistener.asp
    * https://medium.com/modern-javascript/javascript-event-handlers-280ed3cc5631


### Tehtävä A 
1. Avaa teht_a.html editorissa
2. Tee lomake, jossa on seuraavat kentät:
  * Etunimi
  * Sukunimi
  * Sähköpostiosoite
  * Puhelinnumero
  * Osoite
  * Postinumero
  * Salasana
  * Lähetä-nappi
3. Tarkasta HTML koodi validaattorilla, ja tee validaattorin mahdollisesti ehdottamat muutokset
4. Tee lomakkeen validointi (tarkistus) HTML5 avulla
  * Etunimi ja sukunimi ovat pakollisia
  * Sähköpostiosoitteen on oltava oikeaa muotoa ja se on pakollinen
  * Puhelinnumeron on oltava muotoa +358401234567
  * Osoite ja postinumero eivät ole pakollisia, mutta postinumeron on oltava tasan 5 numeroa
  * Salasana pitää olla peitetty ja se on pakollinen
  * Apuja
    * http://www.the-art-of-web.com/html/html5-form-validation/
    * http://www.w3schools.com/TAgs/att_input_pattern.asp
    * http://www.regular-expressions.info/tutorial.html
    * https://regex101.com/
  * Tee myös CSS mikäli aikaa riittää (Muokkaa css-kansion main.css -tiedostoa)

### Tehtävä B 
1. Avaa teht_b.html editorissa
2. Kopioi tehtävä A:ssa tekemäsi lomake
3. Lisää form-elementtiin novalidate attribuutti (HTML5 validointi pois päältä)
4. Tee lomakkeen validointi JavaScriptin avulla
  * Tarkistetaan samat ominaisuudet, kuin tehtävässä A
    * `const elementti = document.querySelector()`
    * `const elementit = document.querySelectorAll()`
    * `elementti.addEventListener('submit', funktio)`
    * `elementti.setAttribute('style', 'cssOminaisuus: arvo;')`
  * Jos tarkistus ei mene läpi, lomakkeen lähettäminen estetään
    * `preventDefault()`
  * Apuja
    * https://www.w3schools.com/jsref/jsref_regexp_exec.asp
    * https://www.w3schools.com/jsref/jsref_obj_regexp.asp
    
### Tehtävä C
#### Lomakkeen vastaanottaminen PHP:llä
1. Tee kaksi uutta tiedostoa: lomakeGET.php ja lomakePOST.php
2. Tulosta PHP:llä lomakkeesta tullut data. 
  * Lähetä data teht_a.html:stä GET-metodilla ja teht_b.html:stä POST-metodilla.
  * lomakeGET.php vastaanottaa teht_a.html:n datan
  * lomakePOST.php vastaanottaa teht_b.html:n datan
  * Apuja
    * https://www.w3schools.com/php/php_forms.asp
3. Validoi lomakkeesta tullut data
  * Apuja
    * https://www.w3schools.com/php/php_form_validation.asp
    * https://www.w3schools.com/php/php_form_required.asp
    * https://www.w3schools.com/php/php_form_url_email.asp
