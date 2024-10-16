---
id: 1727656368-selection-sort
aliases:
  - Selection Sort
tags:
  - algorithms
  - sorting
---

# Selection Sort

- Este algoritmo se encarga de seleccionar el menor elemento dentro de un arreglo y lo posiciona en la primera posición.
- Utiliza dos iteraciones, la primera que selecciona la posición en la que irá el menor elemento y la segunda que encuentra al menor elemento.

## Código

```ts
function selectionSort(arr: number[]): number[] {
  for (let i = 0; i < arr.length; i++) {
    // i es la posición donde se posicionará el menor elemento
    // minIndex es el indice del menor elemento
    let minIndex = i;

    for (let j = i + 1; j < arr.length; j++) {
      if (arr[j] < arr[minIndex]) {
        // si el elemento en j es menor al elemento en el indice menor, actualizamos el indice menor por el valor el nuevo valor
        minIndex = j;
      }
      // al finalizar esta iteracion encontramos el valor menor del arreglo
    }

    // realizamos el intercambio al encontrar el valor menor
    const temp = arr[i];
    arr[i] = arr[minIndex];
    arr[minIndex] = temp;
    // continuamos con la segunda posición del arreglo y se repite el proceso.
  }
  return arr;
}
```
