# SQL: Viite-eheys

## 🔍 1. Viite-eheys relaatiotietokannassa
`Viite-eheys` (referential integrity) on yksi relaatiotietokantojen neljästä keskeisestä eheystyypistä (domain, entity, referential, user-defined). Se keskittyy siihen, että viittaus toisen taulun tietueeseen on aina kelvollinen.
Se on tietokantojen sääntö, jonka tarkoituksena on varmistaa, että vierasavaimet viittaavat olemassa oleviin tietueisiin toisessa taulussa. Se ylläpitää tiedon johdonmukaisuutta ja `estää virheelliset viittaukset taulujen välillä.`
Ilman viite-eheyttä voisi syntyä tilanteita, joissa esimerkiksi tilaus on tehty asiakkaalle, jota ei ole olemassa – tämä rikkoo tietokannan loogista rakennetta.

## 🧩 2. Vierasavaimen määrittely ja säännöt
`Vierasavain` voi viitata vain `ensisijaiseen avaimeen` tai `yksilölliseen (UNIQUE) kenttään` toisessa taulussa.
`Viitattu rivi täytyy olla olemassa` ennen kuin vierasavaimeen viittaava rivi lisätään.
`Et voi poistaa` viitattua `riviä, jos siihen viitataan` vierasavaimella, ellei käytössä ole esim. `ON DELETE CASCADE`.

### 🔗 Keskeiset käsitteet
- **Ensisijainen avain (`PRIMARY KEY`)**: Yksilöllinen tunniste jokaiselle riville taulussa.
- **Vierasavain (`FOREIGN KEY`)**: Sarake, joka viittaa toisen taulun ensisijaiseen avaimeen.

## 🔁 3. Käyttäytyminen muutostilanteissa
Kun viitattu tieto muuttuu (päivitetään tai poistetaan), tietokannan on tehtävä jotain, jotta viite-eheys säilyy.

### 🛠️ Toimintavaihtoehdot vierasavaimille
| Toiminto    | Selitys     |
| ----------- | ----------- |
| CASCADE |              Automaattisesti poistaa/päivittää viittaavat rivit |
| SET NULL |             Asettaa vierasavaimen arvoksi NULL |
| SET DEFAULT |          Asettaa vierasavaimen oletusarvoon |
| RESTRICT / NO ACTION | Estää poiston tai päivityksen, jos viittauksia löytyy (vakioasetus) |

## 📘 4. Esimerkki käytännön tilanteesta
Ajatellaan verkkokaupan tietokantaa:
Taulu `Tuotteet`: sisältää tuotetiedot
Taulu `Tilausrivit`: jokainen rivi vastaa yhtä tilattua tuotetta

```sql
CREATE TABLE Tuotteet (
  tuote_id INT PRIMARY KEY,
  nimi VARCHAR(100)
);

CREATE TABLE Tilausrivit (
  tilausrivi_id INT PRIMARY KEY,
  tuote_id INT,
  maara INT,
  FOREIGN KEY (tuote_id)
    REFERENCES Tuotteet(tuote_id)
    ON DELETE SET NULL
);
```
Jos tuote poistetaan Tuotteet-taulusta, sitä koskevien tilausrivien tuote_id asetetaan NULL:iksi. Näin tiedot tilauksista säilyvät, vaikka tuote ei ole enää saatavilla.

## 📋 Esimerkki
-- Taulu asiakkaille
```sql
CREATE TABLE Asiakkaat (
  asiakas_id INT PRIMARY KEY,
  nimi VARCHAR(100)
);
```
-- Taulu tilauksille, viitaten asiakas_id:hen
```sql
CREATE TABLE Tilaukset (
  tilaus_id INT PRIMARY KEY,
  asiakas_id INT,
  FOREIGN KEY (asiakas_id) REFERENCES Asiakkaat(asiakas_id)
);
```
Tässä `Tilaukset.asiakas_id` viittaa `Asiakkaat.asiakas_id`:hen. Tämä tarkoittaa, että `Tilaukset`-tauluun ei voi lisätä tilausta, jonka `asiakas_id` ei löydy `Asiakkaat`-taulusta.

## 📋Esimerkki `ON DELETE CASCADE`:
```sql
CREATE TABLE Tilaukset (
  tilaus_id INT PRIMARY KEY,
  asiakas_id INT,
  FOREIGN KEY (asiakas_id)
    REFERENCES Asiakkaat(asiakas_id)
    ON DELETE CASCADE
);
```
Jos asiakas poistetaan `Asiakkaat`-taulusta, kaikki hänen tilauksensa poistetaan automaattisesti.

## 🛡️ 5. Yhteenveto - Miksi tämä on tärkeää kehittäjälle? ⚠️
- ✅ Tietojen luotettavuus: Et voi tehdä virheellisiä viittauksia. Tietojen eheyttä ylläpidetään eri taulujen välillä. Vältetään ns. "orvot rivit" (orphans), eli viittaavia rivejä ilman vastaavaa pääavainta.
- ✅ Ylläpidettävyys: Vähemmän manuaalista virheiden tarkistusta sovelluskoodissa.
- ✅ Automaattinen käyttäytyminen: Voi säästää aikaa ja vähentää bugeja esim. poistoketjuissa.
- ✅ Tietoturva: Estetään tahattomat datan katkokset.

```
+-----------+       REFERENCES        +-----------+
| Customers |------------------------>| Orders    |
+-----------+                         +-----------+
| CustomerID| (Primary Key)           | OrderID   |
| Name      |                         | CustomerID| (Foreign Key)
+-----------+                         | Date      |
                                      +-----------+
```
- `Customers`-taulussa on yksilöllinen avain (Primary Key) kentässä `CustomerID`.
- `Orders`-taulu sisältää viittausavaimen (Foreign Key) `CustomerID`, joka viittaa `Customers`-tauluun, varmistaaen että jokaisella tilauksella on olemassaoleva asiakas.

## 📚 Lähteet

- [W3Schools – SQL Foreign Key](https://www.w3schools.com/sql/sql_foreignkey.asp)
- [PostgreSQL Documentation – Referential Integrity](https://www.postgresql.org/docs/current/ddl-constraints.html)
- [Oracle Docs – Integrity Constraints](https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/CONSTRAINT.html)
- Silberschatz, Korth & Sudarshan: *Database System Concepts*
