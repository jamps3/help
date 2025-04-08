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
```

## ✅ Relaatiotietokantojen hyödyt

- **Tietojen eheys:** Viiteavaimet ja rajoitteet takaavat datan johdonmukaisuuden.
- **Standardoitu SQL-kieli:** Laajasti tuettu ja tunnettu kyselykieli.
- **Tehokkaat kyselyt:** Voidaan hakea ja yhdistellä tietoja monimutkaisilla tavoilla.
- **Yksiselitteinen rakenne:** Tiedon rakenne on määritelty ja helppo ymmärtää.
- **Transaktioiden tuki:** Tuki ACID-ominaisuuksille (Atomicity, Consistency, Isolation, Durability).
- **Skaalautuva lukupainotteisiin sovelluksiin:** Soveltuu hyvin sovelluksiin, joissa on paljon lukupyyntöjä.

---

## ⚠️ Relaatiotietokantojen haitat

- **Joustamattomuus:** Rakenteen muuttaminen voi olla hankalaa muuttuvissa tarpeissa.
- **Monimutkaisuus suurissa järjestelmissä:** Useiden taulujen väliset suhteet voivat tehdä järjestelmästä monimutkaisen.
- **Heikompi suorituskyky tietyissä skenaarioissa:** Esimerkiksi suurivolyymisissa, hajautetuissa NoSQL-tyyppisissä käyttötapauksissa.
- **Vaatii tarkkaa suunnittelua:** Hyvän suorituskyvyn ja eheyden takaamiseksi suunnitteluun on panostettava alusta asti.
- **Ei optimaalinen joustavan skeeman datalle:** Esimerkiksi JSON-pohjainen data tai muuttuva rakenne sopii paremmin NoSQL-malleihin.

---

> Hyödyt painottuvat rakenteiseen, ennustettavaan ja tarkasti hallittuun tietoon. Haitat korostuvat dynaamisissa ja erittäin skaalautuvissa ympäristöissä.

