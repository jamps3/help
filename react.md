# React

React on JavaScript-kirjasto käyttöliittymien rakentamiseen. Se on komponenttipohjainen, tehokas ja suosittu tapa rakentaa moderneja web-sovelluksia.

---

## 📚 Sisällysluettelo
- [🔧 Peruskäyttö](#-peruskäyttö)
- [🧩 Komponentit](#-komponentit)
- [🔁 Elinkaarikoukut (Hooks)](#-elinkaarikoukut-hooks)
- [📦 Tilanhallinta](#-tilanhallinta)
- [🌐 API-pyynnöt](#-api-pyynnöt)
- [🎨 Tyylit](#-tyylit)
- [🧪 Testaus](#-testaus)
- [🛠️ Hyödyllisiä työkaluja](#️-hyödyllisiä-työkaluja)
- [📚 Lisämateriaalia](#-lisämateriaalia)

---

## 🔧 Peruskäyttö

### 1. Asennus (esim. Vite-projekti)
```bash
npm create vite@latest my-app --template react
cd my-app
npm install
npm run dev
```

### 2. JSX
- JSX on JavaScriptin laajennos, jolla voi kirjoittaa HTML:n kaltaista syntaksia.
```jsx
const element = <h1>Hello, world!</h1>;
```

---

# REACT- ja NODE.js -npm-komentoja

## 1. Node.js-asennus

Jotta voit käyttää Reactia ja Node.js:ää, asenna ensin Node.js-ympäristö omalle koneellesi asennusohjelmalla.

Asennuspaketti löytyy osoitteesta:  
👉 [https://nodejs.org/en/download](https://nodejs.org/en/download)

## 2. NPM-peruskomennot

**NPM** (Node Package Manager) on internetissä sijaitseva tietovarasto, johon julkaistaan avoimen lähdekoodin Node.js-projekteja. Sen avulla voidaan asentaa, päivittää ja hallita projekteissa käytettäviä paketteja ja niiden riippuvuuksia. NPM asentuu Node.js:n mukana ja sitä käytetään komentoriviltä, esim. Visual Studio Coden Terminal-ikkunassa.

| **NPM-komento**                          | **Selitys** |
|------------------------------------------|-------------|
| `npm install <paketin_nimi>`             | Asentaa paketin. Voit käyttää parametria `-g`, jolloin asennus tapahtuu globaalisti. |
| `npm uninstall <paketin_nimi>`           | Poistaa paketin. |
| `node -v` ja `npm -v`                     | Tarkistaa Node.js- ja NPM-versiot sekä asennuksen onnistumisen. |
| `npm remove <paketin_nimi>`              | Sama kuin uninstall, vaihtoehtoinen tapa. |
| `npm install -g create-react-app`        | Asentaa `create-react-app`-työkalun globaalisti. |
| `create-react-app testi`                 | Luo uuden `testi`-nimisen React-projektin. |
| `npm start`                              | Käynnistää sovelluksen ja avaa selaimen osoitteeseen `http://localhost:3000`. |
| `npm run build` tai `npm run-script build` | Luo tuotantoversion sovelluksesta. |

## 3. NPM-kirjastoja ym.

| **NPM-komento**                          | **Selitys** |
|------------------------------------------|-------------|
| `npm install styled-components`          | Tyylikirjasto komponenttipohjaiseen tyylittelyyn. |
| `npm install bootstrap`                  | Bootstrap-tyylikirjaston asennus. |
| `npm install react-fetch`                | Fetch API:n käyttö Reactissa. |
| `npm install -g json-server`             | Asentaa json-serverin globaalisti. |
| `json-server --watch FakeDb.json`        | Käynnistää json-serverin, joka lukee tiedostoa `FakeDb.json`. |
| `json-server --watch FakeDb.json --port 4000` | Käynnistää json-serverin eri portissa. |
| `npm run server`                         | Käynnistää json-serverin (edellyttää erillistä skriptiä `package.json`-tiedostossa). |
| `npm install react-redux`                | Reduxin asennus tilanhallintaan. |
| `npm install react-logger`               | Loggeri React-sovelluksiin. |
| `npm install prop-types`                 | Tyyppitarkistuksia React-komponenteille. |
| `npm install react-promise-middleware`   | Middleware-paketti promissien käsittelyyn. |
| `npm install react-table`                | Taulukkojen luominen. |
| `npm install react-charts`               | Erilaiset kaaviot: pylväs-, ympyräkaaviot jne. |
| `npm install react-form`                 | Lomakkeiden hallinta. |
| `npm install react-jsonschema-form`      | Lomakkeiden luonti JSON-skeeman perusteella. |
| `npm install react-leaflet`              | Leaflet-karttojen käyttö Reactissa. |
| `npm install react-axios`                | Axios-kirjaston käyttö Reactissa. |
| `npm install express`                    | Node.js-sovellusten kehykseksi tarkoitettu web-kehys. Tukee mm. reititystä, middlewareja ja asetusten hallintaa. |
| `npm install axios`                      | Promise-pohjainen HTTP-asiakas, joka toimii sekä selaimessa että Node.js:ssä. Vaihtoehto `fetch`:ille. |


## 🧩 Komponentit

### Funktiokomponentti
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

### Props
- Propsit välittävät tietoa komponentille:
```jsx
<Welcome name="Maija" />
```

### State (React Hook)
```jsx
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  return (
    <button onClick={() => setCount(count + 1)}>
      Clicks: {count}
    </button>
  );
}
```

---

## 🔁 Elinkaarikoukut (Hooks)

### `useEffect`
- Suorittaa sivuvaikutuksia (esim. API-kutsut).
```jsx
useEffect(() => {
  console.log('Komponentti renderöity');
}, []);
```

---

## 📦 Tilanhallinta

### Yksinkertainen tila:
- `useState`, `useReducer`, `useContext`

### Isommat sovellukset:
- Zustand, Redux, Recoil jne.

---

## 🌐 API-pyynnöt

```jsx
useEffect(() => {
  fetch('/api/data')
    .then(res => res.json())
    .then(data => setData(data));
}, []);
```

---

## 🎨 Tyylit

- CSS-tiedostot
- CSS Modules
- styled-components
- Chakra UI (esim. `<Button colorScheme="blue">Klikkaa</Button>`)

---

## 🧪 Testaus

- React Testing Library
- Jest

---

## 🛠️ Hyödyllisiä työkaluja

- **Vite** – kevyt kehitystyökalu
- **React DevTools** – selainlaajennus tilan tarkasteluun
- **TypeScript** – lisää tyypitykset komponentteihin
- **ESLint + Prettier** – koodinlaadun varmistukseen

---

## 📚 Lisämateriaalia

- [reactjs.org](https://reactjs.org)
- [usehooks.com](https://usehooks.com)
- [Chakra UI](https://chakra-ui.com/)
