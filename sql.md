# Yleisimmät komennot SQL-kyselyissä ovat:

| Komento | Selitys |
| ----------- | ----------- |
| SELECT | Tällä komennolla valitaan jotain tiettyä tietoa tauluista, joihin osoitetaan FROM komennolla. Esimerkiksi SELECT age FROM celebs hakee celeb nimisestä taulukosta listan, joka sisältää age nimisen sarakkeen tiedot. Lisäksi valintaa voidaan tarkentaa WHERE komennolla. |
| CREATE TABLE | Luo nimensä mukaisesti uuden taulukon tietokantaan. Taululle pitää antaa luontivaiheessa kenttien nimet ja tietotyypit. Lisäksi esimerkiksi kentille voi antaa esimerkiksi Primary Key arvon. |
| ALTER TABLE | Mahdollistaa jo olemassa olevan taulukon muokkaamisen. Olemassa olevia sarakkeita voidaan muokata tai sarakkeita voidaan lisätä taulukkoon tai poistaa taulukosta. |
| INSERT | Taulukkoon syötetään uusi tietue. |
| UPDATE | Voidaan muokata taulukkoon syötettyä tietoa. |
| DELETE | Voidaan poistaa tietue taulukosta. Tässäkin komennossa käsiteltävä taulu valitaan komennolla FROM ja tarkennuksia annetaan WHERE-komentoa käyttäen. |

## Esim. ASIAKAS-taulukko, kentät:
	ASIAKASNUMERO, laskuri
	ETUNIMI, teksti
	SUKUNIMI, teksti
	PUHELIN, teksti
	PALKKA, luku
## Komennot
	INSERT INTO ASIAKAS(ETUNIMI, SUKUNIMI,PUHELIN) VALUES(’Jarkko’, ’Turpeinen’,’123456’);
	UPDATE ASIAKAS SET PALKKA = PALKKA + 150  WHERE ETUNIMI=’Matti’;
	DELETE FROM ASIAKAS WHERE ASIAKASNUMERO=110;
