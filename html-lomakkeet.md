# HTML Lomakkeet

HTML-lomakkeet ovat keskeinen osa verkkosivujen käyttäjävuorovaikutusta. Niiden avulla voidaan kerätä syötteitä, kuten tekstiä, valintoja ja tiedostoja.

---

## 🧩 Perusrakenne

```html
<form action="/submit" method="post">
  <!-- Syötekentät -->
</form>
```

- `action`: Lomakkeen lähetysosoite.
- `method`: `GET` (tiedot URL-osoitteessa) tai `POST` (tiedot HTTP-pyynnön rungossa).

---
## 📋 `<form>`-elementin yleisimmät alielementit

| Elementti      | Kuvaus                                           |
|----------------|--------------------------------------------------|
| `<input>`      | Monikäyttöinen kenttä, tyyppi määritetään `type`-attribuutilla |
| `<textarea>`   | Monirivinen tekstikenttä                         |
| `<select>`     | Valintalista                                     |
| `<option>`     | Valintalistan yksittäinen vaihtoehto              |
| `<label>`      | Kentän selite, linkitetään `for`-attribuutilla   |
| `<button>`     | Painike (voi olla lähetä, nollaa tai oma toiminto) |
| `<fieldset>`   | Ryhmittelee kenttiä loogisesti                    |
| `<legend>`     | Kuvaa `fieldset`-ryhmän tarkoituksen              |
| `<datalist>`   | Määrittelee vaihtoehdot `input`-kenttään          |
| `<output>`     | Näyttää laskennallisen tuloksen                  |
| `<meter>`      | Edistyksen/arvon graafinen näyttö                 |
| `<progress>`   | Edistymispalkki                                  |
| `<keygen>`     | Luo julkisen/privaatin avainparin lomakkeeseen liittyvää salausta varten (vanhentunut!) <br>Sen sijaan, että avaimet luotaisiin HTML-elementillä, käytetään nyt JavaScriptin Web Crypto API:a, joka mahdollistaa turvallisten avainparien generoinnin ohjelmallisesti.|
---

## 🔡 Yleisimmät syötekentät

```html
<input type="text" name="Nimi" size="20" maxlength="50" value="..." readonly />
<input type="email" name="Sähköposti" />
<input type="tel" name="puhelin" pattern="\+?[0-9 () \-]+" />
<input type="password" name="Salasana" />
<input type="checkbox" name="Uutiskirje" />
<input type="radio" name="sukupuoli" value="mies" />
<input type="submit" value="Lähetä" />
<input type="reset" value="Tyhjennä" />
<input type="color" id="vari" name="vari" />
<input type="number" value="8" min="4" max="10" id="koe" name="koe" />
<input type="range" min="100" max="500" step="100" id="puhhinta" name="puhhinta" />
<input type="url" />
```
## ⏰ Ajanilmaukset
```html
<input type="time" name="Aika" />
<input type="date" name="Päivä" />
<input type="datetime" name="Aika ja päivä" />
<input type="datetime-local" name="Paikallinen aika" />
<input type="month" name="Kuukausi" />
<input type="week" name="Viikko" />
```

## 📝 Tekstialue

```html
<textarea name="viesti" rows="5" cols="30" maxlength="500" wrap="soft"></textarea>
```

## 🔽 Valintalista

```html
<select name="kieli">
  <optgroup label="Kielet">
    <option value="fi">Suomi</option>
    <option value="en">Englanti</option>
  </optgroup>
</select>
```

---

## 🎛️ Asetukset ja attribuutit

| Attribuutti     | Kuvaus                              |
|----------------|--------------------------------------|
| `required`     | Kenttä on pakollinen                 |
| `placeholder`  | Vihjeteksti kentässä                |
| `value`        | Kentän oletusarvo                   |
| `name`         | Kentän nimi lomaketiedon lähetykseen |
| `disabled`     | Kenttä ei ole käytettävissä          |
| `readonly`     | Vain luettavissa, ei muokattavissa   |
| `maxlength`    | Maksimipituus tekstikentälle         |
| `min` / `max`  | Numerokenttien arvovälit             |
| `pattern`      | Säännöllinen lauseke syötteelle      |

