# Tiedoston tallennus palvelimelle

## Aloitus
1. Lataa tämä repo zippinä https://github.com/ilkkamtk/WebPer5 ja pura se

## 1. Perinteinen versio

* Muokkaa task_a.html ja upload.php tiedostoja:
  * Toimi tämän esimerkin mukaan: http://www.w3schools.com/php/php_file_upload.asp
* shell.metropolia.fi:llä php.ini:n muuttaminen ei onnistu, joten täytyy käyttää `htaccess` tiedostoa
  * ko. tiedosto on tässä harjoituksessa jo valmiina, sieltä täytyy ottaa kommentit (#) pois riviltä, jossa on `AddHandler cgi-script .php`
  * ks. https://wiki.metropolia.fi/display/tietohallinto/Kotisivu-%2C+Shell-+ja+MySQL-palvelut
  * upload.php ja .htaccess tiedostojen oikeudet tulee olla (0)755
    * ks. https://tietohallinto.metropolia.fi/display/tietohallinto/HTTP+403+Forbidden
    * Esim. Mac-terminaali:
```
ssh tunnus@shell.metropolia.fi
cd public_html/kansio/kansio
chmod 755 tiedosto

// tai

chmod -R 755 kansio
```

## 2. Modernimpi versio

* Käytä fetch APIa tiedoston lähettämiseen
* Esimerkki:
```javascript
    // valitaan sivulta input-kenttä, jonka tyyppi on file
    const input = document.querySelector('input[type="file"]');
    // tehdään FormData -objekti
    const data = new FormData();
    // lisätään tiedosto FormData -objektiin.
    // Huomaa että files on taulukko. Voit siis lähettää useampia tiedostoja. 
    data.append('fileToUpload', input.files[0]);
    // tehdään olio asetuksille
    const settings = {
            method: 'POST',
            body: data
        };
    // käynnistetään fetch. Tässä tapauksessa palvelin kertoo
    // uploudin onnistumisen/epäonnistumisen tekstillä. Voi olla myös esim json.
    fetch('upload.php', settings).then((response) => {
        return response.text();
    }).then((text) => {
        console.log(text);
    });
```
* [FormData](https://developer.mozilla.org/en-US/docs/Web/API/FormData)
* Katso tarkemmat ohjeet main_b.js:n kommenteista
