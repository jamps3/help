# Relaatiotietokannat ja NoSQL
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

# 🗂️ NoSQL-tietokannat – Tiivistelmä

## 📘 Mikä on NoSQL?

**NoSQL (Not Only SQL)** viittaa tietokantamalleihin, jotka **eivät noudata relaatiomallia**. Ne on suunniteltu käsittelemään **suuria määriä hajautettua, joustavaa ja usein puolistrukturoitua dataa**. 

NoSQL-tietokannat eivät käytä tauluja ja SQL-kieltä samalla tavalla kuin relaatiotietokannat – ne tukevat erilaisia malleja ja voivat olla hyvin skaalautuvia.

---

## 🧩 NoSQL-mallit

NoSQL-tietokannat jaetaan neljään päätyyppiin:

1. **Dokumenttipohjaiset** (esim. MongoDB)  
   - Tiedot tallennetaan JSON- tai BSON-dokumentteina.
2. **Avain-arvo -pohjaiset** (esim. Redis, DynamoDB)  
   - Tieto tallennetaan yksinkertaisina avain-arvo -pareina.
3. **Saraketietokannat** (esim. Apache Cassandra)  
   - Optimoitu suurten datamäärien käsittelyyn sarakekohtaisesti.
4. **Graafitietokannat** (esim. Neo4j)  
   - Suunniteltu monimutkaisten suhteiden (solmujen ja kaarien) mallintamiseen.

---

## ✅ NoSQL:n hyödyt

- **Skaalautuvuus:** Helppo hajauttaa horisontaalisesti (usealle palvelimelle).
- **Joustava skeema:** Ei vaadi kiinteää rakennetta – soveltuu muuttuvaan dataan.
- **Korkea suorituskyky:** Erityisesti suurten luku- ja kirjoitusmäärien käsittelyyn.
- **Parempi tuki hajautetuille järjestelmille:** Hyvä valinta pilvipohjaisiin sovelluksiin.

---

## ⚠️ NoSQL:n haitat

- **Vähemmän standardoitu:** Ei yhtä yhtenäistä kyselykieltä kuin SQL.
- **Rajoitettu transaktiotuki:** Joissain järjestelmissä puutteellinen ACID-tuki.
- **Monimutkaisempi tiedon eheyden hallinta:** Viiteavaimia ja rajoitteita ei aina ole.
- **Vähemmän tuttu perinteisille kehittäjille:** SQL on yhä standardi monessa ympäristössä.

---

## 💡 Käyttökohteita

- Reaaliaikaiset sovellukset (esim. chatti, pelit)
- Suurten datamäärien analytiikka
- Hajautetut web-palvelut
- Sovellukset, joissa tietorakenne vaihtelee nopeasti

---

> **Yhteenveto:**  
> NoSQL tarjoaa tehokkaan ja joustavan tavan käsitellä dynaamista ja suurivolyymista dataa, mutta sen käyttö vaatii usein erilaista ajattelutapaa kuin relaatiotietokannoissa.

