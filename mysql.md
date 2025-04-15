# Yleisimmät komennot SQL-kyselyissä:

| Komento | Selitys |
|---------|---------|
|SELECT|Valitaan jotain tiettyä tietoa tauluista, joihin osoitetaan FROM komennolla. Esimerkiksi SELECT age FROM celebs hakee celeb nimisestä taulukosta listan, joka sisältää age nimisen sarakkeen tiedot. Lisäksi valintaa voidaan tarkentaa WHERE komennolla.|
|CREATE TABLE|Luo uuden taulukon tietokantaan. Taululle pitää antaa luontivaiheessa kenttien nimet ja tietotyypit. Lisäksi kentille voi antaa esimerkiksi Primary Key arvon.|
|ALTER TABLE|Mahdollistaa jo olemassa olevan taulukon muokkaamisen. Olemassa olevia sarakkeita voidaan muokata tai sarakkeita voidaan lisätä tai poistaa.|
|INSERT|Taulukkoon syötetään uusi tietue.|
|UPDATE|Muokataan taulukkoon syötettyä tietoa.|
|DELETE|Voidaan poistaa tietue taulukosta. Tässäkin komennossa käsiteltävä taulu valitaan komennolla FROM ja tarkennuksia annetaan WHERE-komentoa käyttäen.|
## Apukomennot
| Apukomento | Selitys|
|------------|--------|
|OR|Tai, jompi kumpi ehdoista täytyy täyttyä|
|AND|Ja, molempien ehtojen täytyy täyttyä|
|ASC|Nouseva järjestys|
|DESC|Laskeva järjestys|
|NOT|Negatiivinen ehto|
|IN|Useampi arvo WHERE komennossa Esim. WHERE Country IN ('Germany', 'France', 'UK');|
|BETWEEN|Valitaan arvot, Esim. WHERE Price BETWEEN 15 AND 20;|
|YEAR|Poimitaan vuosiluku päivämäärästä Esim. YEAR(päivämäärä_tietue)|

## Esim. ASIAKAS-taulukko, kentät:
```sql
ASIAKASNUMERO, laskuri
ETUNIMI, teksti
SUKUNIMI, teksti
PUHELIN, teksti
PALKKA, luku
```
## Esimerkkilauseita
```sql
SELECT * FROM Customers WHERE Country="Sweden";
INSERT INTO ASIAKAS(ETUNIMI, SUKUNIMI,PUHELIN) VALUES(’Jarkko’, ’Turpeinen’,’123456’);
UPDATE ASIAKAS SET PALKKA = PALKKA + 150  WHERE ETUNIMI=’Matti’;
DELETE FROM ASIAKAS WHERE ASIAKASNUMERO=110;
```
Hae kentät 'CustomerID', 'CustomerName', 'Country' taulusta 'Customers' joiden 'Country' on 'Finland':
```sql
SELECT CustomerID, CustomerName, Country
FROM Customers
WHERE Country="Finland";
```
Lisää 'Email' tauluun sarake 'Customers' jonka tyyppi on varchar(255):
```sql
ALTER TABLE Customers
ADD Email varchar(255);
```
Hae kirjat joiden Title on näiden kahden kirjan otsikoiden välissä:
```sql
SELECT Title
FROM Books
WHERE Title BETWEEN 'Brave New World' AND 'Pride and Prejudice';
```
| Lause | Selitys |
|-------|---------|
|SELECT CustomerID, CustomerName, Country|Valitse kentät CustomerID, CustomerName, Country|
|FROM Customers|Taulusta Customers|
|WHERE Country='Sweden'|Joiden Country on Sweden|
|ORDER BY CustomerName DESC;|Järjestä CustomerName mukaan LASKEVASSA järjestyksessä|

## Hipsut!
Kaikki hipsut eivät toimi ja joskus toiset toimivat ja toiset eivät, tässä yleisimmät.
```
Komennoissa toimivat hipsut: ' ja "
Nämä eivät käy: `
```
# [SQL Tutorial @ w3schools.com](https://www.w3schools.com/sql/)
