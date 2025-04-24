# TODO-sovellus Reactilla

Tässä ohjeessa tehdään yksinkertainen Todo-sovellus Reactilla. Sovelluksessa käyttäjä voi lisätä, merkitä valmiiksi ja poistaa tehtäviä.

## 🛠️ 1. Ympäristön valmistelu

### Asenna Node.js (jos ei vielä asennettu)
Lataa ja asenna osoitteesta:  
👉 [https://nodejs.org/](https://nodejs.org/)

Tarkista versiot:

```bash
node -v
npm -v
```

### Luo uusi React-projekti

```bash
npm create vite@latest todo-app --- --template react-swc-ts
cd todo-app
npm start
```

Tämä käynnistää projektin selaimessa osoitteessa `http://localhost:3000`.

---

## 📁 2. Kansion rakenne

Käytämme oletusrakennetta. Päämuutokset tehdään tiedostoon `src/App.js` (tai `App.tsx`, jos käytät TypeScriptiä).

---

## ✍️ 3. Todo-sovelluksen koodi

### Korvaa `src/App.js` seuraavalla:

```jsx
import React, { useState } from 'react';
import './App.css';

function App() {
  const [todos, setTodos] = useState([]);
  const [input, setInput] = useState('');

  const addTodo = (e) => {
    e.preventDefault();
    if (input.trim() === '') return;
    setTodos([...todos, { text: input, done: false }]);
    setInput('');
  };

  const toggleTodo = (index) => {
    const newTodos = [...todos];
    newTodos[index].done = !newTodos[index].done;
    setTodos(newTodos);
  };

  const deleteTodo = (index) => {
    const newTodos = todos.filter((_, i) => i !== index);
    setTodos(newTodos);
  };

  return (
    <div className="App">
      <h1>📝 Todo-lista</h1>
      <form onSubmit={addTodo}>
        <input
          value={input}
          onChange={(e) => setInput(e.target.value)}
          placeholder="Lisää tehtävä"
        />
        <button type="submit">Lisää</button>
      </form>

      <ul>
        {todos.map((todo, index) => (
          <li
            key={index}
            style={{ textDecoration: todo.done ? 'line-through' : 'none' }}
          >
            {todo.text}
            <button onClick={() => toggleTodo(index)}>
              {todo.done ? 'Palauta' : 'Valmis'}
            </button>
            <button onClick={() => deleteTodo(index)}>Poista</button>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default App;
```

---

## 🎨 4. Tyylit (valinnainen)

Lisää yksinkertaiset tyylit `src/App.css`-tiedostoon:

```css
.App {
  text-align: center;
  margin-top: 2rem;
  font-family: sans-serif;
}

input {
  padding: 0.5rem;
  font-size: 1rem;
  margin-right: 0.5rem;
}

button {
  margin-left: 0.25rem;
  padding: 0.4rem 0.6rem;
  cursor: pointer;
}
```

---

## 🚀 5. Sovelluksen suoritus

Käynnistä sovellus:

```bash
npm start
```

---

## 📦 6. Lisävinkkejä

- Voit tallentaa tehtävät `localStorage`:en, jotta ne säilyvät sivun päivityksen jälkeen.
- Tyylittele käyttämällä esim. `styled-components` tai `bootstrap`.
- Harjoittele komponenttien pilkkomista pienempiin osiin (esim. `TodoItem`, `TodoList`, `TodoForm`).

---

## ✅ Valmista!

Sinulla on nyt yksinkertainen mutta toimiva Todo-sovellus tehtynä Reactilla.