---

## 🧪 Validointi (client-side)

HTML5 tarjoaa sisäänrakennettua validointia:

```html
<input type="email" name="email" required />
<input type="text" pattern="[A-Za-z]{3,}" title="Vähintään 3 kirjainta" />
<input type="number" min="1" max="10" />
```

- `required`: Estää lomakkeen lähetyksen, jos kenttä on tyhjä.
- `pattern`: Varmistaa, että syöte noudattaa tiettyä muotoa.
- `min` ja `max`: Rajaa sallittuja arvoja numero- ja päivämääräkentissä.

Voit yhdistää tämän myös JavaScriptillä tarkempaan validointiin:

```html
<form onsubmit="return tarkista(event)">
  <input id="nimi" required />
</form>
<script>
function tarkista(e) {
  const nimi = document.getElementById('nimi').value;
  if (nimi.length < 3) {
    alert("Nimen on oltava vähintään 3 merkkiä pitkä");
    e.preventDefault();
    return false;
  }
  return true;
}
</script>
```

---

## 🔒 Lähetys ja käsittely

- `GET`: Sopii hakulomakkeisiin (esim. hakukoneet)
- `POST`: Käytetään lomakkeissa, joissa lähetetään tietoa palvelimelle (esim. kirjautuminen)

Tieto voidaan käsitellä esim. PHP-, Node.js- tai Python-puolella.

---

## 📂 Tiedoston lataus

```html
<form action="upload.php" method="post" enctype="multipart/form-data">
  <input type="file" name="kuva" />
  <input type="submit" value="Lähetä kuva" />
</form>
```

> Huom! Käytä `enctype="multipart/form-data"` tiedostojen lähetyksessä.

---

## ♿ Saavutettavuus

Käytä `label`-elementtejä parantamaan käytettävyyttä:

```html
<label for="sahkoposti">Sähköposti:</label>
<input id="sahkoposti" type="email" name="sahkoposti" />
```

---

# `<fieldset>` ja `<legend>`

HTML:n `<fieldset>`- ja `<legend>`-elementtejä käytetään ryhmittelemään lomakkeen kenttiä loogisesti ja parantamaan saavutettavuutta.

---

## 🔹 `<fieldset>`

`<fieldset>`-elementti luo visuaalisen ja loogisen kehyksen kenttäryhmälle.

```html
<fieldset>
  <legend>Henkilötiedot</legend>
  <label for="nimi">Nimi:</label>
  <input type="text" id="nimi" name="nimi" required />
  <label for="ika">Ikä:</label>
  <input type="number" id="ika" name="ika" />
</fieldset>
```

---

## 🔸 `<legend>`

`<legend>` antaa kuvauksen `<fieldset>`in sisällöstä.

- Asetetaan ensimmäiseksi elementiksi `<fieldset>`-elementin sisälle.
- Parantaa saavutettavuutta, erityisesti apuvälinekäytössä.

```html
<fieldset>
  <legend>Yhteystiedot</legend>
  <!-- Kentät tähän -->
</fieldset>
```

---

## 🔍 Vinkkejä käytöstä

- Käytä lomakkeissa, joissa on useita osioita (esim. henkilötiedot, maksutiedot).
- Yhdistä `fieldset + legend` saavutettavuusparannuksina `label`- ja `aria`-attribuuttien kanssa.

---

## 📚 Lisätietoa

- [MDN: HTML forms](https://developer.mozilla.org/en-US/docs/Learn/Forms)
- [W3Schools: HTML Forms](https://www.w3schools.com/html/html_forms.asp)
- [Can I use - form features](https://caniuse.com/?search=form)

---

*Päivitetty: 2025*
