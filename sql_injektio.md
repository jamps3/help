# SQL-injektio: Yleiskatsaus, esimerkit ja suojautumiskeinot

## Mikä on SQL-injektio?

**SQL-injektio** on kyberhyökkäystekniikka, jossa hyökkääjä syöttää haitallista SQL-koodia verkkosovelluksen syötekenttien kautta manipuloidakseen tietokantaa. Tämän avulla hyökkääjä voi esimerkiksi lukea, muokata tai poistaa tietoja, joihin hänellä ei tulisi olla pääsyä. :contentReference[oaicite:0]{index=0}

## Esimerkki SQL-injektiosta

Kuvitellaan verkkosivusto, jossa käyttäjä kirjautuu sisään syöttämällä käyttäjätunnuksen ja salasanan. Taustalla sovellus suorittaa seuraavan SQL-kyselyn:

```sql
SELECT * FROM käyttäjät WHERE käyttäjätunnus = 'syötetty_tunnus' AND salasana = 'syötetty_salasana';
```
Jos hyökkääjä syöttää käyttäjätunnukseksi esimerkiksi ' OR '1'='1, muodostuu kysely seuraavasti:
```sql
SELECT * FROM käyttäjät WHERE käyttäjätunnus = '' OR '1'='1' AND salasana = '...';
```
Koska ehto '1'='1' on aina tosi, kysely palauttaa kaikki käyttäjät, mahdollistaen luvattoman pääsyn.

Suojautuminen SQL-injektiolta
SQL-injektiolta voi suojautua useilla tavoilla:

Parametrisoidut kyselyt (valmistellut lauseet): Käytä parametrisoituja kyselyitä, joissa SQL-kysely ja syötteet pidetään erillään. Tämä estää syötteiden tulkitsemisen osaksi kyselyä.

Syötteiden validointi: Salli vain odotetut syötteet ja hylkää poikkeavat arvot. Esimerkiksi numerokenttiin hyväksytään vain numerot.

Pääsynhallinta vähimmän oikeuden periaatteella: Anna tietokantakäyttäjille vain tarvittavat oikeudet. Sovelluksen ei tulisi käyttää pääkäyttäjän tunnuksia tietokantaan yhdistettäessä.

Tietokantavirheiden piilottaminen: Älä näytä käyttäjille tarkkoja virheilmoituksia, jotka voivat paljastaa tietokannan rakenteen.

Tietoturvatestaukset: Suorita säännöllisesti tietoturvatestauksia ja käytä työkaluja, jotka havaitsevat mahdolliset haavoittuvuudet.

Lisätietoja ja esimerkkejä
SQL Injection Prevention Cheat Sheet - OWASP

SQL Injection - W3Schools

SQL-injektion opetusohjelma: Kuinka oppia esimerkin avulla - Guru99

Huomio: SQL-injektio on vakava tietoturvauhka, ja sen estäminen vaatii huolellista suunnittelua ja toteutusta. On suositeltavaa pysyä ajan tasalla parhaista käytännöistä ja päivittää järjestelmiä säännöllisesti.
