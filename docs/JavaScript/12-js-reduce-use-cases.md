---
title: Reduce() - Anwendungsbeispiele
description: Beispiele für die Verwendung der reduce()-Methode in JavaScript.
parent: JavaScript
nav_order: 3
layout: default
---

![bg left:50% 80%](../../assets/imgs/spg_logo.png)

# reduce() - Anwendungsbeispiele
Die `reduce()`-Methode ist äußerst vielseitig und wird in vielen Bereichen der JavaScript-Programmierung verwendet. Hier sind einige gängige Einsatzgebiete von `reduce()`:

## 1. **Summen und Produkte berechnen**
`reduce()` eignet sich hervorragend, um die Summe oder das Produkt aller Elemente in einem Array zu berechnen.

```javascript
const numbers = [1, 2, 3, 4, 5];
const sum = numbers.reduce((acc, num) => acc + num, 0);
console.log(sum); // 15
```

## 2. **Datenaggregationen**
`reduce()` wird oft verwendet, um komplexe Daten zu aggregieren, wie z. B. das Zusammenfassen von Objekten oder das Sammeln von Statistiken.

Beispiel: Berechnung des Gesamtalters aller Personen in einem Array von Objekten.

```javascript
const people = [
  { name: 'Alice', age: 25 },
  { name: 'Bob', age: 30 },
  { name: 'Charlie', age: 35 }
];

const totalAge = people.reduce((acc, person) => acc + person.age, 0);
console.log(totalAge); // 90
```

## 3. **Arrays in Objekte umwandeln**
`reduce()` kann verwendet werden, um Arrays in Objekte umzuwandeln, wobei z. B. die Schlüssel anhand bestimmter Eigenschaften des Arrays erstellt werden.

Beispiel: Ein Array in ein Objekt umwandeln, wobei die Namen der Personen die Schlüssel sind:

```javascript
const people = [
  { name: 'Alice', age: 25 },
  { name: 'Bob', age: 30 },
  { name: 'Charlie', age: 35 }
];

const peopleByName = people.reduce((acc, person) => {
  acc[person.name] = person;
  return acc;
}, {});

console.log(peopleByName);
// { Alice: { name: 'Alice', age: 25 }, Bob: { name: 'Bob', age: 30 }, Charlie: { name: 'Charlie', age: 35 } }
```

## 4. **Verschachtelte Datenstrukturen glätten**
Wenn man verschachtelte Arrays (Arrays innerhalb von Arrays) hat, kann `reduce()` verwendet werden, um sie zu "flatten" – also alle Ebenen in ein einziges Array zu konvertieren.

```javascript
const nestedArray = [[1, 2], [3, 4], [5, 6]];
const flatArray = nestedArray.reduce((acc, val) => acc.concat(val), []);
console.log(flatArray); // [1, 2, 3, 4, 5, 6]
```

## 5. **Einzigartige Werte finden (Deduplication)**
`reduce()` kann verwendet werden, um doppelte Werte in einem Array zu eliminieren und ein Array mit nur eindeutigen Werten zu erstellen.

```javascript
const numbers = [1, 2, 3, 4, 3, 2, 1];
const uniqueNumbers = numbers.reduce((acc, num) => {
  if (!acc.includes(num)) {
    acc.push(num);
  }
  return acc;
}, []);

console.log(uniqueNumbers); // [1, 2, 3, 4]
```

## 6. **Komplexe Berechnungen oder Datenpipelines**
`reduce()` kann auch für komplexere Berechnungen oder Pipelines verwendet werden, in denen mehrere Schritte in der Verarbeitung von Daten ausgeführt werden müssen.

Beispiel: Berechnen des Durchschnitts von Werten.

```javascript
const numbers = [10, 20, 30, 40];
const average = numbers.reduce((acc, num, idx, arr) => acc + num / arr.length, 0);
console.log(average); // 25
```

## 7. **Zähler (Häufigkeit von Werten berechnen)**
`reduce()` kann verwendet werden, um die Häufigkeit von Werten in einem Array zu zählen. Dies wird oft in Datenanalysen verwendet, um die Anzahl des Vorkommens eines bestimmten Werts zu berechnen.

```javascript
const items = ['apple', 'banana', 'apple', 'orange', 'banana', 'apple'];

const count = items.reduce((acc, item) => {
  acc[item] = (acc[item] || 0) + 1;
  return acc;
}, {});

console.log(count); 
// { apple: 3, banana: 2, orange: 1 }
```

## 8. **Verkettung von Promises**
Wenn du eine Reihe von asynchronen Aufgaben hast, die in einer bestimmten Reihenfolge ausgeführt werden müssen, kannst du `reduce()` verwenden, um Promises nacheinander zu verketten.

```javascript
const tasks = [
  () => Promise.resolve('Task 1 done'),
  () => Promise.resolve('Task 2 done'),
  () => Promise.resolve('Task 3 done')
];

tasks.reduce((acc, task) => acc.then(() => task()), Promise.resolve())
  .then(() => console.log('All tasks done'));
```

## Fazit

`reduce()` ist eine extrem flexible und leistungsfähige Methode, die weit über einfache Summen hinausgeht. Es kann für eine Vielzahl von Aufgaben eingesetzt werden, von der einfachen Aggregation bis hin zur Umwandlung von Datenstrukturen, der Eliminierung von Duplikaten und sogar der asynchronen Verarbeitung von Promises.