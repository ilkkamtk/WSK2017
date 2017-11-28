# PDO Cheatsheet

### Yhteyden luominen
```php
$user = 'omasi';		//Käytäjänimi 
$pass = 'omasi';		//Salasana, ei OMAn vaan phpAdminin
$host = 'mysql.metropolia.fi';  //Tietokantapalvelin
$dbname = 'omasi';		//Tietokanta
// Muodostetaan yhteys tietokantaan
try {     //Avataan yhteys tietokantaan ($DBH on nyt luotu yhteysolio, nimi vapaasti valittavissa)
    $DBH = new PDO("mysql:host=$host;dbname=$dbname", $user, $pass);
    // virheenkäsittely: virheet aiheuttavat poikkeuksen
    $DBH->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );
    // käytetään  merkistöä utf8
    $DBH->exec("SET NAMES utf8;");
} catch(PDOException $e) {
    echo 'Yhteysvirhe: '.$e->getMessage();  
    //Voidaan myös kirjoittaa mahdollinen virheviesti tiedostoon
    // file_put_contents('log/DBErrors.txt', 'Connection: '.$e->getMessage()."\n", FILE_APPEND);
    //HUOM hakemistopolku ja oikeudet
}

```

### Haku ilman parametrejä
```php
$kysely = $DBH->prepare("SELECT url FROM kuvat;");
$kysely->execute();
while($tulosolio = $kysely->fetchClass()){
    // testataan mitä tulos sisältää
    print_r($tulosolio)
}
```
### Haku parametreillä
```php
// esimerkkiparametri
$param = 1;

$kysely = $DBH->prepare("SELECT url FROM kuvat WHERE kuvaID = :kID;");
$kysely->bindParam(':kID', $param)
$kysely->execute();
while($tulosolio = $kysely->fetchClass()){
    // testataan mitä tulos sisältää
    print_r($tulosolio)
}
```

##### Toinen vaihtoehto: parametrit taulukossa
```php
// esimerkkiparametri taulukkona
$param = array('kID' => 1);

$kysely = $DBH->prepare("SELECT url FROM kuvat WHERE kuvaID = :kID;");
$kysely->execute($param);
while($tulosolio = $kysely->fetchClass()){
    // testataan mitä tulos sisältää
    print_r($tulosolio)
}
```

### Tiedon lisääminen
```php
$param = array('enimi' => 'Sampo', 'snimi' => 'Sompa');

$kysely = $DBH->prepare("INSERT INTO users (etunimi, sukunimi) VALUES (:enimi, :snimi);");
$kysely->execute($param);
```
* voit myös kayttää bindParam() -metodia

### Tiedon muokkaaminen
```php
$param = array('enimi' => 'Saimi', 'userID' => '1');

$kysely = $DBH->prepare("UPDATE users SET etunimi = :enimi WHERE uID = :userID;");
$kysely->execute($param);
```
* voit myös kayttää bindParam() -metodia

### Tiedon poistaminen
```php
$param = array('userID' => '1');

$kysely = $DBH->prepare("DELETE FROM users WHERE uID = :userID;");
$kysely->execute($param);
```
* voit myös kayttää bindParam() -metodia

