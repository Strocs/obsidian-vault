---
id: 1727801920-reduce-method
aliases:
  - Reduce Method
tags:
  - javascript
  - languages
---

# Reduce Method

Reduce es un método de arreglos que itera sobre elementos y devuelve un elemento final que es el resultado de la operación de reducción. Recibe dos argumentos, el primero es el callback de reducción y el segundo el valor inicial que tendrá el el valor acumulado.

El callback recibe tres argumentos:

- `(acc, _, _) => {}`
- será el primer valor del arreglo en la primera iteración o el valor inicial declarado en el método reduce `.reduce(callback, initialAccValue)`
- será el valora cumulado de la operación de reducción aplicada en cada iteración.
- `(acc, el, _) => {}`
  - será a la variable que se está iterando, corresponde al segundo valor del arreglo en la primera iteración
- `(acc, el, i) => {}`
  - será el índice del elemento actual en la iteración

```js
const numbers = [1, 2, 3, 4, 5];

const sum = numbers.reduce((acc, el, i) => {
  return acc + el;
}, 0);

console.log(sum); // 15
```
