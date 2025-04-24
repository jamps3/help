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

## 🔡 Yleisimmät syötekentät

```html
<input type="text" name="nimi" />
<input type="email" name="sahkoposti" />
<input type="password" name="salasana" />
<input type="checkbox" name="uutiskirje" />
<input type="radio" name="sukupuoli" value="mies" />
<input type="submit" value="Lähetä" />
```

## 📝 Tekstialue

```html
<textarea name="viesti" rows="5" cols="30"></textarea>
```

## 🔽 Valintalista

```html
<select name="kieli">
  <option value="fi">Suomi</option>
  <option value="en">Englanti</option>
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

## 📚 Lisätietoa

- [MDN: HTML forms](https://developer.mozilla.org/en-US/docs/Learn/Forms)
- [W3Schools: HTML Forms](https://www.w3schools.com/html/html_forms.asp)
- [Can I use - form features](https://caniuse.com/?search=form)

---

*Päivitetty: 2025*
