# HTTP-statuskoodit

Statuskoodit (status code) kuvaavat palvelimella tapahtunutta toimintaa kolmella numerolla. Statuskoodien avulla palvelin kertoo mahdollisista ongelmista tai tarvittavista lisätoimenpiteistä. Yleisin statuskoodi on 200, joka kertoo kaiken onnistuneen oikein.

## Sisällysluettelo

- [1xx – Informaatioviestit](#1xx--informaatioviestit)
- [2xx – Onnistuneet tapahtumat](#2xx--onnistuneet-tapahtumat)
- [3xx – Uudelleenohjaukset](#3xx--uudelleenohjaukset)
- [4xx – Asiakasvirheet](#4xx--asiakasvirheet)
- [5xx – Palvelinvirheet](#5xx--palvelinvirheet)

---

## 1xx – Informaatioviestit

| Koodi | Nimi                  | Kuvaus |
|-------|-----------------------|--------|
| 100   | Continue              | Palvelin pyytää asiakasta jatkamaan hakupyyntöä. |
| 101   | Switching Protocols   | Palvelin hyväksyy selaimen ehdottaman protokollan vaihdon. |

---

## 2xx – Onnistuneet tapahtumat

| Koodi | Nimi                       | Kuvaus |
|-------|----------------------------|--------|
| 200   | OK                         | Hakupyyntö onnistui. |
| 201   | Created                    | Uusi dokumentti luotiin. |
| 202   | Accepted                   | Pyyntö hyväksytty, mutta ei vielä toteutettu. |
| 203   | Non-Authoritative Information | Palautettu metatieto ei ole alkuperäislähteestä. |
| 204   | No Content                 | Tyhjä dokumentti palautettu. |
| 205   | Reset Content              | Selaimen tulisi tyhjentää lomake. |
| 206   | Partial Content            | Osittainen vastaus dokumentista. |

---

## 3xx – Uudelleenohjaukset

| Koodi | Nimi                    | Kuvaus |
|-------|-------------------------|--------|
| 300   | Multiple Choices        | Useita versioita dokumentista saatavilla. |
| 301   | Moved Permanently       | Dokumentti on siirretty pysyvästi. |
| 302   | Found                   | Dokumentti on siirretty väliaikaisesti. |
| 303   | See Other               | Hae dokumentti toisaalta. |
| 304   | Not Modified            | Dokumenttia ei ole muutettu. |
| 305   | Use Proxy               | Dokumentti haettava välityspalvelimen kautta. |
| 306   | (Unused)                | Käytöstä poistettu. |
| 307   | Temporary Redirect      | Väliaikainen uudelleenohjaus. |

---

## 4xx – Asiakasvirheet

| Koodi | Nimi                          | Kuvaus |
|-------|-------------------------------|--------|
| 400   | Bad Request                   | Pyyntö oli virheellinen. |
| 401   | Unauthorized                  | Tunnistautuminen vaaditaan. |
| 402   | Payment Required              | Maksu vaaditaan (ei käytössä). |
| 403   | Forbidden                     | Pääsy estetty. |
| 404   | Not Found                     | Dokumenttia ei löydy. |
| 405   | Method Not Allowed            | HTTP-metodi ei ole sallittu. |
| 406   | Not Acceptable                | Ei hyväksyttävä tiedostotyyppi. |
| 407   | Proxy Authentication Required | Välimuistipalvelin vaatii tunnistautumista. |
| 408   | Request Timeout               | Aikakatkaisu palvelimen puolella. |
| 409   | Conflict                      | Konflikti dokumentin kanssa. |
| 410   | Gone                          | Dokumentti on tarkoituksella poistettu. |
| 411   | Length Required               | Pituus puuttuu pyynnöstä. |
| 412   | Precondition Failed           | Ehto ei täyttynyt. |
| 413   | Request Entity Too Large      | Pyyntö oli liian suuri. |
| 414   | Request-URI Too Long          | Osoite oli liian pitkä. |
| 415   | Unsupported Media Type        | Tuntematon mediatyyppi. |
| 416   | Requested Range Not Satisfiable | Pyydetty alue ei ole saatavilla. |
| 417   | Expectation Failed            | Ehdollinen ehto ei täyttynyt. |

---

## 5xx – Palvelinvirheet

| Koodi | Nimi                        | Kuvaus |
|-------|-----------------------------|--------|
| 500   | Internal Server Error       | Palvelimen sisäinen virhe. |
| 501   | Not Implemented             | Toimintoa ei ole toteutettu. |
| 502   | Bad Gateway                 | Vääränmuotoinen vastaus seuraavalta palvelimelta. |
| 503   | Service Unavailable         | Palvelin ei ole käytettävissä. |
| 504   | Gateway Timeout             | Yhteyden aikakatkaisu seuraavaan palvelimeen. |
| 505   | HTTP Version Not Supported  | HTTP-versiota ei tueta. |
