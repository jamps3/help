# SQL: Viite-eheys

## 🔍 Mitä on viite-eheys?

**Viite-eheys (referential integrity)** on tietokantojen sääntö, jonka tarkoituksena on varmistaa, että vierasavaimet viittaavat olemassa oleviin tietueisiin toisessa taulussa. Se ylläpitää tiedon johdonmukaisuutta ja estää virheelliset viittaukset taulujen välillä.

## 🔗 Keskeiset käsitteet

- **Ensisijainen avain (PRIMARY KEY)**: Yksilöllinen tunniste jokaiselle riville taulussa.
- **Vierasavain (FOREIGN KEY)**: Sarake, joka viittaa toisen taulun ensisijaiseen avaimeen.

## 📋 Esimerkki

```sql
-- Taulu asiakkaille
CREATE TABLE Asiakkaat (
  asiakas_id INT PRIMARY KEY,
  nimi VARCHAR(100)
);

-- Taulu tilauksille, viitaten asiakas_id:hen
CREATE TABLE Tilaukset (
  tilaus_id INT PRIMARY KEY,
  asiakas_id INT,
  FOREIGN KEY (asiakas_id) REFERENCES Asiakkaat(asiakas_id)
);
```

Tässä `Tilaukset.asiakas_id` viittaa `Asiakkaat.asiakas_id`:hen. Tämä tarkoittaa, että `Tilaukset`-tauluun ei voi lisätä tilausta, jonka `asiakas_id` ei löydy `Asiakkaat`-taulusta.

## ⚠️ Miksi viite-eheys on tärkeää?

- Estetään virheelliset ja rikkinäiset viittaukset.
- Ylläpidetään tietojen eheyttä eri taulujen välillä.
- Vältetään ns. "orvot rivit" (orphans), eli viittaavia rivejä ilman vastaavaa pääavainta.
- Auttaa tietokantaa pysymään loogisesti yhtenäisenä.

## 🛠️ Toimintavaihtoehdot vierasavaimille

Kun viitattu rivi poistetaan tai päivitetään, voidaan määrittää seuraavat toiminnot:

- `ON DELETE CASCADE` – Poistaa automaattisesti viittaavat rivit.
- `ON DELETE SET NULL` – Asettaa vierasavaimen `NULL`:iksi.
- `ON DELETE RESTRICT` / `NO ACTION` – Estää poiston, jos viittauksia on olemassa.
- `ON UPDATE CASCADE` – Päivittää vierasavaimet automaattisesti, jos pääavain muuttuu.

### Esimerkki `ON DELETE CASCADE`:

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

## ✅ Yhteenveto

Viite-eheys:

- Pitää tietokannan rakenteen loogisena.
- Estää ristiriitaisia tietoja.
- Mahdollistaa automaattisia toimenpiteitä viittausten yhteydessä.

## 📚 Lähteet

- [W3Schools – SQL Foreign Key](https://www.w3schools.com/sql/sql_foreignkey.asp)
- [PostgreSQL Documentation – Referential Integrity](https://www.postgresql.org/docs/current/ddl-constraints.html)
- [Oracle Docs – Integrity Constraints](https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/CONSTRAINT.html)
- Silberschatz, Korth & Sudarshan: *Database System Concepts*
