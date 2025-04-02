---
title: Array-Methoden & Spread Operator
nav_order: 2
layout: default
parent: JavaScript
---

![bg left:50% 80%](../../assets/imgs/spg_logo.png)

# WMC – Array-Methoden

## 1. `filter()`

- Erstellt ein neues Array mit den Elementen, die eine bestimmte Bedingung erfüllen.
- Rückgabewert: Ein neues Array mit den passenden Elementen.
- Verwendung: Elemente auswählen, die eine Bedingung erfüllen.

```javascript
const numbers = [1, 2, 3, 4, 5];
const filteredNumbers = numbers.filter(num => num > 3);
console.log(filteredNumbers); // [4, 5]
```

---

## 2. `find()`

- Gibt das **erste** Element zurück, das die Bedingung erfüllt.
- Rückgabewert: Ein einzelnes Element oder `undefined`.

```javascript
const numbers = [1, 2, 3, 4, 5];
const foundNumber = numbers.find(num => num > 3);
console.log(foundNumber); // 4
```

---

## 3. `some()`

- Prüft, ob **mindestens ein Element** eine Bedingung erfüllt.
- Rückgabewert: `true` oder `false`.

```javascript
const numbers = [1, 2, 3, 4, 5];
const hasNumberOver3 = numbers.some(num => num > 3);
console.log(hasNumberOver3); // true
```

---

## 4. `map()`

- Erstellt ein neues Array durch Transformation jedes Elements.

**Beispiel: Namen extrahieren**

```javascript
const people = [
  { name: "Anna", birthdate: "1995-03-25" },
  { name: "Ben", birthdate: "1991-08-14" },
  { name: "Clara", birthdate: "2000-01-05" }
];

const names = people.map(person => person.name);
console.log(names); // ["Anna", "Ben", "Clara"]
```

**Beispiel: Alter berechnen**

```javascript
function calculateAge(birthdate) {
  const today = new Date();
  const birthDate = new Date(birthdate);
  return Math.floor((today - birthDate) / (1000 * 60 * 60 * 24 * 365.25));
}

const peopleWithAge = people.map(person => ({
  name: person.name,
  age: calculateAge(person.birthdate)
}));

console.log(peopleWithAge);
// [
//   { name: "Anna", age: 29 },
//   { name: "Ben", age: 33 },
//   { name: "Clara", age: 24 }
// ]
```

---

## 5. `reduce()`

Reduziert ein Array auf einen einzigen Wert (z. B. Summe, Produkt).

**Syntax:**

```javascript
array.reduce((accumulator, currentValue) => {
  // Operation
}, initialValue);
```

**Beispiel – Summe:**

```javascript
const numbers = [1, 2, 3, 4, 5];
const sum = numbers.reduce((acc, curr) => acc + curr, 0);
console.log(sum); // 15
```

**Beispiel – Gesamtalter:**

```javascript
const people = [
  { name: 'Alice', age: 25 },
  { name: 'Bob', age: 30 },
  { name: 'Charlie', age: 35 }
];

const totalAge = people.reduce((acc, person) => acc + person.age, 0);
console.log(totalAge); // 90
```

---

## Vergleich der Methoden

| Methode     | Zweck                                              | Rückgabewert              |
|-------------|----------------------------------------------------|----------------------------|
| `filter()`  | Elemente nach Bedingung herausfiltern              | Neues Array                |
| `find()`    | Erstes passendes Element finden                    | Ein Element oder `undefined` |
| `some()`    | Prüfen, ob ein passendes Element existiert         | `true` oder `false`        |
| `map()`     | Jedes Element transformieren                       | Neues Array                |
| `reduce()`  | Alle Elemente auf einen Wert reduzieren            | Einzelner Wert             |

---

## Spread Operator (`...`)

### Kopieren eines Arrays

```javascript
const originalArray = [1, 2, 3];
const copiedArray = [...originalArray];
console.log(copiedArray); // [1, 2, 3]
```

### Arrays kombinieren

```javascript
const array1 = [1, 2, 3];
const array2 = [4, 5, 6];
const combinedArray = [...array1, ...array2];
console.log(combinedArray); // [1, 2, 3, 4, 5, 6]
```

---
