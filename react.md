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
