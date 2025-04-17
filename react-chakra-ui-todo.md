# TODO-sovellus Reactilla ja Chakra UI:lla

Tässä ohjeessa tehdään tyylikäs Todo-sovellus Reactilla käyttäen [Chakra UI](https://chakra-ui.com/):ta käyttöliittymäkomponentteihin.

---

## 🛠️ 1. Ympäristön valmistelu

### Asenna Node.js (jos ei vielä asennettu)
👉 [https://nodejs.org/](https://nodejs.org/)

Tarkista versiot:

```bash
node -v
npm -v
```

### Luo uusi React-projekti

```bash
npx create-react-app chakra-todo
cd chakra-todo
```

---

## 🎨 2. Asenna Chakra UI

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

---

## ⚙️ 3. Lisää ChakraProvider

Muokkaa `src/index.js` tiedostoa (tai `main.tsx` jos käytät TypeScriptiä):

```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import { ChakraProvider } from '@chakra-ui/react';
import App from './App';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <ChakraProvider>
      <App />
    </ChakraProvider>
  </React.StrictMode>
);
```

---

## ✍️ 4. Sovelluksen logiikka ja ulkoasu

Korvaa `src/App.js` seuraavalla koodilla:

```jsx
import React, { useState } from 'react';
import {
  Box,
  Button,
  Input,
  VStack,
  HStack,
  Text,
  Heading,
  Checkbox,
  IconButton
} from '@chakra-ui/react';
import { DeleteIcon } from '@chakra-ui/icons';

function App() {
  const [todos, setTodos] = useState([]);
  const [input, setInput] = useState('');

  const addTodo = () => {
    if (!input.trim()) return;
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
    <Box p={8} maxW="500px" mx="auto">
      <Heading mb={6} textAlign="center">📝 Todo-lista</Heading>
      <HStack mb={4}>
        <Input
          placeholder="Lisää tehtävä"
          value={input}
          onChange={(e) => setInput(e.target.value)}
        />
        <Button onClick={addTodo} colorScheme="teal">Lisää</Button>
      </HStack>

      <VStack spacing={3} align="stretch">
        {todos.map((todo, index) => (
          <HStack key={index} justify="space-between">
            <Checkbox
              isChecked={todo.done}
              onChange={() => toggleTodo(index)}
            >
              <Text as={todo.done ? 'del' : undefined}>{todo.text}</Text>
            </Checkbox>
            <IconButton
              icon={<DeleteIcon />}
              colorScheme="red"
              onClick={() => deleteTodo(index)}
              aria-label="Poista"
            />
          </HStack>
        ))}
      </VStack>
    </Box>
  );
}

export default App;
```

---

## 🚀 5. Käynnistä sovellus

```bash
npm start
```

Sovellus käynnistyy selaimessa osoitteessa `http://localhost:3000`.

---

## ✅ Valmista!

Sinulla on nyt tyylikäs ja toimiva Todo-sovellus Chakra UI:n avulla. Voit helposti lisätä ominaisuuksia, kuten:
- tallennuksen `localStorage`:iin
- tumma/vaalea-teemat
- animaatiot (esim. Framer Motion)
