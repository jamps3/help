# Relaatiotietokannat – Tiivistelmä

## 📘 Mikä on relaatiotietokanta?

Relaatiotietokanta on tietokantamalli, jossa data tallennetaan **taulukoihin (relaatioihin)**. Jokainen taulu sisältää rivejä (tietueita) ja sarakkeita (attribuutteja). Malli perustuu relaatiomatematiikkaan.

---

## 🔑 Peruskäsitteet

- **Taulu (table):** Datan säilytysrakenne.
- **Tietue (row):** Yksittäinen rivi taulussa.
- **Attribuutti (column):** Tietueen ominaisuus, esim. nimi tai ikä.
- **Ensisijainen avain (primary key):** Yksilöi jokaisen tietueen.
- **Viiteavain (foreign key):** Viittaa toisen taulun ensisijaiseen avaimeen (yhdistää tauluja).

---

## 💡 Esimerkki

**Asiakkaat-taulu:**

| AsiakasID | Nimi              | Sähköposti           |
|-----------|-------------------|----------------------|
| 1         | Maija Meikäläinen | maija@example.com    |

**Tilaukset-taulu:**

| TilausID | AsiakasID | Päivämäärä   |
|----------|-----------|--------------|
| 101      | 1         | 2025-04-08   |

---

## 🛠 Käyttötarkoitukset

- Sovellusten ja verkkopalvelujen tietojen hallinta
- Raportointi ja analytiikka
- Datan varastointi, kun rakenne on tärkeä

**Yleisiä tietokantajärjestelmiä:**
- MySQL
- PostgreSQL
- SQLite
- Microsoft SQL Server

---

## 💬 SQL – Structured Query Language

Kieli, jolla relaatiotietokantoja käsitellään.

```sql
-- Esimerkki SELECT-kyselystä
SELECT * FROM Asiakkaat WHERE Nimi = 'Maija Meikäläinen';

-- Esimerkki INSERT-kyselystä
INSERT INTO Tilaukset (TilausID, AsiakasID, Päivämäärä)
VALUES (102, 1, '2025-04-08');
