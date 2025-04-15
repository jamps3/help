# Yleisimmät komennot SQL-kyselyissä:

| Komento | Selitys |
|---------|---------|
|SELECT|Valitaan jotain tiettyä tietoa tauluista, joihin osoitetaan FROM komennolla. Esimerkiksi SELECT age FROM celebs hakee celeb nimisestä taulukosta listan, joka sisältää age nimisen sarakkeen tiedot. Lisäksi valintaa voidaan tarkentaa WHERE komennolla.|
|CREATE TABLE|Luo uuden taulukon tietokantaan. Taululle pitää antaa luontivaiheessa kenttien nimet ja tietotyypit. Lisäksi kentille voi antaa esimerkiksi Primary Key arvon.|
|ALTER TABLE|Mahdollistaa jo olemassa olevan taulukon muokkaamisen. Olemassa olevia sarakkeita voidaan muokata tai sarakkeita voidaan lisätä tai poistaa.|
|INSERT|Taulukkoon syötetään uusi tietue.|
|UPDATE|Muokataan taulukkoon syötettyä tietoa.|
|DELETE|Voidaan poistaa tietue taulukosta. Tässäkin komennossa käsiteltävä taulu valitaan komennolla FROM ja tarkennuksia annetaan WHERE-komentoa käyttäen.|

| Apukomento | Selitys|
|------------|--------|
|OR|Tai, jompi kumpi ehdoista täytyy täyttyä|
|AND|Ja, molempien ehtojen täytyy täyttyä|
|ASC|Nouseva järjestys|
|DESC|Laskeva järjestys|
|NOT|Negatiivinen ehto|

Esim. ASIAKAS-taulukko, kentät:
```sql
ASIAKASNUMERO, laskuri
ETUNIMI, teksti
SUKUNIMI, teksti
PUHELIN, teksti
PALKKA, luku
```
```sql
SELECT * FROM Customers WHERE Country="Sweden";
INSERT INTO ASIAKAS(ETUNIMI, SUKUNIMI,PUHELIN) VALUES(’Jarkko’, ’Turpeinen’,’123456’);
UPDATE ASIAKAS SET PALKKA = PALKKA + 150  WHERE ETUNIMI=’Matti’;
DELETE FROM ASIAKAS WHERE ASIAKASNUMERO=110;
```
```sql
SELECT CustomerID, CustomerName, Country
FROM Customers
WHERE Country="Finland";
```
```
Valitse kentät CustomerID, CustomerName, Country
Taulusta Customers
Joiden Country on Sweden
Järjestä CustomerName mukaan LASKEVASSA järjestyksessä
```
```sql
SELECT CustomerID, CustomerName, Country
FROM Customers
WHERE Country='Sweden'
ORDER BY CustomerName DESC;
```
```
Komennoissa toimivat hipsut: ', "
Nämä eivät käy: `
```
# [SQL Tutorial @ w3schools.com](https://www.w3schools.com/sql/)
